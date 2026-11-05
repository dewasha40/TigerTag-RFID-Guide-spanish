> **Traducción informativa:** versión en español de [`TRADEMARK-FILING.md`](TRADEMARK-FILING.md). Si hay discrepancias o se requiere interpretar obligaciones jurídicas, prevalece el original en inglés.

# Presentación de marca — dossier de preparación

> **No es asesoramiento legal.** Este documento recopila en un solo lugar todo lo que se necesita para la presentación, de manera que el trabajo con un abogado (o una presentación directa ante el INPI) comience desde decisiones ya tomadas, en lugar de partir de una página en blanco. Cada punto marcado **DECIDE** requiere una respuesta humana; cada punto marcado **CONSULTAR CON UN ABOGADO** es un juicio legal que no debe tomarse de este documento.

>
> Estado: **nada está presentado en ningún lugar** (INPI, EUIPO, USPTO) hasta el **2026-07-19**.

---

## 1. Por qué esto bloquea el negocio, no solo el trámite

El protocolo está abierto intencionalmente, por lo que la licencia no es lo que impide que un fabricante utilice TigerTag — y tampoco se pretende que lo sea. Lo que impide que impriman **"TigerTag Certified"** en una caja sin haber certificado nada es que el *nombre* es una marca comercial cuya protección puede hacerse valer. Esto es exactamente el modelo Zigbee / Matter: especificación abierta, logotipo protegido.

**Por tanto, el programa de certificación no tiene efecto hasta que la marca se registre.** Puede documentarse y operarse, pero no puede hacerse valer contra alguien que lo ignore. Este es el única dependencia externa en la que se basa el plan comercial.

---

## 2. Solicitante — DECIDE PRIMERO, todo lo demás sigue

Los documentos en este repositorio están redactados en nombre de **"TigerTag Corp"** (33 menciones en 7 archivos). La verdadera entidad jurídica detrás del proyecto es **3D FRANCE**. No pueden ser ambas correctas.

|  | 3D FRANCE | "TigerTag Corp" |
|---|---|---|
| Existe como entidad registrada | **Sí** — SIREN 820444305, establecida en 2016 | **No verificado — probablemente no** |
| Utilizada para la identidad de firma de código de Azure | Sí | No |
| Mencionada en los documentos de certificación/marca | No | Sí, en todos los lugares |

**Riesgo:** un acuerdo firmado por una entidad que no existe puede ser ineficaz — y el contraparte, no usted, es quien se beneficia de ello. **CONSULTAR CON UN ABOGADO** si se debe presentar en nombre de 3D FRANCE ahora, o si se debe primero incorporar la entidad con el nombre y luego presentar en su nombre. Presentar en un nombre y luego asignar posteriormente es posible, pero implica un paso adicional y un pago de registro.

**Datos del solicitante (3D FRANCE), listos para pegar:**

```
Name:      3D FRANCE
SIREN:     820444305
Address:   12G rue de l'Europe, 31150 LESPINASSE, Haute-Garonne, France
Contact:   benoit@tigertag.io  /  tigertag@tigertag.io
Domains:   tigertag.io, tigersystem.io
Applicant: Benoit Michaut
```

Una vez decidido, la misma cadena debe corregirse en los 7 archivos que mencionan "TigerTag Corp"
(`TRADEMARK.md`, `CERTIFICATION.md`, `LICENSING.md`, `LICENSE_COMMERCIAL.md`, `README.md`,
`SECURITY.md`, `CONTRIBUTING.md`) y en la línea `©`.

---

## 3. Qué presentar, en orden de prioridad

El presupuesto es limitado, por lo que se debe presentar en el orden de lo que realmente protege los ingresos. Las marcas que aparecen más abajo pueden esperar.

