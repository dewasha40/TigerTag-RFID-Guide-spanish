> **Traducción informativa:** versión en español de [`VERSIONING.md`](VERSIONING.md). Si hay discrepancias o se requiere interpretar obligaciones jurídicas, prevalece el original en inglés.

# Versionado

TigerTag tiene **dos números de versión independientes**, y confundirlos causa errores. Esta
página explica qué es cada uno, quién lo incrementa y cómo se relacionan.

| | Versión de especificación | Versión del formato de etiqueta |
|---|---|---|
| **¿Qué versiona?** | Este documento — el texto, los diagramas, los ejemplos | Los bytes en la etiqueta |
| **¿Dónde se encuentra?** | `README.md`, tabla de historia de versiones, el distintivo | [`database/id_version.json`](database/id_version.json) |
| **Valor actual** | `2.1` | `0.0`, `1.0` |
| **Leído por** | Humanos | Lectores, en tiempo de ejecución, desde la etiqueta |
| **Cambia cuando** | El documento cambia | El diseño en la etiqueta o una clave cambia |

Un lector **nunca** analiza la versión de especificación. Lee el campo `id_tigertag` de
la etiqueta, lo busca en `id_version.json`, y aprende qué diseño esperar y qué
clave pública utilizar para verificar.

---

## 1. Versión de especificación

La versión de *este documento*. Sigue el esquema de versionado semántico, aplicado al protocolo como
un contrato:

- **Mayor** (`2.0` → `3.0`) — un lector existente interpretaría erróneamente una etiqueta
  escrita bajo la nueva especificación. Un campo movido, un cambio en el codificado, un cambio en el orden de bytes.
  Un incremento mayor requiere una nueva versión del formato de etiqueta (§2) para que los lectores antiguos puedan detectar y
  rechazar etiquetas que no puedan analizar.
- **Menor** (`2.0` → `2.1`) — nuevo material que no cambia cómo un lector existente
  actúa sobre una etiqueta existente. Un byte previamente reservado se le da un significado, un nuevo campo opcional
  en espacio no utilizado, nueva documentación de comportamiento que siempre fue cierto.
- **Parche** (`2.1` → `2.1.1`) — el protocolo no cambia. Errores tipográficos, valores hexadecimales corregidos en ejemplos,
  redacción aclarada, nuevos diagramas, traducciones.

La versión actual de especificación se indica en el distintivo en la parte superior de `README.md` y en
la tabla de historia de versiones en §7. Ambos deben actualizarse juntos.

### Historial

| Versión | Fecha | Cambio |
|---|---|---|
| 1.0 | 2025-06-09 | Formato público inicial |
| 2.0 | 2026-03-11 | Corrección del diseño de memoria binaria y alineación de capacidad NTAG21x |
| 2.1 | 2026-05-18 | Añadir documentación de UID, diseño de páginas del sistema, corregir valores hexadecimales de ejemplo |

Tenga en cuenta que `2.0` corrigió la *documentación* del diseño. Las etiquetas en el campo no se
re-codificaron.

---

## 2. Versión del formato de etiqueta

El valor escrito en la etiqueta, en el campo `id_tigertag`. Es un identificador big-endian de tipo `u32`, no una cadena legible por humanos, y cada entrada está registrada en
[`database/id_version.json`](database/id_version.json):

| `id` | `version` | `name` | `tag` | Clave pública |
|---|---|---|---|---|
| `0` | `0.0` | RFID Vacío | `TIGER_TAG_UNINITIALIZED` | — |
| `1542820452` | `1.0` | TigerTag | `TIGER_TAG_V1.0` | Sí |
| `1816240865` | `1.0` | TigerTag Inicial | `TIGER_TAG_INIT` | Sí |
| `3155151767` | `1.0` | TigerTag+ | `TIGER_TAG_PLUS_V1.0` | Sí |

