# Instrucciones de traspaso — ExoFarm Research Resources

> **Documento para el agente que continuará el desarrollo de la web en un entorno local.**
> Estado de referencia: 30 de octubre de 2026. Leer completamente antes de modificar el proyecto.

## 1. Objetivo y decisión editorial DEFINITIVA

Se está construyendo una **página web complementaria a un póster científico** sobre posibles tecnofirmas atmosféricas asociadas con agricultura intensiva en exoplanetas. La página se abrirá desde el **código QR impreso en el póster** durante un congreso. El visitante debe poder reconocer el trabajo inmediatamente, consultar la literatura y profundizar en la explicación física.

**La decisión más importante del usuario es que la primera cosa que se debe ver al entrar sea el PÓSTER COMPLETO, grande y sin confusión.** No quiere una página de promoción, ni una landing page con héroe, ilustraciones enormes, cuatro tarjetas de resultados, botones que compitan con el póster, ni un rediseño divulgativo del contenido. Se probó una versión más elaborada y el usuario la descartó expresamente.

**Orden obligatorio, de arriba abajo:**

1. **Póster final completo**, visible en la misma página, con enlace claro para abrir y descargar su PDF original de alta calidad.
2. **References**, en el centro de la página: bibliografía del manuscrito, bien presentada y con enlaces DOI/URL donde existan.
3. **Extended scientific context**, al final: desarrollo científico organizado y legible de los conceptos, métodos, resultados, limitaciones e interpretación, utilizando solo material autorizado del borrador y los pósteres.

Se permite una barra de navegación MINIMALISTA con anclas «Poster», «References» y «Extended text», pero no debe desplazar ni ocultar el póster. La interfaz y el texto público van **en inglés**; este documento de coordinación va en español.

Título de la web propuesto: **ExoFarm — Poster & Supporting Information**.

## 2. Identidad y alcance científico

Título del póster: **Atmospheric Technosignatures in ExoFarm Scenarios around M-Dwarf Stars**.

Autores del póster: **David Santiago Duque Castaño, Jorge I. Zuluaga y Lauren Flor-Torres**. El correo del autor principal aparece en el PDF final; usar únicamente datos de contacto presentes en los materiales, sin inventarlos.

La pregunta central: **cómo la radiación de distintas estrellas afecta la acumulación de N₂O y NH₃ derivados de emisiones agrícolas a gran escala, y qué tan detectables/recuperables resultarían sus firmas espectrales**.

Idea clave: la agricultura intensiva perturba el ciclo del nitrógeno. Estas emisiones no se traducen directamente en abundancias atmosféricas: intervienen fuentes y sumideros, fotólisis, transporte y espectro UV estelar. Se estudian escenarios A0 (preagrícola), A1 (Tierra moderna), A2 (ExoFarm moderado) y A3 (ExoFarm extremo). Se modela la fotoquímica en ambientes con irradiación solar, TRAPPIST-1 y Proxima Centauri, con observabilidad simulada en **transmisión con JWST** y **emisión térmica con LIFE**.

Herramientas citadas en el material: **VULCAN** (fotoquímica), **POSEIDON** (espectros / retrievals), **PandExo** (ruido instrumental JWST), **LIFEsim** (simulaciones LIFE) y **MultiNest** (inferencia bayesiana). Evitar presentar LIFE como instrumento actualmente operativo: es un concepto de futura misión/observatorio.

**Interpretación cautelosa:** una mayor concentración de N₂O o NH₃, incluso conjunta, **no demuestra de manera exclusiva agricultura extraterrestre**. N₂O puede tener fuentes naturales, y NH₃ depende fuertemente de sumideros. No confundir una estimación de S/N molecular con evidencia de identificación bayesiana.

## 3. Fuentes y jerarquía documental

El usuario entregó cuatro tipos de material:

### A. Póster final: fuente pública principal

**`Poster_finale.pdf`** (una página A0). Es la versión visual final y **debe mostrarse en la cabecera**, íntegra y con los márgenes y logotipos intactos. Este es el documento para abrir/descargar como póster; no sustituirlo silenciosamente por una versión previa ni por una reconstrucción HTML.

