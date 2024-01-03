---
title: 'Yuzu'
description: 'Yuzu is the best'
date: 2023-07-24
image: '/blog-placeholder-2.jpg'
tags: ["blog", "astro"]
---
**Yuzu: Emulación de Nintendo Switch en Windows y Linux**

**DISCLAMER**
- Partes de esta guía involucran piratería. No me hago responsable de las acciones tomadas en base a este material. 
- Agradecimientos al usuario AbdGaming de reddit por hacer una guía tan detallada sobre el tema. En mi caso, solo añado mis propios métodos y algún paso extra junto a capturas de pantalla para hacer el proceso más ameno. Además de, claro está, traducirlo al castellano. 
	- [(Updated) Complete guide for setting up Yuzu and Ryujinx emulators. Download links available : NewYuzuPiracy (reddit.com)](https://www.reddit.com/r/NewYuzuPiracy/comments/uduaut/updated_complete_guide_for_setting_up_yuzu_and/)

---

**PROGRAMAS REQUERIDOS PARA LOS JUEGOS E INSTALACIÓN**
- Extensión uBlock Origin (bloqueador de anuncios)
	- Firefox: [uBlock Origin – Consigue esta extensión para 🦊 Firefox (es) (mozilla.org)](https://addons.mozilla.org/es/firefox/addon/ublock-origin/)
	- Chrome: [uBlock Origin - Chrome Web Store (google.com)](https://chrome.google.com/webstore/detail/ublock-origin/cjpalhdlnbpafiamejdnhcphjbkeiagm?hl=es)
	- Edge: [uBlock Origin - Microsoft Edge Addons](https://microsoftedge.microsoft.com/addons/detail/ublock-origin/odfafepnkmbhccpbejgmiehpchacaeak?hl=es-ES)
	- Opera: [Extensión uBlock Origin - Complementos de Opera](https://addons.opera.com/es/extensions/details/ublock/)
- WinRAR: [Winrar 6.11  El mejor descompresor - Artista Pirata](https://www.artistapirata.com/winrar-5-80-final-windows-el-mejor-descompresor/)
	- 7zip alternativa: [7-Zip](https://www.7-zip.org/)
- 1.1.1.1 DNS Resolver Cloudflare: [1.1.1.1 — The free app that makes your Internet faster.](https://1.1.1.1/)
	- En caso de no poder entrar al link porque se redirige automáticamente a la dirección del router, instala Tor Browser y descargarlo desde ahí:
		- [Tor Project | Descargar](https://www.torproject.org/es/download/)
- qbittorrent: [qBittorrent Official Website](https://www.qbittorrent.org/)
- Un bloqueador de anuncios como ublock Origin es muy recomendable por no decir necesario. 

Una vez instalado todo esto, podemos proceder a instalar los juegos. 

---

## Instalando Yuzu
Para instalar Yuzu, nos dirigimos a esta página.
[yuzu - Nintendo Switch Emulator](https://yuzu-emu.org/)

![](https://i.imgur.com/VL3l55Z.png)

Cuando estemos dentro, es necesario descargar el complemento de Visual C++ para que el emulador funcione correctamente. Si no está instalado, es bastante probable que salte el error ### **“VCRUNTIME140_1.dll was not found”**. Para más información: [FAQ - yuzu (yuzu-emu.org)](https://yuzu-emu.org/wiki/faq/#yuzu-starts-with-the-error-vcruntime140_1dll-was-not-found)


![](https://i.imgur.com/Lpsfqip.png)

Al final de la página, encontramos el botón de instalación de Windows x64

Descargamos el instalador y seguimos los pasos. Esta guía no informa sobre la versión de desarrollo o "early access" de yuzu, solo la versión normal y estable. Para más información: [yuzu Early Access - yuzu (yuzu-emu.org)](https://yuzu-emu.org/help/early-access/)

Si encuentras errores durante la instalación o en el resto del proceso, consulta la página FAQ de yuzu: 
[FAQ - yuzu (yuzu-emu.org)](https://yuzu-emu.org/wiki/faq/)

## Keys
Las keys son vitales para que yuzu funcione. La primera vez que abramos el programa, nos dirá que faltan las keys. 

Para descargar las keys, el archivo prod.keys, nos dirigimos aquí:  http://www.mediafire.com/file/ldsbcskbt0z10kv/prod.keys/file 


![](https://i.imgur.com/kJc2edb.png)
- Página de descarga de mediafire para descargar las llaves. 


![](https://i.imgur.com/b5MG3oa.png)
- Abrimos la carpeta de yuzu clickando en file --> open yuzu folder


![](https://i.imgur.com/wsZdt37.png)
- Una vez abierta, abrimos la carpeta keys y arrastramos el archivo "prod.keys" dentro. 

![](https://i.imgur.com/MFweora.png)

Después de eso, cerramos y volvemos a abrir yuzu y listo. 

En caso de que las keys estén desactualizadas, nos dirigimos a esta página para ver la lista de keys actualizadas: [Keys - Google Drive](https://drive.google.com/drive/folders/1KAym-RpGIDuJiSmMLmpCtGVbhLm4VjTZ) Al descargarlas, las descomprimimos con WinRAR 

## Firmware (si no tienes problemas con el juego que quieras jugar, salta este paso)
La descarga de firmware para Yuzu no es un requisito. Sin embargo, hay tres o cuatro juegos que fallan en el menú principal sin él. Se recomienda descargar el firmware independientemente.

[Switch Firmwares - Darthsternie's Firmware Archive](https://darthsternie.net/switch-firmwares/)

Abre yuzu, ve a la carpeta yuzu al igual que con las claves, luego navega hasta "nand/system/Contents/registered" y pega todos los archivos de firmware.

## Organización
Es importante mantenernos organizados, y más con los juegos. Es por ello que recomiendo crear una carpeta con juegos de Switch dentro del disco duro. Cada juego puede venir con DLC's y actualizaciones extra. 

Una vez creado el directorio, añadimos la carpeta a través de yuzu. 

![](https://i.imgur.com/Qf1u2K6.png)


## Juegos
Debido a que hay muchos tipos de ROMs, es importante diferenciar los tipos de ROMs que hay y cuales descargar.

**Lista de compatibilidad y optimización de los juegos**
No todos los juegos están igual de bien optimizados. Para información sobre el juego que quieras jugar, consulta esta lista: [Games - yuzu (yuzu-emu.org)](https://yuzu-emu.org/game/)
### Diferencias entre NSP, NSZ y XCI
En resumen, nos debemos de centrar en descargar solo las ROMs NSP para emular con yuzu o con Ryunix. Pero si queremos añadir juegos extra a nuestra Switch existente, podemos usar los otros tipos de archivos. Aquí dejo una explicación en inglés de los diferentes tipos de ROMs sacada de la página: [nsw2u.in | Download Switch Roms eShop NSP XCI NSZ](https://nsw2u.in/)

Añado otra explicación de los propios desarrolladores de yuzu: [Overview of Switch Game Formats - yuzu (yuzu-emu.org)](https://yuzu-emu.org/wiki/overview-of-switch-game-formats/)

### NSP
**What is an NSP file?**
An NSP file is a eShop game package used by the Nintendo Switch console and Switch emulators, such as **Yuzu or Ryujinx**. It stores multiple files, which may include the game ROM, .JPG game icon, game updates, and game metadata. NSP files are typically used for storing backup dumps of Switch games

NSP files can be played on a Nintendo Switch using SX OS and Atmosphere and ReiNX custom firmwares used to play NSP files on a Nintendo Switch using the Goldleaf homebrew application.

### NSZ
**What is an NSZ file?**
NSZ is a compressed and optimized Nintendo Switch eshop NSP of a smaller size, which does not require preliminary unpacking when installing on Switch (only the installation file itself is compressed, the volume of occupied files on the console is exactly the same as when installing .NSP, it does not decrease).  

The format is fully supported by the dbi + nsusbloader installer;  
everything happens transparently, no additional actions need to be done, you can install games as usual.

### XCI
**What is an XCI file?**
An XCI file contains the contents of a Nintendo Switch game card (cartridge dump) in the NX Card Image format. It stores an encrypted backup of a Nintendo Switch game, which includes the Switch game ROM, icons, and metadata. XCI files may also be used to contain updates to a Switch game.

## Páginas de ROMs
-  **[NXBrew.com | Free Nintendo Switch Gaming XCI, NSP Downloads](https://nxbrew.com/)** (recomendada)
- [Ziperto - A Digital Park for Gamers](https://www.ziperto.com/)
- [Switch Archives - Download Game Nintendo (nswgame.com)](https://nswgame.com/category/switch/)
- [ROMs Switch](https://romxci.com/es/nintendo-xci/)

Antes de entrar a las páginas, es necesario tener el WARP 1.1.1.1 de Cloudflare instalado y funcionando. 

![](https://i.imgur.com/mzlaNOx.png)

Si bien podemos usar Ziperto, yo personalmente prefiero NXBrew por la posibilidad de descargar las ROMs vía Torrent. Para mi, es más cómodo.

![](https://i.imgur.com/gHIjo9t.png)

Nos metemos en la página y buscamos en la lupa roja el juego que queramos. 

![](https://i.imgur.com/cgLqy8t.png)

Como hemos mencionado antens, es importante fijarnos que el juego que vayamos a descargar sea NSP. Bajamos hasta el apartado de "Downloads", y clickamos en el Torrent. 

![](https://i.imgur.com/kXmYKSo.png)


En lo siguente pasos, se nos abrirán una web de 1Click Club y después otra web de CutDL.Xyz. Si tenemos el bloqueador de anuncios activado, no debería de surgir ningún problema.

![](https://i.imgur.com/Ff26xxD.png)
Catchap necesario.


![](https://i.imgur.com/W1Vx7lL.png)

![](https://i.imgur.com/9Zvbggh.png)


![](https://i.imgur.com/TMEnmoK.png)

![](https://i.imgur.com/OfZ0fKd.png)


Una vez abierto el qbittorrent, nos aseguramos de que se descargue en la ruta de archivos que hemos creado para juegos de Switch. 

Y después, usando WinRAR, descomprimimos los archivos NSP y se añadirán automáticamente a Yuzu. 

![](https://i.imgur.com/rCMeyCe.png)

## Añadir updates y DLCs

Abre Yuzu. vaya a la esquina superior izquierda y haga clic en "Archivo" e "Instalar archivos en NAND". Luego elige los archivos de actualización/DLC que desees instalar. Espera a que termine la actualización y listo.

La instalación en NAND crea una copia adicional del contenido instalado en la unidad C, por lo que puede eliminar su actualización original y/o archivos DLC después de instalarlos.

Para comprobar si la actualización o DLC se ha instalado correctamente, haga clic con el botón derecho en el juego para el que instaló la actualización/DLC, seleccione "Propiedades" y debería aparecer la actualización/DLC.

## Ajustes para el mejor performance
Una vez instalado, y con los juegos preparados, vamos a cambiar los ajustes necesarios para conseguir el mejor rendimiento. Si no sabes que gráfica tienes, puedes mirarlo en el administrador de tareas (ctrl + shift + esc)

### General, para todas las gráficas y configuraciones
- La precisión de la GPU debe mantenerse normal. Usa alto cuando intente corregir errores visuales. No debe mantenerse encendido si no es necesario, ya que puede reducir el rendimiento en algunos casos. Evita los niveles "extreme (very slow)". Para cambiar la precisión de la GPU, abre la configuración de Yuzu, haz clic en el apartado "Gráficos" a la izquierda, luego en "Avanzado" en la parte superior y configure la precisión de la GPU como consideres.
- Establece la precisión de la CPU en "Auto". La configuración Insegura puede romper cosas y solo debe usarse en circunstancias específicas. En la configuración de Yuzu, "CPU" en el panel izquierdo y configura "Precisión" en "Auto"
- Cambie el archivo de paginación a 10000 MB o 20000 MB. Videotutorial [aquí]([How to Increase VirtualMemory QuickGuide - YouTube](https://www.youtube.com/watch?v=wAMT9LWtvUs)).
- Instala los drivers más recientes para su GPU
	- NVIDIA: [Official Drivers | NVIDIA](https://www.nvidia.com/Download/index.aspx?lang=en-us)
	- AMD: [AMD Drivers and Support | AMD](https://www.amd.com/en/support)
	- Intel: [Download Intel Drivers and Software](https://www.intel.com/content/www/us/en/download-center/home.html)

### Nvidia
- Abra la configuración de Yuzu. Vaya a la pestaña "Gráficos" a la izquierda y asegúrese de que la API esté configurada en "Vulkan". También asegúrese de que seleccione su GPU dedicada/preferida en la opción "Dispositivos".
- OpenGL solo se usará si un juego específico no funciona o tiene problemas en Vulkan.
- Si usas OpenGL, configura el apartado de Shader Backend a "GLASM" para una creación de sombreado más rápida. Una vez que se construyen los sombreadores, configúralo de nuevo en "GLSL". 
- Haz clic derecho en el escritorio y abre el "Panel de control de NVIDIA". Una vez que se abra, haz clic en "Administrar configuración 3D" a la derecha. Ve a la "Configuración del programa" y haz clic en "Agregar". Selecciona Yuzu, luego desplázate hacia abajo en la lista de configuraciones y configure lo siguiente:
	- Sincronización vertical
	- Desactivado Optimización de subprocesos: activado
	- Modo de administración de energía: prefiera el máximo rendimiento
	- GPU de renderizado OpenGL - [Seleccione su GPU]
- Luego haz clic en "Aplicar" en la esquina inferior derecha.

**NOTA: Los jugadores de Smash pueden querer habilitar la baja latencia en el panel de control de Nvidia**

### AMD
- Abre la configuración de Yuzu. Ve a la pestaña "Gráficos" a la izquierda y asegúrate de que la API esté configurada en "Vulkan". También asegúrate de seleccionar tu GPU dedicada/preferida en la opción "Dispositivos".
- Agrega Yuzu como perfil en Radeon Software, esto agregará un caché de nivel de controlador a Vulkan.

**NOTA: Los jugadores de Smash pueden querer habilitar Anti-Lag en Radeon Software**

### Intel
- Abre la configuración de Yuzu. Ve a la pestaña "Gráficos" a la izquierda y asegúrate de que la API esté configurada en "Vulkan". También asegúrate de seleccionar tu GPU dedicada/preferida en la opción "Dispositivos".

 Consejos sobre la precisión de la CPU (independientemente de la GPU que tengas) 
- Establecer la precisión de la CPU en "**CPU insegura**" puede causar ciertos errores o fallas en los juegos, aunque también ha habido casos en los que ocurrió lo contrario.
- Si su CPU AMD se lanzó en 2012 o después, o su CPU Intel se lanzó en 2014 o después, desmarque la opción "Unfuse FMA" que aparece cuando usa la configuración de CPU no segura.

Prácticamente puede comenzar a jugar ahora, ya que todos los pasos requeridos están completos. Las siguientes secciones son opcionales, es decir, instalación de guardados, modificaciones, sombreadores y algunas correcciones de errores.

### Configuración de mandos
Si bien se puede jugar con teclado y ratón, es más recomendable jugar con mando. Yuzu soporta muchos tipos de mandos por no decir la mayoría de Nintendo, PlayStation y Xbox.

Dentro de la configuración  de "Controles", es importante seleccionar el "input device" correcto. Una vez conectemos nuestro mando por USB al PC, abrimos yuzu y dentro de "input device", saldrá la opción del mando que tengamos conectado. Cuando lo detecte, veremos en la página de configuración de yuzu reflejado todo lo que hagamos con el mando. Se pueden conectar hasta 8 mandos diferentes, cada uno con diferente configuración. 

![](https://i.imgur.com/16bJjzr.png)


## Errores comunes
Correcciones de errores u otros problemas 
- Error BKTR: recibe este error al iniciar una actualización, en lugar del juego real. 
- Error de Video Core: los controladores de Vulkan no están actualizados. 
	- Si usa una GPU Nvidia, instale el archivo desde https://developer.nvidia.com/vulkan-beta-45836-windows-10-dch 
	- Para los usuarios de GPU AMD, simplemente actualice a los controladores opcionales más recientes en el Panel de software de AMD. 
- Error "No se pudo encontrar la clave de encabezado NCA": las claves están desactualizadas 
- Error de revisión criptográfica: las claves están desactualizadas. Otra vez. 
- Actualizaciones o DLC que no se instalan: las claves están desactualizadas... otra vez 
- Juegos que no aparecen en tu lista de juegos 
	- Colocaste el juego en una carpeta dentro de tu carpeta de juegos. 
		- Coloca solo el archivo del juego o habilita el escaneo de subcarpetas en Yuzu. 
	- Colocaste una actualización del juego en lugar del juego dentro de la carpeta del juego. Verifique esto mirando el nombre del archivo. Verá [v0] o [v357534]. [v0] es siempre el juego. Si el número es diferente, es una actualización. 
	- El juego está corrupto.

## Extra

### Shaders
Shaders: https://github.com/JENOVAAbsolute/128BB-Shaders 

Para instalar sombreadores: Inicia el juego para el que desea los shaders. Ciérrelo una vez que vea la primera pantalla que aparece. Luego haz clic con el botón derecho en el juego en Yuzu, haz clic en "Abrir caché de tubería transferible" ("Open Transferable Pipeline Cache"") y coloca los sombreadores en la carpeta que se abre.

### Mods
Puede obtener algunas modificaciones de Switch de las siguientes fuentes: 
- Colección de Abd007: [Nintendo Switch - Google Drive](https://drive.google.com/drive/folders/1z2rjO2NAqfDoWTgLEl0FxWI1-8zg2F8P)
- GitHub de TheBoy181:[theboy181/switch-ptchtxt-mods (github.com)](https://github.com/theboy181/switch-ptchtxt-mods) - 
- Página oficial de modificaciones de Yuzu: [Switch Mods · yuzu-emu/yuzu Wiki (github.com)](https://github.com/yuzu-emu/yuzu/wiki/Switch-Mods)

Para instalar mods, haga clic derecho en el juego para el que desea instalar el mod, haga clic en "Abrir ubicación de datos de mod" y pegue la carpeta de mod allí. Debe colocar la carpeta de mod que descargó, y no solo los archivos dentro de ella.

### Saves (Archivos de guardado)
Puedes encontrar guardados aquí:
- Colección de Abd007: https://drive.google.com/drive/folders/1G2gHYZn7Dbx_X9iYUgpOfCBiWCixBTWU?usp=sharing 
- Alternativa: https://www.homebrewgeneral.net/2020/03/switch-games-save.html 
- Para instalar guarda: Haga clic con el botón derecho en el juego para el que desea instalar el guardado, haga clic en "Abrir ubicación de datos guardados" y coloca los archivos guardados allí. 
	- Copia de seguridad de sus archivos guardados: Si alguna vez necesitas reinstalar Yuzu, haga una copia de seguridad de los archivos o carpetas a continuación para no perder el progreso del juego.
	- El siguiente archivo almacena el perfil de usuario del Switch. Algunas partidas guardadas necesitan esto para funcionar: %AppData%/yuzu/nand/system/save/8000000000000010/su/avators/profiles.dat 
	- La siguiente carpeta contiene archivos guardados para todos los juegos: %AppData%/yuzu/nand/user/save/0000000000000000


### Mario Kart Fix 
[How To Fix Stuck In Menu Mario Kart 8 Deluxe on yuzu Emulator - YouTube](https://www.youtube.com/watch?v=HYtq2yLfZBE)

### Parsec (trabajando en ello)
[Connect to Work or Games from Anywhere | Parsec](https://parsec.app/)
Parsec es una aplicación de control remoto para Windows, Linux y macOS. Con esta solución y otro input externo, se supone que se podría jugar a juegos de Switch en multiplayer "local". 


## Yuzu en Mac M1

