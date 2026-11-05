> **Traducción informativa:** versión en español de [`TRADEMARK.md`](TRADEMARK.md). Si hay discrepancias o se requiere interpretar obligaciones jurídicas, prevalece el original en inglés.

# Política de marcas comerciales — TigerTag & TigerTag+

## TL;DR

- **Sí** — puedes **implementar el protocolo TigerTag** en cualquier producto, de código abierto o propietario, de forma gratuita, para siempre. Ver [`LICENSING.md`](LICENSING.es.md).
- **Sí** — puedes **construir y vender productos comerciales** que lean o escriban chips TigerTag.
- **Sí** — puedes decir que tu producto es **"compatible con TigerTag"**, incluyendo en texto plano
  en el empaquetado de un lector, impresor o software compatible.
- **Sí** — puedes **mostrar el logotipo de TigerTag para indicar compatibilidad**, sin modificaciones — en tu
  aplicación, en tus documentos, en la descripción de tu producto en la tienda.
- **No** — no puedes poner el **logotipo o nombre** ("TigerTag", "TigerTag+", "TigerTag+
  Certificado") **en un chip de RFID / NFC de cualquier formato** — chip, inlay, etiqueta, etiqueta adhesiva, tarjeta, llavero, soporte — **ni en un carrete, botella de resina o su empaquetado**, sin autorización por escrito. Allí, la marca es una declaración de **autenticidad**, no de compatibilidad.
- **No** — no puedes **llamar a tu producto o protocolo "TigerTag"**, ni usar el nombre comercialmente como marca.
- **No** — no puedes **emitir firmas TigerTag+** — nosotros poseemos la clave privada.
- **No** — no puedes **implicar certificación, afiliación o aval** sin autorización por escrito.
- **La certificación es una auditoría, y es un servicio de pago** — ver [`CERTIFICATION.md`](CERTIFICATION.es.md).

> Di lo que hace tu producto *tan fuerte como quieras*. Solo nosotros decimos qué es un TigerTag.

---

## Las licencias y la marca comercial son distintas

Las licencias en [`LICENSING.md`](LICENSING.es.md) regulan la **especificación, la base de datos de referencia y el código de ejemplo** — permiten que leas, cites, traduzcas, implementes, copies y distribuyas, incluso comercialmente, sin royalties ni permiso.

La marca comercial regula los **nombres y la marca** — garantiza que un producto llamado "TigerTag", o que lleva el logotipo de TigerTag como marca de autenticidad, proviene de o está autorizado por TigerTag Corp.

Puedes tener derechos plenos sobre el protocolo y aún así estar sujeto a las reglas de marca comercial sobre el nombre. Esto es práctica estándar en estándares abiertos y código abierto (Arduino, OpenWrt, Prusa Research, GS1, Bluetooth SIG).

> **Nota:** una versión anterior de este documento afirmaba que el protocolo estaba disponible "bajo
> la licencia MIT". Eso nunca fue preciso y ha sido eliminado. La declaración autoritativa sobre qué está bajo qué licencia es [`LICENSING.md`](LICENSING.es.md).

---

## Marcas comerciales protegidas

### "TigerTag"

**"TigerTag"** es una marca comercial de TigerTag Corp.

> **Estado de registro.** TigerTag se afirma como una marca no registrada ("common law") y se escribe **TigerTag™**, nunca TigerTag®. No se ha presentado ninguna solicitud en INPI, EUIPO o el USPTO aún; se planea presentarla (ver `docs/TRADEMARK-FILING.md`). No escribas "registrado"
> ni uses el símbolo ® en ningún lugar hasta que exista realmente un certificado de registro — afirmar un registro que no posees es un delito en varias jurisdicciones, incluida Francia, y
> este documento es el que un socio lee antes de firmar.

TigerTag se refiere al **protocolo de identificación de materiales RFID**, al **servicio en la nube**
(`tigersystem.io`), y al **catálogo oficial de productos**.

**Puedes** referirte a "TigerTag" de manera factual y descriptiva
(p. ej. *"compatible con TigerTag"*, *"lee carretes TigerTag"*, *"implementa el protocolo TigerTag
v2.2"*) sin permiso — en prosa, en tus documentaciones, y en texto plano en
la embalaje de un producto que lee o escribe chips TigerTag (ver
[uso nominativo](#nominative-text-on-a-compatible-product)). El nombre nunca podrá imprimirse
directamente en el chip ni en un consumible: ver [Uso del producto](#2-product-use--written-authorization-required).

**No podrá** utilizar "TigerTag" como nombre de un protocolo RFID competitivo, servicio en la nube,
empresa, dominio o marca de producto sin autorización escrita explícita.

### "TigerTag+"

**"TigerTag+"** es una marca registrada de TigerTag Corp y denota una etiqueta cuya identidad lleva
un **identificador de producto del catálogo oficial**, junto con metadatos de enriquecimiento
opcionales almacenados en la nube.

**El `+` significa *identificado*, no *certificado*.** Indica que la etiqueta es un producto
conocido del catálogo, no que alguien haya garantizado su procedencia. Una etiqueta TigerTag+
leída en modo avión se comporta como cualquier otra etiqueta TigerTag: todo lo necesario para
imprimir está en el chip, y el enriquecimiento es un complemento, nunca una dependencia. Una
etiqueta TigerTag+ que no lleve firma alguna es completamente legítima.

Una etiqueta TigerTag+ que **además** lleve una firma válida de ECDSA-P256 es una
**"TigerTag+ Certificada"**. Esa firma es escrita por un fabricante que posee la certificación
TigerTag+, la cual incluyen las herramientas de firma. **TigerTag Corp posee la clave privada**,
por lo que nadie más puede emitir una firma válida — lo cual es el motivo principal por el
que la verificación tiene algún significado.

**No podrá** describir una etiqueta como "TigerTag+ Certificada" a menos que lleve dicha firma:
eso sería tanto un uso indebido de la marca como una afirmación falsa sobre su autenticidad.
Describir una etiqueta del catálogo sin firma como "TigerTag+" es correcto y siempre ha sido
así pretendido.

Verificar una firma es gratuito, offline y sin restricciones. Las claves públicas se publican en
[`database/id_version.json`](database/id_version.json) y están en el dominio público.

La definición canónica del nivel se encuentra en la wiki:
<https://wiki.tigersystem.io/products/tigertag-plus/>. El diseño binario de la firma
depende de lo especificado [aquí](README.es.md#3-verificar-firma-ecdsa-p256-completamente-fuera-de-línea).

---

## Uso del logotipo

**Hay dos usos diferentes del logotipo**, y solo uno de ellos es gratuito.

La distinción es la misma que Zigbee hace entre *"Zigbee Compatible"* y
*"Zigbee Certified"*: decir que su producto **comunica con** TigerTag es una afirmación factual
sobre su producto. Colocar nuestro logotipo **en** un chip, un carrete o su embalaje es una
afirmación sobre **origen y autenticidad** — y un comprador lo interpreta como una garantía.

### 1. Uso referencial — gratuito, no se requiere permiso

**Puede** utilizar el logotipo de TigerTag, sin modificaciones, para indicar **compatibilidad**:

- dentro de la interfaz de usuario de su aplicación,
- en su documentación, README o lista de su tienda,
- en la publicidad que describe con qué funciona su producto.

Condiciones:

- El nombre de su producto debe ser claramente distinto de "TigerTag".
- El logotipo debe permanecer sin modificaciones — no se permite recolorear, estirar ni recomponer.
- Debe aparecer como una declaración de compatibilidad, nunca como un sello o distintivo de calidad.
- No podrá sugerir afiliación, certificación o aprobación.
- Debe respetar las directrices visuales en [`brand/`](brand/).

### Texto nominativo en un producto compatible

Un producto que **lea o escriba** chips TigerTag — un lector, una impresora, una báscula, un cortador, una
aplicación — puede decirlo **en texto plano** en su embalaje, página de producto y manual, sin
permiso. Este es el uso descriptivo (nominativo) que la ley de marcas tolera:
- **solo texto plano**, por ejemplo: *"Compatible con TigerTag"* o *"Lee etiquetas TigerTag"* — no el logotipo, ni una tipografía estilizada, ni un distintivo o sello;
- no más destacado que el texto que le rodea, y nunca más destacado que tu propia marca;
- solo las palabras necesarias para indicar el hecho — no *"oficial"*, *"certificado"*, *"aprobado"* ni *"socio"* a menos que poseas ese estatus;
- **nunca en el chip, ni en un consumible** (hilado, resina, bobina, botella, recarga) **ni en su embalaje** — allí se indica *"esto es un TigerTag"*, lo cual corresponde al uso del producto descrito a continuación.

### 2. Uso del producto — autorización por escrito requerida

**No podrás**, sin una licencia por escrito de uso de marca registrada de TigerTag Corp:

- imprimir, grabar, grabar con láser, codificar como arte o de otro modo reproducir el **logotipo o nombre** de TigerTag — "TigerTag", "TigerTag+", "TigerTag+ Certified", o cualquier variante, abreviatura o traducción de ellos — **en un chip RFID / NFC de cualquier formato**: chip desnudo, inserto (húmedo o seco), etiqueta adhesiva, etiqueta, tarjeta, llavero, moneda, soporte o cualquier otro tipo de carcasa para etiqueta;
- reproducir ese logotipo o nombre **en una bobina, una botella de resina, una recarga o su embalaje**;
- utilizar el nombre de TigerTag **comercialmente como marca o denominación de producto**;
- presentar el logotipo o nombre como **marca de autenticidad, certificación, calidad o asociación**.

Esto abarca la superficie visible de la etiqueta. Lo que lleva la **memoria** del chip es el protocolo en sí mismo: escribir datos TigerTag, incluyendo un identificador de producto TigerTag+, es gratuito y siempre lo será.

También está prohibido, certificado o no:

- utilizar la marca, o una forma modificada, abreviada o combinada de ella, **en un nombre de producto, un nombre de empresa, un nombre de dominio o subdominio, o un identificador de redes sociales** (*"@TigerTagShop"*, *"tigertag.example.com"*, *"TigerTagPro"*);
- describir un producto terminado como certificado porque **contiene un componente certificado** — una Plataforma Compatible con TigerTag (ver [`CERTIFICATION.md`](CERTIFICATION.es.md#componentes-plataforma-compatible-con-tigertag));
- utilizar la marca en una línea de productos que **no esté registrada** en el registro certificado.

La licencia de marca registrada concedida con la certificación es **limitada, no exclusiva, no transferible y revocable**: cubre solo las líneas de productos listadas y termina cuando finalice la certificación.

Cuando se aplica a un producto, la marca ya no dice *"esto funciona con TigerTag"*. Dice
**"esto *es* un TigerTag"** — una afirmación sobre quién lo fabricó y si puede confiarse en él.
Esa afirmación es nuestra y solo nuestra.

La autorización se concede mediante **certificación**: una auditoría de tu producto y de tu proceso, seguida de una licencia de marca registrada. Es un servicio de pago. Ver [`CERTIFICATION.md`](CERTIFICATION.es.md).

### El modelo: la Alianza de Estándares de Conectividad

En productos, TigerTag sigue las reglas que la Alianza de Estándares de Conectividad aplica a Zigbee y Matter:

- el logotipo en un producto, un chip o su embalaje requiere **certificación**;
- un producto certificado **debe mostrar** el logotipo, y está **listado** en un registro público;
- los componentes certificados son *Plataformas Compatibles*, y no certifican el producto en el que se instalan;
- el logotipo nunca aparece en un nombre de producto, un dominio, un subdominio o un identificador de redes sociales, y nunca se modifica;
- la licencia es **limitada y revocable**.

Una diferencia es deliberada. Matter está reservado para miembros de la Alianza; el protocolo TigerTag está abierto para todos ([`LICENSING.md`](LICENSING.es.md)). Por eso, la **capa referencial** permanece gratuita para
Cualquier persona, miembro o no: decir *"compatible con TigerTag"* y mostrar el logotipo en una aplicación,
documentación o en una descripción de una tienda. Un estándar abierto que cobrara el derecho de decir que
lo implementas no sería abierto.

### Por qué existe esta línea

La ley de marcas existe para **proteger al comprador**, no a la marca: evita la confusión sobre quién
fabricó un producto y si cumple con el estándar que afirma. Un consumidor que vea nuestro logotipo en una bobina debe poder concluir, sin necesidad de comprobar nada, que el chip es auténtico, correctamente escrito y se comportará según lo prometido por la especificación.

Esa garantía solo tiene valor si verificamos las integraciones detrás de ella. Por tanto, la certificación no es solo trámites administrativos — es lo que hace que la promesa sea real. También es una necesidad legal: un titular de marca que licencia una marca sin ejercer control de calidad sobre los licenciatarios corre el riesgo de perder la marca por completo.

**El protocolo permanece gratuito. La promesa sigue siendo nuestra responsabilidad.**

### Arte gráfico

El contenido de `brand/` está **reservado todos los derechos** y no está cubierto por las licencias
en `LICENSING.md`. El permiso referencial anterior es un permiso limitado y revocable para usar
el logotipo de manera descriptiva; no es una licencia de derechos de autor sobre el arte gráfico.

---

## Lo que puedes hacer libremente

| Acción | ¿Permitido? |
|---|---|
| Leer, citar y traducir la especificación | Sí (CC-BY-4.0) |
| Implementar el protocolo en un producto de código cerrado | Sí (concesión irrevocable) |
| Enviar un impresor, cortador o lector comercial que hable TigerTag | Sí |
| Copiar el código de ejemplo en tu firmware | Sí (Apache-2.0) |
| Incorporar `database/*.json` en tu producto | Sí (CC0, no se requiere atribución) |
| Verificar una firma TigerTag+ sin conexión | Sí |
| Escribir datos TigerTag — incluyendo un ID de producto TigerTag+ — en la memoria de un chip | Sí |
| Decir "compatible con TigerTag", incluyendo en un producto comercial | Sí |
| Escribir "Compatible con TigerTag" **en texto plano** en el empaque de un lector, impresor o software compatible | Sí — uso nominativo, sin logotipo |
| Mostrar el logotipo no modificado **en tu aplicación, documentación o descripción de tienda** para mostrar compatibilidad | Sí |
| Describir los datos de tu etiqueta como "TigerTag+" (un ID de producto del catálogo) en tu aplicación, documentación o descripción | Sí |
| Proponer un cambio al protocolo | Se fomenta — véase [`CONTRIBUTING.md`](CONTRIBUTING.es.md) |
| Colocar el **logotipo o nombre** de TigerTag en un **chip RFID / NFC de cualquier formato** (chip, inlay, pegatina, etiqueta, tarjeta, llavero, soporte) | No — autorización escrita + certificación |
| Colocar el **logotipo o nombre** de TigerTag en un **bobina, botella, recarga o su empaque** | No — autorización escrita + certificación |
| Usar el nombre de TigerTag **comercialmente como marca o designación de producto** | No (marca registrada) |
| Presentar el logotipo o nombre como **sello de autenticidad, calidad o colaboración** | No — autorización escrita + certificación |
| Nombrar tu aplicación o protocolo "TigerTag" | No (marca registrada) |
| Nombrar tu empresa o dominio "TigerTag" | No (marca registrada) |
| Usar "TigerTag" en un subdominio o en un nombre de usuario de redes sociales | No (marca registrada) |
| Llamar a un producto terminado certificado porque contiene un chip, inlay o módulo certificado | No — el producto necesita su propia certificación |
| Crear un protocolo RFID competitivo llamado "TigerTag" | No (marca registrada) |
| Emitir o falsificar una firma TigerTag+ | No (custodia de claves) |
| Describir una etiqueta como "TigerTag+ **Certificado**" sin una firma válida | No (marca registrada + representación falsa)
| Solicitar certificación TigerTag sin acuerdo | No — véase [`LICENSE_COMMERCIAL.md`](LICENSE_COMMERCIAL.es.md) |

---

## Integración oficial

Tres palabras, y solo una de ellas nos concierne:

- **Oficial** — realizada por TigerSystem. Una declaración de origen, no una marca que se otorgue.
- **Certificada** — realizada por un tercero, auditada y validada por TigerSystem. Abierta a
  cualquier cosa que un tercero construya, ya sea hardware o software: la línea se traza según si alguien
  ha revisado, no según qué tipo de producto sea.
- **Compatible** — realizada por un tercero, declarada por el propio tercero. Gratuita, no auditada, no se requiere permiso
  y así seguirá siendo.

La certificación se divide en dos ámbitos, **TigerTag Certified** y **TigerTag+ Certified**, siendo
este último el que abarca el manejo verificado de etiquetas firmadas. Quién puede solicitar qué, qué verifica la auditoría,
y qué cuesta cada marca se define en
[`CERTIFICATION.md`](CERTIFICATION.es.md) — ahí es donde residen esos hechos, y no se repiten aquí.

Si fabricas filamento o resina y deseas **medios TigerTag oficialmente suministrados**
(portadores preimpresos), **firmas TigerTag+**, **asignación de identificadores de producto**, el derecho a colocar
**el logotipo o nombre de TigerTag en tus chips, en tu producto o en su embalaje**, o **el estatus de socio certificado**, necesitas la certificación.

La certificación es una **auditoría** — de tu producto y de tu proceso — seguida de una licencia de marca. Es un servicio de pago, siguiendo el modelo que utiliza la Connectivity Standards Alliance para Zigbee
y Matter. El proceso, lo que verifica la auditoría, la vigilancia y la revocación se describen
en [`CERTIFICATION.md`](CERTIFICATION.es.md). El propio acuerdo se encuentra en
[`LICENSE_COMMERCIAL.md`](LICENSE_COMMERCIAL.es.md).

Los socios certificados se listan públicamente. Ese registro es la única forma autoritativa para que un comprador
verifique si un logotipo en una bobina es legítimo.

**Ninguna de estas cosas es necesaria para implementar el protocolo.** Implementa el protocolo libremente, vende libremente, di
"compatible con TigerTag" libremente. La certificación es necesaria solo para hacer la *promesa* —
para colocar nuestro sello en tu producto y decirle a un comprador que es auténtico.

---

## Preguntas

Abre un problema, o contacta con nosotros en [Discord](https://discord.gg/3Qv5TSqnJH).
Para solicitudes de autorización de marca: [tigertag@tigertag.io](mailto:tigertag@tigertag.io).

© 2025–2026 TigerTag Corp.