### B. Póster largo: fuente de contextualización

**`Poster(2).pdf`** (también una página A0). Contiene desarrollo y explicaciones más largos. Úsese para comprender cómo se formularon antecedentes, métodos y resultados que se redujeron en el póster final. Puede servir para redactar la explicación de la tercera sección, pero **NO sustituye al póster final en la parte superior**.

### C. Manuscrito de trabajo: fuente PRIVADA, NO publicable

**`Exofarms_Photochemistry.zip`**, con `ExoFarms_Photochemistry_v2.tex`, `reference.bib`, imágenes y otros recursos. También se entregó **`Exofarms_Photochemistry (3).pdf`**, un borrador de 34 páginas; puede contener material posterior al corte y resultados todavía en revisión.

**Restricción esencial del usuario: usar SOLAMENTE el contenido del `.tex` que aparece ANTES del marcador literal `{HASTA AQUÍ VAMOS}`.**

Procedimiento seguro para leerlo:

```python
from pathlib import Path
tex = Path('ExoFarms_Photochemistry_v2.tex').read_text(encoding='utf-8')
marcador = '{HASTA AQUÍ VAMOS}'
assert marcador in tex, 'No se localizó el límite aprobado; detener la extracción'
texto_autorizado = tex.split(marcador, 1)[0]
```

**No utilizar por accidente el resto del `.tex`, ni tratar el PDF de 34 páginas como si estuviera todo aprobado.** El manuscrito **no está publicado**; no enlazar, exhibir, distribuir ni subir el PDF/TeX completo ni presentar el artículo como aceptado o publicado. El texto de la web debe ser un **desarrollo explicativo nuevo**, basado en las secciones aprobadas, no un volcado indiscriminado del manuscrito. El acceso al artículo se podrá agregar cuando el autor lo autorice expresamente.

Antes del marcador, se identificaron apartados sobre introducción; nitrógeno y sus ciclos; fuentes y sumideros de NH₃; fuentes y destino estratosférico de N₂O; agricultura como transición tecnológica; escenarios ExoFarm; espectros de transmisión; espectros de emisión; simulaciones LIFE; y retrievals. No completar huecos con resultados de partes posteriores.

### D. Bibliografía

**`reference.bib`** dentro del ZIP es la fuente de metadatos para la sección **References**. Se observaron **84 entradas BibTeX** en el archivo. La última web generada visualizaba **81 referencias**; esta diferencia debe comprobarse, no asumirse como correcta. Decidir el criterio editorial: mostrar las referencias efectivamente citadas en la parte autorizada y el póster, o una bibliografía completa aprobada por el autor. No añadir trabajos innecesarios ni inventar DOI, años o títulos. Revisar con especial atención entradas cuya capitalización o título pueda haberse dañado al convertir BibTeX a HTML (LaTeX, subíndices, títulos truncados y caracteres especiales).

**Nota de consistencia:** en versiones previas del póster se mencionan porcentajes diferentes para NH₃ (65 % frente a 81 %), que pueden representar categorías de emisiones distintas (por ejemplo agricultura vs. actividades antropogénicas). **No fusionar esas cifras ni atribuir 81 % específicamente a agricultura sin revisar el artículo original y las definiciones.** Mantener el sentido exacto de la fuente elegida y señalar al autor cualquier discrepancia.

## 4. Valores y afirmaciones científicas que requieren cuidado

El póster tuvo múltiples actualizaciones de la tabla bayesiana: **no reutilizar tablas antiguas por comodidad**. Si se mencionan cifras en el texto ampliado, contrastarlas con el último cuadro aprobado y el PDF final. La tabla de referencia corregida corresponde al SVG **`ExoFarm_lnB_sobria_horizontal_DATOS_ACTUALIZADOS.svg`**, modificado a partir del SVG original para conservar su estilo.

Resultados destacados en la última revisión:

