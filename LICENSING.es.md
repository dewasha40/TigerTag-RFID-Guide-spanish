> **Traducción informativa:** versión en español de [`LICENSING.md`](LICENSING.md). Si hay discrepancias o se requiere interpretar obligaciones jurídicas, prevalece el original en inglés.

# Licencias

Este repositorio contiene cuatro tipos diferentes de material, y no todo está bajo la misma licencia. Esta página indica exactamente qué está bajo qué licencia.

Si solo lees un párrafo, léelo siguiente.

---

## Concesión de implementación

> TigerTag Corp concede un derecho irrevocable, mundial y sin regalías para implementar
> esta especificación en cualquier producto o software, de código abierto o propietario,
> sin restricciones y sin necesidad de permiso adicional.

No necesitas una licencia para leer esta especificación. No necesitas una licencia para
implementarla. No necesitas informarnos, registrarte con nosotros o pagar. Esto aplica
a productos comerciales, firmware de código cerrado, impresoras, programas de corte y cualquier otro elemento.

Esta concesión es irrevocable. No expira, y no está condicionada a que permanezcas en buenos términos con nadie.

---

## Qué está bajo qué

| Ruta | Licencia | Identificador SPDX |
|---|---|---|
| `README.md` y toda la documentación del protocolo | Creative Commons Attribution 4.0 Internacional | `CC-BY-4.0` |
| `Images/`, `assets/` — diagramas y figuras | Creative Commons Attribution 4.0 Internacional | `CC-BY-4.0` |
| `database/*.json` — el registro de referencia | Creative Commons Zero 1.0 Universal (dominio público) | `CC0-1.0` |
| `Sample code/`, `SpoolmanDB/`, `database/db_update.py` — todo el código fuente | Apache License 2.0 | `Apache-2.0` |
| `brand/` — logotipo, banner, iconos, marcas de palabra | **Todos los derechos reservados.** No está cubierto por ninguna licencia anterior | — |

El archivo `LICENSE` en la raíz del repositorio contiene el texto completo de CC-BY-4.0, porque la especificación es el contenido principal aquí. Los textos completos de todas las licencias utilizadas se encuentran en
[`LICENSES/`](LICENSES/).

---

## Qué significa esto en la práctica

**Quieres construir un lector, un escritor, una impresora o un programa de corte que hable TigerTag.**
Adelante. Nada aquí te lo impide. La especificación está bajo CC-BY-4.0, así que cite y traduzca libremente con atribución; la concesión de implementación mencionada anteriormente cubre la acción de implementarla, algo que la propiedad intelectual no habría restringido de todos modos.

**Quieres copiar el código de ejemplo en tu firmware.**
Está bajo Apache-2.0. Mantén la notificación, mantén el texto de la licencia, indica tus cambios. Apache-2.0 incluye una concesión expresa de patentes de cada contribuyente — esto es deliberado, y es
la razón por la que elegimos Apache-2.0 en lugar de MIT para el código.

**Quieres incrustar `database/*.json` en tu producto.**
Está bajo CC0-1.0 — dominio público. No se requiere atribución, no se requiere notificación, nada que llevar a tu binario. En la Unión Europea, el derecho *sui generis* de base de datos puede adherirse a un conjunto de datos compilado independientemente de la propiedad intelectual, por lo que se usa CC0 aquí para renunciar a eso explícitamente. Aun así, nos gustaría recibir un crédito. No te debes uno a nosotros.

**Quieres traducir la especificación, citarla en un libro o enseñar con ella.**
CC-BY-4.0. Atribuye a TigerTag Corp y ya está.

**Quieres llamar a tu producto "TigerTag" o poner nuestro logotipo en tu caja.**
Eso es lo único que no es gratuito, y se trata de un asunto de marca registrada, no de licencia. Ver [`TRADEMARK.md`](TRADEMARK.es.md).

---

## Qué *no* se concede aquí

Tres cosas se sitúan fuera de cada licencia en esta página:

1. **Las marcas TigerTag™ y TigerTag+™ y el logotipo.** Todos los derechos reservados.
   Ver [`TRADEMARK.md`](TRADEMARK.es.md). Tenga en cuenta que CC-BY-4.0 §2(b)(2) expresa
   que no licencia derechos de marca registrada, ni lo hacemos nosotros.

2. **La firma TigerTag+.** TigerTag Corp posee la clave privada ECDSA-P256. Cualquier persona
   puede *verificar* una firma de forma offline — las claves públicas se publican en
[`database/id_version.json`](database/id_version.json) y están bajo CC0. Solo TigerTag Corp puede *emitir* uno. Esto es una propiedad de la custodia de la clave, no de una licencia, y es lo que hace que una etiqueta firmada correctamente pueda probarse que proviene de TigerTag.

3. **Asignación de Product-ID en el catálogo oficial.** Al igual que un prefijo de empresa GS1, un ID de producto oficial se *asigna*, no se licencia. El protocolo es gratuito; el espacio de identidad se administra.

Los puntos 1–3 son lo que cubre [`LICENSE_COMMERCIAL.md`](LICENSE_COMMERCIAL.es.md), junto con el suministro de medios TigerTag preimpresos oficiales. Ninguno de ellos restringe el protocolo.

---

## ¿Por qué no GPL

Versiones anteriores de este repositorio anunciaron GPLv3. Eso fue un error y se ha corregido.

El copyleft sobre una *especificación* asusta a los fabricantes que un estándar necesita — un abogado de una marca de filamento leyendo "cualquier obra derivada también debe ser GPLv3" junto a un documento que describe un diseño de memoria, correctamente, lo elevaría. Una especificación que pretende convertirse en el código de barras EAN de la impresión 3D debe ser permisiva, y su código de referencia debe incluir una concesión de patentes. Nada se ganó con la GPL y mucho estaba en riesgo.

El anuncio de GPLv3 tampoco fue operativo: el antiguo `LICENSE.md` contenía un marcador de posición donde debería haber estado el texto de la licencia, por lo que GitHub informó el repositorio como `NOASSERTION` — "todos los derechos reservados". Durante un período, nadie pudo implementar este protocolo legalmente en absoluto. Ahora eso está arreglado.

---

## ¿Por qué bifurcar la especificación es inútil

Nada en estas licencias te impide bifurcar este repositorio. No vamos a intentarlo.

Pero una especificación no es un programa. Su valor total es que todos estén de acuerdo con ella. Una bifurcación del protocolo TigerTag produce un documento que describe chips que nadie fabrica, que ningún lector en el campo implementa, y que no puede llamarse TigerTag. Fragmenta el ecosistema y no ayuda a nadie, especialmente al que lo escribió.

Si la especificación está equivocada, incompleta o falta un campo que necesitas, el movimiento útil es una propuesta, no una bifurcación. Consulta [`CONTRIBUTING.md`](CONTRIBUTING.es.md) para el proceso TEP (TigerTag Enhancement Proposal), y [`VERSIONING.md`](VERSIONING.es.md) para ver cómo los cambios aceptados llegan a una versión publicada de la especificación.

---

## SPDX

Los archivos de código fuente llevan encabezados `SPDX-License-Identifier`. Para el repositorio en su conjunto:

```
SPDX-License-Identifier: CC-BY-4.0 AND CC0-1.0 AND Apache-2.0
```

---

## Contacto

Preguntas sobre licencias: [tigertag@tigertag.io](mailto:tigertag@tigertag.io)

© 2025–2026 TigerTag Corp.
