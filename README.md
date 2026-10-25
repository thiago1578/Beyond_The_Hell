# Beyond_The_Hell — Capítulo 1 (Chapter 1)
Mod de terror analógico / ARG para **Minecraft Java 1.21.1 — NeoForge**.

## Cómo compilarlo
1. Descarga el **MDK de NeoForge 1.21.1** (https://neoforged.net) y copia de él la carpeta `gradle/`, `gradlew` y `gradlew.bat` dentro de esta carpeta
   (o ejecuta `gradle wrapper` si tienes Gradle instalado).
2. Necesitas **JDK 21**.
3. En `build.gradle` revisa `neoForge { version = '21.1.172' }` y pon la versión que uses de NeoForge 1.21.1 (21.1.x).
4. `./gradlew build` → el .jar queda en `build/libs/`. Para probar: `./gradlew runClient`.
5. Importa la carpeta como proyecto Gradle en IntelliJ IDEA / Eclipse si quieres editar.

> El código está escrito contra la API de NeoForge 1.21.1 pero **no pude compilarlo aquí** (sin acceso a internet para bajar NeoForge).
> Si Gradle marca algún error de nombre/import, pégamelo y lo corrijo.

## Qué incluye
- **Menú principal nuevo** `Beyond_The_Hell` + `Chapter 1` (en inglés), animado: estática de cinta, barra de tracking, título con glitch, silueta que se acerca con ojos rojos, REC/timestamp y zumbido ambiente. Botones: Singleplayer, Multiplayer, Options, **idioma de la historia**, Quit.
- **30 dimensiones liminales** (`beyond_the_hell:dim_01` … `dim_30`), cada una con su tipo, bioma, colores de niebla, luz y bloques (Yellow Halls, Pool Rooms, Red Corridor, Empty Mall, Hospital Wing, Sunken Church, … Beyond The Hell).
- **10 criaturas**: Smiler, Skin Walker, Mannequin (se congela si lo miras), Hall Crawler, Static Man (glitch-teleport), Pale Child, Tape Ghoul, The Host, The Viewer (glitch-teleport), Hell Walker (jefe, nivel 20+). Aparecen solas según el nivel y dan *Darkness* al golpear.
- **Música dinámica**: zumbido ambiente → música de persecución (criatura a <28 bloques) → persecución cercana (<10 bloques).
- **Overlay VHS** dentro de las dimensiones (REC, PLAY, timestamp, ruido que empeora cuando hay peligro).
- **Historia con diálogos hablados + subtítulos** en **Español, Inglés, Francés y Portugués** (13 líneas).
- **ARG**: `VHS Tape` con mensajes cifrados (ver abajo).
- Items: `Void Key` (clic derecho = bajar un nivel; tras el 30 vuelves a casa), `VHS Tape`, huevos de aparición, pestaña creativa propia.

## Idioma
- Menú principal: botón de bandera para ciclar **Auto / English / Español / Français / Português** (se guarda en la config).
- También en `Mods → Beyond_The_Hell → Config` (idioma, subtítulos, voces, VHS, música de persecución).
- *Auto* sigue el idioma de Minecraft. Los textos del juego (items, criaturas, dimensiones) existen en en_us, es_es/es_mx/es_ar/es_cl/es_uy/es_ve, fr_fr/fr_ca, pt_br/pt_pt.

## Comandos (OP)
- `/bth dim <1-30>` → ir a una dimensión
- `/bth return` → volver al overworld
- `/bth say <id>` → reproducir una línea (`intro`, `key`, `tape`, `chase`, `dim_01`…`dim_08`, `final`)

## Grabar tus propias voces
Las voces ahora son **placeholders** (un blip de radio). Reemplázalos con tus grabaciones `.ogg` (mono, 44.1kHz) con el mismo nombre en:
`src/main/resources/assets/beyond_the_hell/sounds/voice/<en|es|fr|pt>/<id>.ogg`
Textos de cada línea: `assets/beyond_the_hell/dialogue/<idioma>.json`. Puedes cambiar también la música (`sounds/music/*.ogg`).
Para regenerar todo lo sintetizado: `python3 tools/generate_assets.py` (requiere numpy, Pillow y ffmpeg).

## Soluciones del ARG (las 6 cintas)
1. Base64 → `THE DOOR IS ALWAYS OPEN`
2. Hex → `Are you still recording`
3. Binario → `COUNT THE TAPES`
4. Morse → `WHO WAS WATCHING`
5. Texto invertido → `LEVEL 30 HAS NO EXIT`
6. César +3 → `THE DOOR IS BEHIND YOU`

## Notas / ampliar
- Las dimensiones son planas con techo (habitaciones infinitas, cada una con distinta altura/luz/bloques). Para estructuras (pasillos, piscinas, laberintos) lo siguiente es añadir estructuras NBT o un generador propio.
- Las criaturas usan el modelo humanoide con textura propia; para modelos únicos usa Blockbench + GeckoLib.
- Crea un **mundo nuevo** para probarlo; en mundos existentes las dimensiones pueden requerir recargar.

## Obtener el .jar sin instalar nada (GitHub Actions)
1. Crea un repositorio nuevo en github.com y sube todo el contenido de esta carpeta (incluida `.github/`).
2. Ve a la pestaña **Actions** → "Build Beyond_The_Hell" → espera ~3 min.
3. Entra a la ejecución terminada y descarga el artefacto **Beyond_The_Hell-jar**: dentro está el `.jar`.
4. Ponlo en la carpeta `mods` de Minecraft 1.21.1 con NeoForge instalado.