| # | Marca | Por qué | Prioridad |
|---|---|---|---|
| 1 | **TigerTag** | El protocolo, los chips vendidos a fabricantes, toda la marca | **Esencial** |
| 2 | **TigerTag Certified** | El palo de la certificación — sin ella, la etiqueta no es protegible | **Esencial** |
| 3 | **TigerTag+** | El nivel pagado y firmado | Alta |
| 4 | **TigerSystem** | Nombre general del ecosistema | Media |
| 5 | **TigerScale**, **TigerPOD** | Hardware abierto, dado gratuitamente — valor de marca bajo y ambos tienen colisiones conocidas | Baja |
| — | **TigerData** | Nombre de visualización para entradas sin chips; vocabulario interno, no un producto vendido | Probablemente omitir |
| — | **TigerTag Compatible** | Nivel gratuito y autodeclarado — protegerlo importa menos que proteger "Certified" | Opcional |

**CONSULTAR CON UN ABOGADO:** marca verbal, marca figurativa (logotipo) o ambas? Una marca verbal es más amplia y normalmente se presenta primero; el logotipo puede seguir después.

---

## 4. Clases (Clasificación Nice)
**CONSULTAR CON UN ABOGADO SOBRE LA REDACCIÓN EXACTA** — estas son las clases en las que se enmarca la actividad, no especificaciones validadas.

| Clase | Cubre | Frase a discutir |
|---|---|---|
| **9** | Los chips y el software — **la clase principal** | Etiquetas y transpondedores RFID y NFC; chips electrónicos en blanco y codificados; software descargable para gestión de inventarios; software grabado |
| **42** | El servicio en la nube y el aspecto técnico de la certificación | Software como servicio (SaaS); diseño y desarrollo de software informático; asesoría técnica; **servicios de control de calidad y autenticación** |
| **35** | Solo si se opera un directorio/marketplace de productos certificados | Compilación y gestión de un registro de productos certificados; servicios de información comercial |
| **45** | Solo si la licencia de marca es una actividad formal | Licencia de propiedad intelectual |

Las clases 9 y 42 son el par fundamental. Las 35 y 45 son adicionales para equilibrar su costo.

**Nota sobre la clase 9 — este es el lugar donde se encuentra el riesgo de colisión.** Ver §6.

---

## 5. Marca de certificación, o marca ordinaria bajo licencia? — CONSULTAR CON UN ABOGADO

Hay dos instrumentos legales distintos, y la elección tiene una consecuencia estructural:

- **Una marca ordinaria**, licenciada contractualmente a socios certificados. Flexible; el control
  proviene del acuerdo de licencia.
- **Una marca de certificación** (*marque de garantie ou de certification* en Francia desde 2019, marca de certificación de la UE desde 2017). Diseñada específicamente para este fin, pero viene con **regulaciones de uso**
  presentadas ante la oficina — y, lo más importante, **el titular de una marca de certificación de la UE no puede ejercer una actividad que implique la provisión de bienes o servicios del tipo certificado.**

**Esa restricción puede ser decisiva aquí**, ya que el plan es vender chips *y* certificar a los fabricantes que los usan. Si se aplica, una marca de certificación formal podría ser incompatible con el modelo de negocio, lo que empujaría hacia una marca ordinaria licenciada bajo contrato — lo cual es lo que ya describe `CERTIFICATION.md`. **Esta es la pregunta más importante que debe plantearse al abogado**, ya que moldea los documentos tanto como la presentación.

---

## 6. Marcas previas encontradas — verificar antes de presentar

Solo señales públicas de internet, recopiladas durante la revisión del 2026-07-19. **Ninguna de estas es una conclusión legal** — una búsqueda adecuada de disponibilidad es labor del abogado, y debe realizarse *antes* de presentar, no después de un rechazo.