La última columna indica si la entrada incluye una clave, **no** si las etiquetas de esa versión
están firmadas. La firma es opcional e independiente de la versión del formato: una etiqueta firmada es una
`TigerTag+ Certified` (ver [`CERTIFICATION.md`](CERTIFICATION.es.md)), y una etiqueta no firmada
`TigerTag+` es normal.

Cada entrada con una clave lleva la **clave pública** utilizada para verificar etiquetas de esa versión, en
formato PEM, en el campo `public_key`. Este es el mecanismo que hace posible la verificación offline: un lector lleva incrustado `id_version.json`, lee `id_tigertag` de la etiqueta,
selecciona la clave correspondiente y verifica. Sin conexión a red.

### Reglas
1. **`id_version.json` es de solo lectura.** Los chips son físicos y de larga duración. Eliminar una entrada deja huérfanos a todos los chips ya en el campo. Las entradas nunca se eliminan y sus valores `id` nunca se reutilizan.
2. **Se requiere una nueva entrada siempre que un lector existente la interpretara incorrectamente.** Nuevo diseño, nueva clave, nuevo esquema de firma.
3. **Los valores `id` son opacos.** No infieras orden, recencia o capacidad a partir del valor numérico. Busca la entrada.
4. **Un lector que encuentre un valor `id_tigertag` desconocido debe fallar cerrado** — trátalo como un chip no reconocido, no como uno no firmado pero válido. Puede ser un formato del futuro.
5. **La rotación de claves ocurre añadiendo una versión**, nunca editando una clave en su lugar. Ver [`SECURITY.md`](SECURITY.es.md#rotación-de-claves).

### Cómo se mantiene `id_version.json`

`database/*.json` se genera a partir del catálogo de TigerTag y se sincroniza automáticamente en este repositorio mediante `.github/workflows/sync-database.yml`. **No lo edites a mano, ni envíes solicitudes de extracción contra él** — ver [`CONTRIBUTING.md`](CONTRIBUTING.es.md).

---

## 3. Cómo se relacionan los dos

- Un **bump de parche o menor** en la especificación deja `id_version.json` sin cambios.
- Un **bump de mayor** en la especificación añade una nueva entrada a `id_version.json`. Las entradas antiguas permanecen. Los chips escritos antes del bump siguen funcionando, para siempre, sin cambios.
- Un **nuevo formato de etiqueta** puede añadirse sin un bump de mayor en la especificación — por ejemplo, para rotar una clave mientras el diseño permanece inalterado. En ese caso, la especificación recibe un bump menor para documentar la nueva entrada.

En consecuencia: la versión de la especificación te indica *qué documento estás leyendo*. No te indica qué contiene cualquier chip dado. Solo el chip lo hace.

---

## 4. Cambiar la especificación

Los cambios en el protocolo llegan como TEPs (TigerTag Enhancement Proposals), no como bifurcaciones. Un TEP aceptado es lo que desencadena un incremento de versión. Ver [`CONTRIBUTING.md`](CONTRIBUTING.es.md).

Cuando se publica un TEP:

1. `README.md` se actualiza con el cambio.
2. La tabla de historia de versiones en `README.md` §7 añade una fila.
3. El distintivo del protocolo en la parte superior de `README.md` se actualiza.
4. La tabla en §1 de este archivo añade una fila.
5. Si se cambió el diseño en el chip o una clave, se registra una nueva entrada en el catálogo de TigerTag y aparece en `id_version.json` en la próxima sincronización.
6. Se envía una etiqueta git `spec-vX.Y.Z`, y se genera una publicación en GitHub contra ella.

---

## 5. Garantía de estabilidad

La compromiso implicado por lo anterior, expresado claramente:

> Un chip escrito hoy será legible por un lector TigerTag conforme de forma indefinida. Los diseños de campo, una vez publicados bajo una versión de formato de etiqueta, nunca se redefinen. Nuevas capacidades llegan como nuevas versiones de formato de etiqueta, no como redefiniciones de una antigua.

Esta es la propiedad que hace seguro para un fabricante de impresoras grabar un lector TigerTag en el firmware que se distribuirá durante una década.