- **N₂O, A1, 100 h:** ln B = **9.834 ± 0.341** (nueva cifra; antes figuraba 1.61 en una versión obsoleta).
- **N₂O, A3, 10 h:** ln B = **9.142 ± 0.292**.
- **N₂O, A3, 100 h:** ln B = **84.661 ± 0.347**.
- **NH₃, A3, 100 h:** ln B = **2.749 ± 0.345**.
- En el póster final, para el enriquecimiento conjunto de N₂O y NH₃ sobre A1 a 100 h, figura una **probabilidad posterior conjunta de 98.67 %**. El póster largo menciona un incremento de odds posterior/prior de aproximadamente 114; preservar la diferencia entre probabilidad y odds.

El texto debe transmitir que **N₂O es la especie más accesible en las configuraciones simuladas**; para NH₃ se obtiene evidencia moderada en 100 h bajo A3. **JWST** sigue siendo difícil en la configuración de transmisión estudiada, mientras que **LIFE** muestra sensibilidad prometedora para N₂O. No universalizar las conclusiones a todos los planetas ni todos los instrumentos.

En métodos y discusión, distinguir claramente: tasas de emisión superficial → composición química vertical → espectros sintéticos → S/N instrumental → retrievals bayesianos. Es importante no confundir el modelo fotoquímico vertical con una recuperación **isochemical** de abundancias efectivas.

## 5. Diseño y experiencia de usuario

**Regla principal:** cuando el visitante abre `https://d4san.github.io/exofarm-resources/`, el primer bloque visible debe ser el **póster completo** (imagen de vista previa de toda la página), con suficiente ancho, en alta calidad y sin recortar. La vista previa es para orientación; el PDF original debe abrirse de forma muy visible y permitir zoom/descarga. En móvil, no fuerce una imagen ilegible de 100 % de ancho sin ofrecer claramente el PDF ampliable.

- Sin héroe ilustrado separado ni bloques de «Key findings» antes del póster.
- Sin carruseles, tarjetas de marketing, introducciones largas ni animaciones pesadas.
- Barra de navegación mínima, idealmente: «Poster · References · Extended text».
- Después de la imagen del póster, sección de referencias ordenada y legible; luego texto científico con subtítulos y párrafos.
- Cuidar accesibilidad: textos alternativos, jerarquía de títulos, enlaces descriptivos, contraste y uso móvil.
- Imagen/PDF deben ser archivos locales estables, servidos por GitHub Pages. Utilizar rutas relativas correctas para el proyecto GitHub Pages; no rutas absolutas a `/` que fallen con el prefijo `/exofarm-resources/`.
- Mantener el aspecto gráfico **sobrio y académico** del póster: serif semejante a Times New Roman, azul oscuro `#002642` y acentos `#56E3DB` (cian), `#95E36B` (verde), `#BD62E3` (violeta), `#E34F95` (magenta). Blanco y grises muy claros. Las ilustraciones artesanales/de fieltro forman parte de la identidad del póster, pero **no hay obligación de repetirlas en la web**: el póster por sí mismo ya aporta la identidad visual.

## 6. Código y GitHub Pages: estado conocido

**Cuenta GitHub:** `D4san`.

**Repositorio PÚBLICO de esta página:** `D4san/exofarm-resources`.

**URL permanente que ya está impresa en el QR:** `https://d4san.github.io/exofarm-resources/`.

**MUY IMPORTANTE:** mantener inalterada esa URL: no renombrar el repositorio ni cambiar el dominio. El repositorio científico `D4san/exofarm` es otro proyecto y NO debe modificarse.

Se configuró GitHub Pages desde **`main` → `/(root)`**, con HTTPS; el usuario mostró una captura de esa configuración. Se habían subido `index.html`, `styles.css`, `README.md` y `.nojekyll`. Al principio la URL arrojaba un **404** porque Pages todavía no estaba publicando; la captura siguiente mostró que la rama `main` estaba seleccionada. **No hay una verificación final de que el despliegue público haya quedado correcto**, así que revisar estado en Actions y Settings → Pages antes de anunciar publicación exitosa.

En la última iteración se subió al repositorio una **versión simplificada del HTML y CSS, con el póster primero**. Aun así, podría faltarle la imagen y el PDF del póster en el repositorio remoto: verificar antes de asumir que todo está desplegado.

**Paquete local más reciente:** `ExoFarm_Poster_First_Website.zip`. Contenido constatado:

```text
README.md
index.html
styles.css
.nojekyll
downloads/exofarm-poster.pdf        (póster final, aprox. 6.1 MB)
assets/poster-preview.webp          (vista previa completa del póster)
```

Se puede comenzar por **descomprimir este ZIP en el directorio de trabajo local** y compararlo con el remoto. El HTML de ese paquete ya organiza la página como «Poster → References → Extended scientific context», contiene 81 referencias y siete secciones de texto científico. **Es un punto de partida, NO una versión definitivamente revisada por el usuario**. Comprobar el contenido, las rutas y las referencias antes de publicar; puede haber entradas bibliográficas mal formateadas.

La web es **estática**: HTML/CSS + archivos estáticos bastan; no necesita framework, backend, base de datos, autenticación o servicios de terceros. Es preferible minimizar complejidad y dependencias.

## 7. Cómo debe trabajar el agente local

1. **Abrir el repositorio local** y confirmar que es `exofarm-resources`, no el repositorio científico.
2. **Revisar el ZIP más reciente**, el HTML/CSS y las versiones del PDF. Usar `Poster_finale.pdf` como póster visible.
3. **Garantizar que la página empieza directamente con el póster** y que hay un botón/enlace claro para abrir y descargar el PDF.
4. **Revisar la bibliografía** usando `reference.bib` y la parte autorizada del `.tex`; corregir DOI, títulos mal representados, duplicados y diferencias entre 81/84 entradas. No suprimir referencias válidas sin criterio explícito.
5. **Revisar el texto ampliado** contrastándolo con las fuentes y el punto de corte. Mejorar claridad y continuidad sin convertirlo en un manuscrito íntegro accesible públicamente.
6. **Verificar todas las cifras** contra la tabla bayesiana definitiva y el póster final. Si hay discrepancias científicas, informar en vez de decidir en silencio.
7. **Probar localmente** la web en escritorio y móvil. Revisar scroll horizontal, legibilidad, tamaño del póster, enlaces a PDF, DOI, navegación, ortografía inglesa y contraste visual.
8. **Ejecutar pruebas de despliegue** para GitHub Pages, con rutas relativas; revisar que no haya recursos rotos o 404.
9. **No hacer push ni cambios remotos automáticamente sin petición del usuario**: actualmente desea continuar el trabajo en local; presentar primero el resultado para revisión. Si el usuario autoriza publicar, desplegar al repositorio correcto y verificar la URL pública.

## 8. Criterios de aceptación

El trabajo estará listo cuando:

- Al abrir el sitio, la primera pieza protagonista sea **el póster completo**, no un encabezado promocional.
- El póster se pueda **abrir en PDF y descargar** sin enlaces rotos.
- Las referencias estén **después del póster y antes del texto largo**, con datos correctos y enlaces útiles.
- El texto científico sea claro, riguroso, en inglés y derivado **exclusivamente de fuentes autorizadas**.
- No se haya difundido ni embebido el borrador del artículo, ni el texto posterior a **`{HASTA AQUÍ VAMOS}`**.
- El diseño no agregue complejidad visual; la web sirva de **acompañamiento al póster**.
- La página sea adaptable a móviles, accesible y funcione en `https://d4san.github.io/exofarm-resources/`, preservando el QR existente.

## 9. Mensaje operativo final para el agente

> **Continúa el desarrollo LOCAL del sitio público `D4san/exofarm-resources`. El usuario NO quiere una landing page sofisticada: quiere ver INMEDIATAMENTE el póster final completo y poder abrir su PDF. Después deben venir las referencias científicas y, únicamente al final, un texto ampliado. Usa como base la última web `ExoFarm_Poster_First_Website.zip` y el póster `Poster_finale.pdf`. Para bibliografía, usa `reference.bib`; para contenido del manuscrito, SOLO el `.tex` anterior a `{HASTA AQUÍ VAMOS}`. Nunca publiques el manuscrito completo ni utilices resultados obsoletos. Conserva la URL fija que ya está en el QR. Revisa visualmente en escritorio y móvil y no subas cambios a GitHub hasta que el usuario lo autorice.**