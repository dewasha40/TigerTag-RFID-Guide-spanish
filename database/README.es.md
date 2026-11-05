> **Traducción informativa:** versión en español de [`README.md`](README.md).

# Base de datos de referencia de TigerTag

Este directorio contiene el registro de referencia del protocolo TigerTag: los identificadores canónicos para materiales, marcas, aspectos, tipos, diámetros, unidades de medida y versiones de formato de etiqueta, además de las claves públicas utilizadas para verificar firmas TigerTag+ sin conexión.

## Licencia

**El contenido de `database/*.json` se publica en el dominio público bajo**
[CC0 1.0 Universal](../LICENSES/CC0-1.0.txt) (`SPDX-License-Identifier: CC0-1.0`).

No se requiere atribución. No es necesario incluir ninguna notificación en tu binario. Incorpora estos archivos directamente en un cortador, un firmware de impresora, un lector o una aplicación móvil, comercial u otra, sin pedir permiso ni atribuir a nadie.

CC0 se utiliza deliberadamente en lugar de CC-BY. En la Unión Europea, un conjunto de datos compilado puede quedar sujeto al derecho *sui generis* de la base de datos independientemente de los derechos de autor, lo que de otro modo requeriría una concesión explícita antes de que alguien pudiera legalmente extraer y reutilizar una parte sustancial de ella. CC0 renuncia a ese derecho junto con los derechos de autor. El objetivo es la adopción máxima; si los fabricantes dudan en integrar el registro, este no cumple su propósito.

Aun así, nos gustaría recibir un crédito y un enlace a <https://tigersystem.io>. No nos debes nada a cambio.

`database/db_update.py` es **código fuente**, no datos, y está licenciado bajo
[Apache-2.0](../LICENSES/Apache-2.0.txt). Ver [`../LICENSING.md`](../LICENSING.es.md).

## Estos archivos se generan — no los edites

`database/*.json` se genera a partir del catálogo de TigerTag y se sincroniza automáticamente en este
repositorio mediante [`.github/workflows/sync-database.yml`](../.github/workflows/sync-database.yml).

**Las solicitudes de extracción que añadan o modifiquen entradas se revertirán en la próxima sincronización.** Para añadir una marca, material, aspecto o tipo, abre un problema o contacta con
[tigertag@tigertag.io](mailto:tigertag@tigertag.io).

Las correcciones a `db_update.py` y a las herramientas de sincronización son bienvenidas como solicitudes de extracción.

## API en vivo

Los mismos datos están disponibles siempre actualizados, sin clave ni inicio de sesión:

<https://api.tigertag.io/api:tigertag>

## Archivos

