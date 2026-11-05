> **Traducción informativa:** versión en español de [`SECURITY.md`](SECURITY.md). Si hay discrepancias o se requiere interpretar obligaciones jurídicas, prevalece el original en inglés.

# Política de Seguridad

La garantía de autenticidad de TigerTag se basa en una única afirmación criptográfica:

> Una etiqueta que lleva una firma válida de TigerTag+ solo puede haber sido firmada por TigerTag Corp,
> y cualquier lector puede verificar esto sin conexión a red.

Cualquier cosa que debilite esa afirmación es una vulnerabilidad de seguridad, y queremos que nos lo comuniquen
antes que a alguien más.

---

## Informe de una vulnerabilidad

**No abra un problema público, una solicitud de extracción o un mensaje en Discord.**

Informe de forma privada, mediante cualquiera de las siguientes vías:

1. **GitHub Security Advisory** (preferido) — utilice
   [Reportar una vulnerabilidad](https://github.com/TigerTag-Project/TigerTag-RFID-Guide/security/advisories/new)
   en este repositorio. Esto crea un hilo privado visible solo para los mantenedores.
2. **Correo electrónico** — [security@tigertag.io](mailto:security@tigertag.io), copiando
   [tigertag@tigertag.io](mailto:tigertag@tigertag.io).

Si cree que el problema está siendo explotado activamente, indíquelo en la primera línea.

### Qué incluir

- Lo que encontró y qué beneficio obtiene un atacante de ello
- Cómo reproducirlo — un volcado de chip, un script, una firma que se verifica cuando no debería
- La versión de especificación y la versión del formato de etiqueta involucradas (ver [`VERSIONING.md`](VERSIONING.es.md))
- Si ha revelado el problema en otro lugar

No es necesario un exploit funcional. Una descripción creíble de una falla en el esquema de firma
es suficiente.

### Qué esperar

| Etapa | Objetivo |
|---|---|
| Reconocimiento de su informe | 48 horas |
| Evaluación inicial — ¿es una vulnerabilidad y cuán grave? | 7 días |
| Plan de corrección o mitigación comunicado a usted | 30 días |
| Divulgación pública | Coordinada con usted, normalmente después de que esté disponible una corrección |

Lo acreditaremos en el aviso a menos que nos lo pida que no lo hagamos. Actualmente no operamos un
programa de recompensas pagado.

---

## En el ámbito

Especially anything touching the signature or key handling:

- **Falsificación de firma** — producir una etiqueta que se verifique contra una clave pública publicada
  sin la clave privada de TigerTag Corp
- **Bypass de firma** — causar que un lector que sigue la especificación presente una etiqueta no firmada o firmada incorrectamente como **origin-verified**: como un `TigerTag+ Certified`, o
  como cualquier cosa que un usuario leería como prueba de procedencia. Aceptar una etiqueta no firmada como un `TigerTag+` es un comportamiento correcto y no es un bypass — el `+` es una identidad de catálogo, no una afirmación de autenticidad.
- **Debilidad en la construcción del mensaje firmado** — el mensaje firmado es
  `SHA-256(uid[7B] ‖ id_tigertag[4B BE] ‖ id_product[4B BE])`. Colisiones, extensión de longitud,
  ambigüedad en la concatenación, o cualquier forma de hacer que dos etiquetas distintas produzcan el mismo
  resumen están en el ámbito.
- **Exposición de claves** — una clave privada, o material suficiente para derivar una, presente en cualquier lugar
  en este repositorio, en un artefacto publicado, en la API, o en una herramienta entregada
- **Ataques de downgrade** — forzar a un lector a tratar un chip firmado válidamente como uno no firmado,
  o a seleccionar una versión más débil del formato de etiqueta
- **Sustitución de clave pública** — cualquier camino por el cual un lector pueda ser inducido a verificar contra
  una clave controlada por un atacante en lugar de las que están en
  [`database/id_version.json`](database/id_version.json)
- **Defectos en la especificación** que lleven a una implementación correcta a un estado inseguro.
  Un error en este documento es una vulnerabilidad en cada lector que lo implementa.
- Vulnerabilidades en `Sample code/`, `SpoolmanDB/`, o `database/db_update.py`

## Fuera del ámbito
- **Clonado de una etiqueta.** TigerTag+ firma la UID de la etiqueta junto con la identidad del producto, por lo que una firma está vinculada a un chip físico concreto y no se puede transferir. Copiar una UID requiere un chip con una UID escribible — esta es una propiedad del mercado de hardware NFC, no del protocolo TigerTag, y es una limitación conocida y aceptada.
- **Escritura de datos arbitrarios en un chip.** Los chips TigerTag nunca se bloquean para escritura, deliberadamente, para que puedan reutilizarse tras finalizar el carrete. Cualquier persona con acceso físico puede reescribir uno. Esto está diseñado así. Lo que no pueden hacer es producir una firma válida de TigerTag+.
- **Lectura de un chip.** Los datos en una etiqueta TigerTag no son secretos.
- Vulnerabilidades en lectores, impresoras o cortadores de terceros que implementan el protocolo incorrectamente. Informe estas vulnerabilidades a sus autores. Si la especificación los condujo allí, eso está dentro del alcance — háganoslo saber.
- Denegación de servicio contra `api.tigertag.io` — informe a
  [tigertag@tigertag.io](mailto:tigertag@tigertag.io), no como un aviso de seguridad.
- Falta de encabezados de seguridad o configuración de TLS en el sitio web.

---

## Manejo clave

- La **clave privada de TigerTag+ es custodiada exclusivamente por TigerTag Corp** y nunca se distribuye, nunca está presente en este repositorio, y nunca está presente en ninguna herramienta o SDK entregada.
- Las **claves públicas correspondientes se publican** en
  [`database/id_version.json`](database/id_version.json), una por versión de formato de etiqueta, en formato PEM.
  Están en el dominio público (CC0) y están destinadas a ser incrustadas directamente en los lectores.
- La verificación es **ECDSA sobre NIST P-256 con SHA-256**, y se realiza completamente offline. Un lector que requiere una llamada de red para verificar una etiqueta no está implementando esta especificación.
- **Si encuentra una clave privada en cualquier lugar,** trátela como una vulnerabilidad crítica y notifíquela inmediatamente mediante los canales privados mencionados anteriormente.

### Rotación de claves

Una clave comprometida o retirada se retira mediante la **introducción de una nueva versión de formato de etiqueta** con un nuevo par de claves, añadido a `id_version.json`. Los lectores existentes continúan verificando las etiquetas existentes con la antigua clave pública; las etiquetas emitidas después de la rotación llevan el nuevo identificador de versión y se verifican con la nueva clave.

Por lo tanto, en la práctica, las claves públicas son de solo añadido: eliminar una invalidaría las etiquetas ya en el campo. Una clave que ya no debe ser *confiada* — en lugar de simplemente no ser *usada* — se anuncia mediante un aviso de seguridad en este repositorio, y se espera que los lectores traten las etiquetas con esa versión como si no estuvieran firmadas.

---

## Versiones compatibles

Las correcciones de seguridad se emiten contra la versión actual de la especificación y las versiones de formato de etiqueta listadas en `database/id_version.json`. Véase [`VERSIONING.md`](VERSIONING.es.md).

Dado que las etiquetas son objetos físicos con una vida útil prolongada, **ninguna versión de formato de etiqueta se retira formalmente nunca.** Un lector debe esperar encontrar una etiqueta v1.0 de forma indefinida.

---

## Divulgación

Practicamos una divulgación coordinada. No tomaremos medidas legales contra un investigador que reporte una vulnerabilidad con buena fe a través de los canales mencionados anteriormente, que no acceda ni modifique datos pertenecientes a terceros, y que nos dé tiempo razonable para emitir una corrección antes de divulgar públicamente.

Contacto: [security@tigertag.io](mailto:security@tigertag.io)
