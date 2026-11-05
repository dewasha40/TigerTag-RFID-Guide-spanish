> **Traducción informativa:** versión en español de [`CERTIFICATION.md`](CERTIFICATION.md). Si hay discrepancias o se requiere interpretar obligaciones jurídicas, prevalece el original en inglés.

# Certificación TigerTag

**La implementación del protocolo es gratuita y siempre lo será. La certificación es lo que te permite colocar nuestro sello en tu producto y decirle a un comprador que es auténtico.**

Este documento describe el programa. Sigue el modelo que la Connectivity Standards Alliance utiliza para Zigbee y Matter, y la justificación es la misma: un sello en un producto es una promesa para el comprador, y una promesa solo vale lo que la verifica.

---

## Tres palabras, y lo que cada una afirma

| Palabra | Creada por | Lo que afirma |
|---|---|---|
| **Oficial** | TigerSystem en sí mismo | Una declaración de **origen**: esto proviene de nosotros. |
| **Certificado** | Una tercera parte | Auditado y validado por TigerSystem. |
| **Compatible** | Una tercera parte | Declarado por sí mismo. Nadie lo ha verificado. |

**Oficial no es un sello que se otorgue**, porque nadie se certifica a sí mismo. Es una afirmación de origen, y se sitúa fuera del programa descrito en esta página: no hay auditoría que superar ni autorización que obtener, solo el hecho de quién fabricó el objeto.

Los chips oficiales — **formato pegatina** y **formato recarga para soportes** — son fabricados por TigerSystem, llevan el logotipo y se envían **en blanco**. Un revendedor de esos chips auténticos puede presentarlos como un producto oficial: no están aplicando el sello a nada, están vendiendo bienes que ya lo llevan. Lo que el comprador escriba después en un chip oficial en blanco es asunto suyo, y no hace que el resultado esté certificado.

El resto de esta página trata sobre las otras dos palabras — los sellos que una tercera parte puede poseer.

---

## Dos sellos para terceras partes. Solo uno de ellos necesita nuestra intervención.

| | **TigerTag Compatible** | **TigerTag Certificado** |
|---|---|---|
| Quién | Cualquier cosa que una tercera parte construya y que no haya sido verificada | Cualquier cosa que una tercera parte construya **y que haya sido verificada** — hardware o software por igual: fabricantes de filamento y resina, productores de insertos y soportes, fabricantes de máquinas, y también lectores, aplicaciones, cortadores y herramientas |
| Dice | *"Esto funciona con TigerTag."* | *"Esto ha sido verificado por TigerTag."* |
| Auditoría | Ninguna | **Requerida** |
| Coste | Gratis | **Pagado** |
| Aprobación | Ninguna. Declaración autónoma | Autorización escrita |
| Logo y nombre | Logo en tu aplicación, documentos, lista de tienda; el nombre en texto plano (*"Compatible con TigerTag"*) en un lector, impresor o software compatible | **En el chip (cualquier formato), en el producto y en el empaque** |
| Emisión de firma TigerTag+ | — | Solo en el ámbito TigerTag+ Certificado |
| Asignación de ID de producto | — | Sí |
| Lista pública | — | Sí — en el registro certificado |

**La línea entre las dos columnas es si alguien lo ha verificado — no qué es el producto.** La certificación está abierta a cualquier cosa que una tercera parte construya, incluido el software: un lector, un cortador o una aplicación móvil pueden ser certificados bajo exactamente los mismos términos que un carrete, pasando la auditoría y cumpliendo con la especificación. Es el modelo Zigbee del que este programa se basa, y es el objetivo. Nada está excluido de la certificación por categoría.

### Dos ámbitos

| Ámbito | Cubre |
|---|---|
| **TigerTag Certificado** | El producto ha sido auditado frente a la especificación y cumple con ella. |
| **TigerTag+ Certificado** | Lo anterior, más la verificación del manejo de **etiquetas firmadas** — emitirlas para un fabricante, o leerlas y verificarlas correctamente para un lector o una aplicación. La emisión de firmas pertenece a este ámbito. |

Si solo lees la especificación y envías un lector, no necesitas nada de nosotros. Diga
*"compatible con TigerTag"*, muestra el logotipo en tu interfaz, vende el producto comercialmente. Ver
[`TRADEMARK.md`](TRADEMARK.es.md). La compatibilidad se declara de forma autónoma, es gratuita y no requiere auditoría
ni permiso — y así seguirá siendo. La certificación es algo que puedes elegir buscar, nunca algo que se te exija.

El resto de esta página trata sobre la segunda columna.

---

## ¿Por qué la certificación se audita y por qué tiene un costo

Un comprador que vea el logotipo de TigerTag en un carrete debe poder concluir, sin necesidad de comprobar nada,
que el chip es auténtico, escrito correctamente y se comporta según lo prometido en la especificación. Esa
conclusión es el valor total de la marca — para ellos, y para cada socio certificado que pagó para obtenerla.

Un logotipo no verificado es peor que no tener logotipo alguno. Engaña al comprador y desvaloriza a los socios que
realizaron el trabajo.

También hay una razón legal. Un titular de marca que licencia una marca **sin ejercer control de calidad sobre sus licenciatarios**
corre el riesgo de perder la marca por completo. La auditoría no es un gasto administrativo;
es lo que mantiene la marca vigente y, por tanto, lo que mantiene viva la promesa del protocolo.

