> **Traducción informativa:** versión en español de [`CONTRIBUTING.md`](CONTRIBUTING.md).

# Contribuyendo al protocolo TigerTag

Gracias por querer mejorar TigerTag.

Este repositorio es la **fuente de verdad** sobre cómo se almacenan los datos en un chip TigerTag. Cada
lector, escritor, impresor, cortador y aplicación en el campo implementan lo que se escribe aquí. Eso
lo hace diferente de un proyecto de software ordinario, y cambia cómo funcionan las contribuciones.

---

## No bifurques la especificación

Legalmente puedes crear una bifurcación — [`LICENSING.md`](LICENSING.es.md) no te lo impide, y no
vamos a añadir una licencia que lo haga. Te lo estamos pidiendo porque no te ayuda.

Un fork de un programa es un programa funcional. Un fork de una especificación es un documento
que describe chips que nadie fabrica y que ningún lector en el campo entiende. No puede
llamarse TigerTag ([`TRADEMARK.md`](TRADEMARK.es.md)), quedará desactualizada, y
fragmentará el ecosistema para todos, incluyéndote a ti.

Si la especificación está equivocada, poco clara o falta algo que necesitas, **la solución es una propuesta, y
la propuesta será leída.** Más de dos millones de chips están en producción; tomamos cambios en
este documento en serio y preferimos incorporar tu cambio en la especificación canónica
que en un fork.

---

## Dos tipos de contribución

### 1. Correcciones — simplemente abre una solicitud de extracción

Si algo está incorrecto o poco claro y la corrección no cambia el protocolo, envía una
solicitud de extracción directamente. No se necesita ningún proceso. Esto incluye:

- Errores tipográficos, enlaces rotos, valores hexadecimales incorrectos en ejemplos
- Aclarar un lenguaje ambiguo que no cambia el comportamiento
- Mejorar diagramas, añadir traducciones
- Corregir errores en `Sample code/` o `SpoolmanDB/`
- Añadir una implementación de ejemplo en un nuevo lenguaje

### 2. Cambios en el protocolo — abre un TEP

Cualquier cosa que cambie lo que debe hacer una implementación conforme pasa por un **TEP
(Proposal de Mejora de TigerTag)**. Esto incluye:

- Añadir, eliminar o reutilizar un campo
- Cambiar un desplazamiento de memoria, un codificación o un orden de bytes
- Cambiar el comportamiento de firma o verificación
- Añadir una nueva versión del formato de etiqueta
- Cualquier cosa que podría hacer que un lector existente malinterprete un chip

Abre un problema utilizando la
[**plantilla de propuesta de protocolo**](https://github.com/TigerTag-Project/TigerTag-RFID-Guide/issues/new?template=protocol-proposal.yml).

---

## El proceso del TEP

Un TEP es un problema de GitHub. No hay un repositorio separado, no hay un comité de numeración, y no
hay una lista de correo. Manténlo ligero.

```
  Draft  ──►  Discussion  ──►  Accepted  ──►  Released
    │             │               │              │
    │             └──► Deferred   └──► Rejected  └──► spec version bump
    └──► Withdrawn
```

**1. Borrador.** Abres un problema desde la plantilla. Se etiqueta `tep` y `draft`. Explica
el problema antes de la solución. Un TEP que describe un problema real de forma pobre es más útil
que uno que describe una solución elegante a nada.

**2. Discusión.** Pública, en el hilo del problema. Espera preguntas sobre la compatibilidad hacia atrás por encima de todo. La pregunta más importante para casi cualquier TEP es: *¿qué hace un lector existente en el campo cuando encuentra un chip escrito bajo esta propuesta?* Si la respuesta es "se comporta mal", el TEP necesita una nueva versión del formato de etiqueta, no un nuevo campo.

**3. Aceptado / Diferido / Rechazado.** Un mantenedor marca el resultado y explica por qué en
el hilo. Los rechazos vienen con una razón. "Diferido" significa buena idea, momento equivocado — normalmente esperando un aumento de versión que ya está planeado.

**4. Publicado.** Un TEP aceptado se implementa en `README.md`, se actualiza la tabla de historia de versiones, y se actualiza la versión de la especificación según [`VERSIONING.md`](VERSIONING.es.md). El problema del TEP se cierra con un enlace a la versión publicada.
No existe un plazo fijo. Los cambios en el diseño del chip son lentos por naturaleza y eso es correcto.

---

## ¿Qué hace que un TEP sea probable que se acepte?

- **Resuelve un problema que alguien realmente tiene.** Idealmente con un producto o flujo de trabajo con nombre.
- **Es compatible hacia atrás**, o es honesto al respecto y propone un incremento de versión.
- **Encaja en el presupuesto de memoria.** El NTAG213 tiene 144 bytes utilizables. El espacio en el chip es el recurso más escaso en este proyecto; un TEP que necesita cuatro bytes debe explicar por qué dos no bastan.
- **No requiere un servidor.** La operación offline es una propiedad fundamental de TigerTag.
- **No debilita la firma.** Ver [`SECURITY.md`](SECURITY.es.md).

## ¿Qué se rechazará?

- Cambios que rompan lectores ya desplegados en el campo sin un incremento de versión
- Campos que duplican información ya derivable del chip o de la API pública
- Cualquier cosa que haga que una implementación dependa de un viaje de red
- Cualquier cosa que requiera permiso de TigerTag Corp para implementarla

---

## Entradas de la base de datos de referencia

**No envíes solicitudes de extracción que añadan entradas a `database/*.json`.** Estos archivos se generan desde el catálogo de TigerTag y se sobrescriben automáticamente por el flujo de trabajo de sincronización — una solicitud de extracción contra ellos se revertirá silenciosamente en la próxima sincronización.

Para añadir una marca, material, aspecto o tipo a la base de datos de referencia, abre un problema normal describiendo la entrada, o contacta a [tigertag@tigertag.io](mailto:tigertag@tigertag.io).

Las correcciones a `database/db_update.py` y a las herramientas de sincronización son bienvenidas como solicitudes de extracción.

---

## Problemas de seguridad

**No** abra un problema público para una vulnerabilidad, especialmente una que afecte a la firma TigerTag+, manejo de claves o verificación. Ver [`SECURITY.md`](SECURITY.es.md).

---

## Licenciamiento de contribuciones

Al contribuir, aceptas que tu contribución se licencia bajo los mismos términos que el material que modifica, como se establece en [`LICENSING.md`](LICENSING.es.md):

| Estás modificando | Tu contribución está licenciada bajo |
|---|---|
| Texto de especificación, `Images/`, `assets/` | `CC-BY-4.0` |
| `Sample code/`, `SpoolmanDB/`, `database/db_update.py` | `Apache-2.0` |
| Contenido de la base de datos de referencia | `CC0-1.0` |

Apache-2.0 §5 significa que una contribución de código lleva una concesión explícita de patentes. Esto es intencional: es lo que permite a un fabricante incrustar el código de ejemplo sin una revisión de patentes.

Conservas los derechos de autor de tu contribución. No hay un CLA.

---

## Estilo de código

- Python: solo la biblioteca estándar donde sea posible, `Sample code/` debe ejecutarse sin dependencias más allá de `cryptography` para la verificación de firma.
- Cada archivo de origen comienza con un encabezado SPDX:
  `# SPDX-License-Identifier: Apache-2.0`
- Mantén los ejemplos ejecutables. Si cambias un valor hexadecimal, verifica que coincida con un volcado real.

---

## Preguntas

Abre un problema, o encuentra a nuestros desarrolladores en [Discord](https://discord.gg/3Qv5TSqnJH).
