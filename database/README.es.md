# Base de datos de referencia de TigerTag

Esta carpeta contiene el registro de referencia del protocolo TigerTag: identificadores de materiales, marcas, atributos, tipos, diámetros, unidades de medida y versiones del formato de etiqueta. También incluye las claves públicas necesarias para verificar sin conexión las firmas TigerTag+.

## Licencia

El contenido de `database/*.json` se publica en el dominio público bajo [CC0 1.0 Universal](../LICENSES/CC0-1.0.txt). Puedes copiarlo, modificarlo y distribuirlo, incluso comercialmente, sin pedir permiso ni conservar atribución. La licencia es irrevocable. El código de sincronización `db_update.py` se distribuye bajo Apache-2.0.

## Archivos

| Archivo | Contenido |
|---|---|
| `id_version.json` | Versiones del formato de etiqueta y claves públicas de verificación |
| `id_material.json` | Identificadores de materiales |
| `id_brand.json` | Identificadores de marcas |
| `id_aspect.json` | Identificadores de atributos, como color o refuerzo |
| `id_type.json` | Tipos de producto |
| `id_diameter.json` | Diámetros de filamento |
| `id_measure_unit.json` | Unidades de medida |
| `id_catalog.json` | Catálogo de productos TigerTag+: productos identificados y sus marcas, series, nombres, materiales, atributos, colores, referencias e imágenes |
| `last_update.json` | Marcas de tiempo de sincronización proporcionadas por la API |
| `manifest.json` | Huella SHA-256, tamaño, número de entradas y fecha de cada archivo de datos |
| `db_update.py` | Herramienta para sincronizar las tablas y el catálogo |

## Catálogo de productos

Las tablas anteriores definen el vocabulario: qué significa cada identificador de marca o material. `id_catalog.json` contiene productos reales con el `id` que se almacena en el campo `id_product` del chip. Basta consultar ese archivo para resolver un identificador a su producto.

El catálogo se incluye aquí para que una aplicación pueda distribuirlo y consultarlo sin API, clave, paginación ni conexión a Internet. Lee `series` y `name` desde sus campos respectivos; **no dividas `title` por el último ` - `**, porque el nombre del color también puede contener ese separador. Campos como `sku`, `barcode` y `updated_at` pueden faltar; considérense opcionales.

Ejecuta `python db_update.py` para actualizar tablas y catálogo. `python db_update.py --check` no escribe archivos y termina con error si están desactualizados, por ejemplo, en una integración continua.

El catálogo no tiene una marca temporal propia en `all/last_update`; por eso cada ejecución vuelve a descargarlo completo, pero solo escribe cambios. La fecha de modificación del catálogo está en `manifest.json`.

## Manifiesto

`manifest.json` se genera al final de la sincronización. Permite comprobar las descargas sin usar la API de GitHub:

- `files` enumera los JSON de esta carpeta, excepto el propio manifiesto.
- `sha256` y `bytes` describen el contenido exacto publicado.
- `entries` indica el número de elementos de la lista superior, o `null` si se trata de un objeto.
- `updatedAt` registra el último cambio de contenido del archivo.
- `generatedAt` registra la última vez que cambió algún archivo.

Un cliente descarga el manifiesto, obtiene solo los archivos con una huella distinta, verifica tamaño, SHA-256 y número de entradas, y aplica las tablas en un solo paso. Si algo falla, conserva las tablas actuales. Así también se puede detectar una copia desactualizada o alterada en un espejo.

`python db_update.py --manifest` reconstruye el manifiesto localmente, sin red. `python db_update.py --manifest --check` solo informa si necesita cambios.

## Claves públicas

`id_version.json` contiene únicamente claves **públicas** en formato PEM, una por cada versión de formato firmada. Se pueden incluir en lectores para verificar TigerTag+ sin red.

La clave privada correspondiente está únicamente en poder de TigerTag Corp. Si encuentras una clave privada en este repositorio, trátalo como una vulnerabilidad crítica y notifícala de forma privada según [`../SECURITY.md`](../SECURITY.md).
