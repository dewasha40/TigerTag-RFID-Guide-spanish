# Contribuir al protocolo TigerTag

Gracias por querer mejorar TigerTag.

Este repositorio es la **fuente de verdad** sobre cómo se almacenan los datos en un chip TigerTag. Cada lector, escritor, impresora, laminador y aplicación implementa lo que se define aquí. Por eso las contribuciones requieren cuidado.

---

## No bifurques la especificación

Tienes derecho legal a crear una bifurcación —[`LICENSING.md`](LICENSING.md) no lo impide—, pero el proyecto pide que no lo hagas. Una bifurcación de un programa sigue siendo un programa funcional; una bifurcación de una especificación describe chips que nadie fabrica y que los lectores existentes no entienden. Tampoco puede llamarse TigerTag (consulta [`TRADEMARK.md`](TRADEMARK.md)), con el tiempo quedará desactualizada y fragmentará el ecosistema.

Si la especificación contiene un error, no se entiende o le falta algo, **propón el cambio**. El equipo prefiere incorporar la mejora en la especificación canónica. Hay más de dos millones de chips en producción, por lo que los cambios se revisan con cuidado.

## Dos tipos de contribución

### 1. Correcciones — abre directamente una solicitud de cambios

Para errores de hecho o ambigüedades que no cambien el protocolo, abre una solicitud de cambios (pull request). Por ejemplo:

- Erratas, enlaces rotos o valores hexadecimales incorrectos en ejemplos.
- Aclaraciones que no alteren el comportamiento.
- Mejoras de diagramas y traducciones.
- Correcciones de errores en `Sample code/` o `SpoolmanDB/`.
- Una implementación de ejemplo en otro lenguaje.

### 2. Cambios de protocolo — presenta un TEP

Cualquier cambio en lo que debe hacer una implementación conforme requiere un **TEP (TigerTag Enhancement Proposal, propuesta de mejora de TigerTag)**. Por ejemplo:

- Añadir, quitar o reasignar un campo.
- Cambiar un desplazamiento de memoria, una codificación o el orden de bytes.
- Cambiar la firma o su verificación.
- Añadir una versión del formato de etiqueta.
- Cualquier cambio que pueda hacer que un lector interprete mal un chip existente.

Abre una incidencia con la plantilla de [propuesta de protocolo](https://github.com/TigerTag-Project/TigerTag-RFID-Guide/issues/new?template=protocol-proposal.yml).

## Proceso TEP

Un TEP es una incidencia de GitHub; no hay otro repositorio ni comité de numeración.

1. **Borrador:** describe primero el problema. Una descripción clara de un problema real vale más que una solución elegante a un problema inexistente.
2. **Debate:** se conversa en la incidencia. La compatibilidad con lectores existentes es prioritaria. La pregunta clave es qué hará un lector actual ante un chip creado con la propuesta. Si lo interpreta mal, probablemente se necesite una versión nueva del formato.
3. **Aceptado, aplazado o rechazado:** una persona mantenedora comunica el resultado y el motivo.
4. **Publicado:** se actualiza `README.md`, el historial de versiones y la versión de la especificación según [`VERSIONING.md`](VERSIONING.md). Después se cierra la incidencia con un enlace a la versión publicada.

No hay un plazo fijo; los cambios en el diseño del chip llevan tiempo.

## Qué ayuda a que se acepte un TEP

- Resuelve un problema real de un producto o flujo de trabajo concreto.
- Es compatible con versiones anteriores o explica claramente por qué no lo es y propone subir la versión.
- Cabe en el espacio disponible. NTAG213 tiene 144 bytes utilizables; cada byte debe justificarse.
- No requiere un servidor: el uso sin conexión es una propiedad esencial.
- No debilita la firma. Consulta [`SECURITY.md`](SECURITY.md).

## Licencias

Puedes implementar la especificación de forma gratuita, incluso en un producto comercial. Revisa [`LICENSING.md`](LICENSING.md) para conocer las licencias por componente. Las marcas y los logotipos tienen reglas aparte; consulta [`TRADEMARK.md`](TRADEMARK.md).