La certificación es un servicio de pago porque la auditoría implica un trabajo real: pruebas de conformidad, verificación de muestras físicas, revisión del catálogo y vigilancia continua. **El horario de tarifas se proporciona junto con el acuerdo de socio** ([`LICENSE_COMMERCIAL.md`](LICENSE_COMMERCIAL.es.md)).

---

## El proceso

### 1. Solicitar

Ponte en contacto con TigerTag Corp y firma el acuerdo de socio. Cubre la licencia de marca, la emisión de firmas,
la asignación de identificadores de producto y el estatus de socio certificado.

### 2. Declaración de conformidad

Declara por escrito exactamente lo que implementas: qué versión de especificación utilizas, qué campos escribes,
qué tipos de chips usas, cómo se aplica la etiqueta al producto. Esta es tu declaración de intención,
y la auditoría se mide contra ella.

### 3. Auditoría

Se prueban muestras físicas contra el conjunto de pruebas de conformidad. La auditoría verifica que:

1. **El chip se escribe correctamente** — exactamente en bytes según la especificación, en cada muestra.
2. **Los datos del catálogo son precisos** — lo que dice la página del producto coincide con lo que realmente es el carrete,
   y tienes un proceso para mantenerlo correcto después del envío.
3. **Las etiquetas firmadas llevan firmas válidas**, emitidas por TigerTag Corp — dentro del ámbito de TigerTag+
   Certificado. Un TigerTag+ sin firma es conforme y no se considera un hallazgo.
4. **El logotipo y el nombre aparecen solo donde realmente está el chip** — en el chip, en el producto y su embalaje, en ningún otro lugar.
5. **La etiqueta sobrevive al producto** — colocación, adhesión y legibilidad a lo largo de la vida del carrete,
   en las orientaciones en las que un cliente realmente lo cargará.

### 4. Declaración de conformidad

La firmas. Establece que las unidades de producción coinciden con las muestras auditadas.

### 5. Emisión

Al aprobar, TigerTag Corp concede:

- la **licencia de marca** — el derecho de aplicar el logotipo y el nombre de TigerTag a esa línea de productos;
- **emisión de firmas TigerTag+** para tus productos, dentro del ámbito de TigerTag+ Certificado;
- **asignación de identificadores de producto** en el catálogo oficial;
- una **lista pública en el registro de socios certificados**.

**Obligación de visualización.** Una línea de productos certificados **debe** mostrar el logotipo de TigerTag donde
el comprador pueda verlo — en el chip, en el producto o su embalaje, y, cuando se venda en línea, junto al lugar
donde se compra. El logotipo aparece **solo** en las líneas de productos listadas en el registro, nunca
### 6. Vigilancia

La certificación no es un evento único. TigerTag Corp muestrea periódicamente el mercado y realiza reauditorías en los siguientes casos:

- una nueva versión de especificación,
- un cambio en su proceso de escritura, proveedor de etiquetas o tipo de chip,
- una nueva línea de productos bajo la misma certificación,
- una queja fundada.

### 7. Revocación

La certificación puede ser retirada. Cuando esto ocurre, TigerTag Corp **deja de emitir firmas**, elimina al socio del registro y termina la licencia de uso de la marca.

La primera consecuencia es la que importa, y es por eso que el programa tiene peso: la firma TigerTag+ se emite con una clave privada que posee TigerTag Corp. No puede ser falsificada, ni puede ser emitida por nadie más. **La revocación es técnicamente real, no simplemente contractual.**

---

## Componentes: Plataforma Compatible con TigerTag

Los chips, inlays, soportes, módulos lectoras y firmware son **componentes**: terminan dentro de un producto de terceros. Un componente que pasa la auditoría se certifica como **Plataforma Compatible con TigerTag** y puede llevar el logotipo en el propio componente y en su propio empaque.

Un producto terminado **no** se certifica simplemente por contener una plataforma compatible. Un carrete equipado con inlays certificados, o una impresora construida alrededor de un módulo lectora certificado, aún necesita su propia certificación antes de que el logotipo aparezca en el producto o su empaque — lo que se audita es el componente, no cómo el producto escribe, coloca o utiliza dicho componente. El uso de una plataforma compatible sí acorta esa auditoría. La misma regla separa la *Plataforma Compatible* de Zigbee de un producto final certificado.

---

## Rebranding de un producto certificado

El filamento y la resina se etiquetan ampliamente en blanco. Si usted vende, bajo su propia marca, un producto ya certificado por su fabricante, no repite la auditoría completa: la certificación se transfiere, sujeta a una tarifa reducida y a una lista propia.

Los hechos auditados no cambian. El nombre en la caja sí.

---

## Registro certificado

Cada socio certificado y línea de productos se lista públicamente. Ese registro es la **única forma autoritativa en la que un comprador puede verificar si un logotipo en un carrete es legítimo**, y la única forma en la que un socio puede demostrar que lo ha ganado.

Cumple el mismo papel que el Libro de Cumplimiento Distribuido para Matter, con el mismo propósito:
verificación sin necesidad de confianza.

---

## Independencia

Hoy en día, la auditoría es realizada por TigerTag Corp. A medida que el número de socios aumenta, TigerTag Corp pretende autorizar laboratorios de prueba independientes, tal y como lo hace la Connectivity Standards Alliance. Decimos esto claramente en lugar de sugerir una independencia que aún no poseemos.

---

## Preguntas

Certificación, acuerdos con socios y horario de tarifas: **licensing@tigertag.io**

Nada en esta página es necesario para implementar el protocolo. Consulte
[`LICENSING.md`](LICENSING.es.md) y [`TRADEMARK.md`](TRADEMARK.es.md).