| Marca previa | Campo | Por qué importa |
|---|---|---|
| **TigerTags** (tiger-tags.com) | Rastreadores inteligentes / etiquetas electrónicas | **Cadena idéntica, misma clase 9, campo adyacente.** La señal más seria. El dominio no resolvía, por lo que podría estar inactivo — pero inactivo no es lo mismo que abandonado |
| **TigerScale** (tigerscale.net) | Balanzas, India | Colisión directa con el producto TigerScale, que es una balanza en sí misma |
| **TigerPOD** | Marca de trípode para cámara iShot | Colisión con el nombre TigerPOD |
| **Tiger Data** (ex-Timescale) | Software de base de datos | Aumenta la densidad de marcas de la familia Tiger en tecnología |

**Consecuencia práctica:** la búsqueda de disponibilidad debe realizarse **antes** de gastar en presentaciones, y podría cambiar la lista de prioridades en §3 — por ejemplo, eliminar TigerScale y TigerPOD, o presentarlos solo como marcas figurativas.

---

## 7. ¿Dónde presentar y aproximadamente cuánto cuesta

El orden importa: una primera presentación otorga una **ventana de prioridad de 6 meses** durante la cual las presentaciones posteriores en otros lugares conservan la fecha inicial.
| Oficina | Territorio | Tarifas oficiales estimadas | Cuándo |
|---|---|---|---|
| **INPI** (Francia) | Francia | ~190 € por una clase, ~40 € por clase adicional | **Primero** — más barato, jurisdicción de residencia, establece la fecha |
| **EUIPO** | 27 países de la UE | ~850 € por una clase, ~50 € por la segunda, ~150 € cada una adicional | Dentro de la ventana de prioridad de 6 meses si el mercado de la UE es relevante |
| **USPTO** | Estados Unidos | ~250–350 $ por clase | Solo si se vende en EE.UU. — EE.UU. requiere **prueba de uso en el comercio**, lo cual es una restricción real |

Las tarifas de abogados se suman a estas y suelen superar las tarifas oficiales. **Los datos son indicativos y pueden variar** — confirma en el calendario actual de cada oficina.

**CONSULTA A UN ABOGADO** si el Sistema de Madrid (una solicitud internacional única a través de la WIPO) es más barato que presentar solicitudes separadas para los territorios que realmente se desean.

---

## 8. Hazlo ahora, antes de cualquier presentación — gratis

- [x] Deja de afirmar una inscripción que no existe: `TRADEMARK.md` dijo *"marca registrada"*.
      Corregido el 2026-07-19 a una mera afirmación de marca, con una nota que indica que no está registrada.
- [x] Confirma que no aparece `®` en ningún lugar del producto, del sitio web ni de las guías — revisado en los cinco repositorios el 2026-07-19; la única aparición fue en el informe de revisión que describe exactamente este problema.
- [ ] **Usa ™ de forma consistente** en la primera mención destacada de TigerTag, TigerTag+, TigerTag Certified.
      ™ indica una afirmación, que es cierta hoy en día. ® afirma una inscripción, que no existe.
- [ ] **Decide el solicitante** (§2) y corrige la cadena de entidad en los 7 archivos.
- [ ] **Mantén pruebas de la primera utilización** — capturas de pantalla con fecha, la primera publicación, la primera factura que menciona el nombre, las facturas de compra del dominio. Los derechos no registrados y cualquier futura presentación en EE.UU. dependen ambos de una utilización comprobable, y esta evidencia es más barata de recoger ahora que reconstruirla más tarde.

---

## 9. Lo que ya está sólido

Merece mencionarse, ya que significa que el trabajo aquí es presentar la solicitud en lugar de diseñar: `CERTIFICATION.md`, `TRADEMARK.md` y `VERSIONING.md` fueron evaluados en la revisión del 2026-07-19 como *"una clonación competente de CSA/Matter"* — una división en dos marcas (una gratuita declarada por el usuario vs. una pagada auditada), un proceso completo de conformidad → auditoría → declaración → emisión → vigilancia → revocación, un registro certificado, y una divulgación honesta de que los laboratorios de terceros aún no existen. El programa está diseñado.
**Lo que falta es la inscripción, no el pensamiento.**