| Archivo | Contenido |
|---|---|
| `id_version.json` | Versiones de formato de etiqueta y sus claves públicas **ECDSA-P256**. Ver [`../VERSIONING.md`](../VERSIONING.es.md) |
| `id_material.json` | Identificadores de material (PLA, PETG, ABS, resina, …) |
| `id_brand.json` | Identificadores de marca |
| `id_aspect.json` | Identificadores de aspecto / acabado de superficie |
| `id_type.json` | Identificadores de tipo de producto |
| `id_diameter.json` | Identificadores de diámetro de filamento |
| `id_measure_unit.json` | Identificadores de unidades de medida |
| `id_catalog.json` | **El catálogo completo de productos TigerTag+** — nombrado como sus vecinos `id_*.json` porque eso es lo que es: los ids — cada producto referenciado con su marca, serie, nombre, material, aspecto, color, SKU, código de barras, capacidad e imagen |
| `last_update.json` | Marcas temporales de sincronización, como las proporcionadas por `all/last_update` de la API |
| `manifest.json` | Cada tabla anterior con su sha256, tamaño, número de entradas y fecha de último cambio. Ver [El manifiesto](#el-manifiesto) |
| `db_update.py` | Herramientas de sincronización para todo lo anterior — tablas y catálogo (Apache-2.0) |

### El catálogo de productos

Las tablas anteriores nombran el *vocabulario* — qué significa un identificador de material o marca.
`id_catalog.json` es **el catálogo en sí mismo**: ~3 000 productos reales, cada uno con el
`id` que lleva un chip en `id_product`. Asociar un chip escaneado con un producto real no requiere nada más que este archivo.

Se refleja aquí para que una integración pueda enviar el catálogo con él — sin necesidad de una API
llamada, sin clave, sin paginación, sin reconstruir nada, y funciona sin conexión. Lo mismo
que los tablas de referencia.

```jsonc
{
  "id": 1251796608,            // matches the chip's id_product
  "product_type": "Filament",
  "brand": "3DXTech",
  "series": "CarbonX",
  "name": "Black",
  "title": "CarbonX - Black",  // series + name, pre-joined
  "material": "PP",
  "aspect1": "Carbon",
  "aspect2": null,
  "color": "#000000FF",
  "color_info": { "type": "mono", "colors": ["#000000FF"] },
  "measure": "750 g",
  "sku": "PP01010750BK0",
  "barcode": "07050135",
  "img_src": "https://cdn.tigertag.io/img?id=1251796608&v=4",
  "updated_at": 1785083620855
}
```

Lee `series` y `name` desde sus propios campos — **no** dividas `title` en el
último `" - "`. Un nombre de color puede contener uno: *"PLA Basic - CMYK - Magenta"* es
serie `PLA Basic` + nombre `CMYK - Magenta`, y dividirlo lo obtiene al revés.

`sku`, `barcode` y `updated_at` **no** se rellenan para cada producto; trátalos
como opcionales. `id`, `product_type`, `brand`, `series`, `name`, `material`,
`aspect1`, `color`, `color_info` y `measure` siempre están presentes.

Refrescado por `python db_update.py`, en la misma ejecución que las tablas anteriores — no
hay un comando de catálogo separado. Recorre cada página, ordena por `id` y ordena
las claves de cada producto, por lo que un catálogo inalterado genera un archivo idéntico en bytes y
no hay confirmación. `--check` no escribe nada y sale con código de error distinto de cero cuando cualquier archivo ha quedado
atrasado — útil en CI.

A diferencia de las tablas, el catálogo no tiene clave en `all/last_update`, por lo que no hay
una marca de tiempo del servidor para comparar y cada ejecución lo descarga completo (19 205 productos,
cuatro páginas, ~17 MB en octubre de 2026). Por eso importa la comparación de bytes anterior:
la descarga es incondicional, pero la *escritura* no lo es. `last_update.json` permanece
como la propia carga útil de la API; el script solo añadiría una clave `products` desde el
`updated_at` de los productos, lo cual la API no devuelve hoy. Por lo tanto, la fecha de cambio del catálogo está
en `manifest.json`.

### El manifiesto

`manifest.json` se escribe mediante `db_update.py` al final de cada ejecución, después de
las tablas, con la misma escritura atómica. Permite que un cliente compruebe actualizaciones y verifique
cada descarga desde cualquier fuente, sin necesidad de la API de GitHub:

```json
{
  "format": 1,
  "generatedAt": "2026-10-31T16:44:10Z",
  "files": {
    "id_catalog.json": {
      "sha256": "1a37a1b90766c96dd1bb299a269daa7ec7454a27f112e3b4143e37cede95c39d",
      "bytes": 17268794,
      "entries": 19205,
      "updatedAt": "2026-10-31T16:44:10Z"
    }
  }
}
```

- `files` enumera cada archivo JSON de esta carpeta excepto el manifiesto mismo.
- `sha256` (hex) y `bytes` describen exactamente los bytes del archivo tal como se publicó.
- `entries` es la longitud del array principal, o `null` para un objeto
  (`last_update.json`).
- `updatedAt` es la última vez que el contenido de este archivo cambió; los archivos sin cambios mantienen
  su fecha.
- `generatedAt` es la última vez que cualquier archivo cambió. Una ejecución que no cambia nada
  deja el manifiesto idéntico en bytes, por lo que no genera confirmación.

Un cliente descarga `manifest.json` desde la primera fuente que responda, descarga solo
los archivos cuyo `sha256` difiere de su copia local, comprueba `bytes`, `sha256` y
`entries`, y reemplaza sus tablas en un solo paso, manteniendo las actuales en caso de cualquier
error. Dado que cada archivo se comprueba contra el manifiesto, un espejo no necesita más confianza que GitHub: un archivo antiguo o modificado se rechaza.

`python db_update.py --manifest` reconstruye el manifiesto desde los archivos en disco
sin tocar la red (`--manifest --check` solo informa).

## Una nota sobre las claves públicas

`id_version.json` contiene **solo** claves **públicas**, en formato PEM, una por versión del formato de etiqueta firmada.
Están destinadas a ser incrustadas en lectores para que la verificación de TigerTag+ funcione sin
acceso a la red.

La clave privada correspondiente se encuentra únicamente en TigerTag Corp. Si en algún momento encuentras una clave privada en este repositorio, trátala como una vulnerabilidad crítica y notifícala de forma privada —
ver [`../SECURITY.md`](../SECURITY.es.md).
