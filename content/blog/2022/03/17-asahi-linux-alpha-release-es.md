+++
date = "2022-03-18T23:50:00+00:00"
draft = false
title = "¡La primera versión alfa de Asahi Linux ya llegó!"
slug = "asahi-linux-alpha-release-es"
author = "marcan and zanez"
+++

¡Ha pasado mucho tiempo desde la última vez que actualizamos este blog! A decir verdad, queríamos más reportes acerca de nuestro progreso, pero siempre había "una cosa más"... Así que, decidimos arriesgarnos y publicar nuestra primera alfa pública de Asahi Linux.

Estamos muy emocionados de finalmente tomar este paso hacía adelante para darle acceso a todos de probar Linux en Apple Silicon. Esto solo es el comienzo, a partir de ahora el desarrollo será más rápido.

Recuerda que esta es una versión alfa muy prematura. Solamente está destinada para los desarrolladores y los usuarios experimentados, si decides instalarla, esperamos que estés dispuesto a ayudarnos reportando bugs de una forma detallada. Una vez aclarado esto, le damos la bienvenida a todos los que quieran probar esta versión - ten en cuenta que es posible que algunas cosas no funcionen. 

Esta edición trae consigo muchas características nuevas de compatibilidad para el futuro. Lo que esto significa es que los usuarios que la instalen ahora podrán obtener todas las nuevas mejoras que el proyecto pueda tener simplemente actualizando los paquetes - y no reinstalando el sistema operativo de nuevo.

¿Listo para darle una oportunidad? Asegúrate de actualizar tu sistema operativo macOS a la versión 12.3 u otra más reciente, luego abre una terminal en tu macOS y copia este comando: 

<div class="curlsh">
<pre>curl https://alx.sh | sh</pre>
</div>

Revisa los mensajes que se muestra el instalador, especialmente al final de su ejecución.

## Requisitos del sistema

* Máquinas M1, M1 Pro, o M1 Max (esto no incluye la Mac Studio)
* macOS 12.3 o alguna versión más reciente, estar registrado con permisos de administrador.
* Al menos 53GB de espacio libres en el sistema (Instalación de escritorio)
	* Necesitas 15GB para la instalación de Asahi Linux de escritorio, pero macOS por sí solo necesita mucho espacio libre en el disco para sus actualizaciones de sistema, el instalador espera que dejes 38GB libres de espacio para macOS para evitar que tengas problemas futuros al momento de actualizar. Por ejemplo, si tienes 60GB libres de espacio en tu disco, será posible encoger el sistema macOS hasta 22GB, libreando 22GB para la nueva instalación de Linux y dejando 38GB de espacio libre en la partición de macOS. Si quieres desactivar esta prueba, activa el modo experto cuando se te indique.  
* Una conexión a Internet funcional
	* El instalador va a descargar de 700MB a 4GB de información, depende del sistema operativo que elijas. 

Si es que usas "Time Machine" (programa de macOS para realizar copias de seguridad), te darás cuenta que es posible que no cuentes con suficiente espacio libre en tu disco. Esto ocurre debido a que tienes copias de seguridad creadas por Time Machine guardadas de forma local en tu disco. En este [link](https://appleinsider.com/articles/21/06/26/how-to-delete-time-machine-local-snapshots-in-macos) puedes aprender a eliminar estas copias de seguridad para liberar espacio para la instalación.

## Instalación

El instalador está diseñado para ser tan fácil de entender como sea posible. Veras una serie de mensajes en la terminal que te ayudarán a cambiar el tamaño de la partición de macOS (si es que es necesario) y a instalar tu nuevo sistema operativo. Se espera que los usuarios instalen Linux junto a macOS. El instalador no borrará o afectará tu instalación de macOS, sin tomar en cuenta el cambio de tamaño de la partición.

Una vez que se termine la primera parte de la instalación, vas a tener que reiniciar y entrar en el modo 1T (One True recoveryOS) para poder finalizar la instalación. Lee las instrucciones que el instalador te muestra con mucho cuidado. Reiniciar para intentar acceder a tu nuevo sistema operativo no funcionará hasta que no termines la instalación. Necesitas apagar tu máquina, después enciéndela de nuevo mientras presionas el botón de encender hasta que veas la pantalla de opciones de inicio que mostrará los discos de arranque, elige tu nuevo sistema operativo en el menú de boot y sigue las instrucciones que se te mostrarán.

El instalador proporciona las siguientes opciones:

### Asahi Linux Desktop

Una versión personalizada de Arch Linux ARM que viene con el entorno de escritorio completo de KDE Plasma con todos los paquetes básicos. Incluye una pantalla de personalización gráfica para que agregues las configuraciones que desees la primera vez que inicies sesión. No existe una contraseña root por defecto; usa el comando `sudo` para convertirte en root.

### Asahi Linux Minimal (Arch Linux ARM)

Un entorno estándar de Arch Linux ARM, con los menos paquetes posibles para hacer que funcione el proceso de inicio (boot) y el hardware en las máquinas Apple Silicon. ¡Los usuarios de Arch se sentirán como en casa! 

Inicia sesión como root/root or alarm/alarm. ¡No te olvides de cambiar ambas contraseñas! SSH está deshabilitado por defecto por razones de seguridad, así que tendrás que iniciarlo manualmente.

### Solo entorno UEFI (m1n1 + U-Boot + ESP)

Sin ninguna distribución, solamente un entorno de inicio UEFI. Con esto puedes utilizar cualquier instalador de sistema operativo desde una USB e instalar lo que quieras (siempre y cuando la distribución tenga soporte para estas máquinas).

## Lo que funciona

Todos los dispositivos M1, M1 Pro, y M1 Max son compatibles, exceptuando la Mac Studio.

* Wi-Fi
* USB2 (Puertos thunderbolt)
* USB3 (Puertos tipo A de la Mac Mini)
* Pantalla (no GPU)
* NVMe
* Lid switch
* Botón de encendido
* Pantalla incorporada (framebuffer only)
* Teclado/panel táctil incorporado
* Luz de fondo de la pantallas encendido/apagado
* Información de la batería / control de cargado
* RTC
* Ethernet (desktops)
* Lector de SD (M1 Pro/Max)
* Cambio de frecuencia del CPU

Solamente las máquinas M1 (no Pro/Max):

* Enchufe de audífonos (inconsistente)

Solo para la Mac Mini:

* Salida de HDMI 

Aún no funcionan, pero pronto se van a añadir:

* USB3
* Altavoces
* Controlador de pantalla (control de brillo en la luz de fondo, V-Sync, una correcta implementación de DPMS)

## Lo que no funciona

Todo lo demás, pero lo más destacable es:

* DisplayPort
* Thunderbolt
* HDMI en las MacBooks
* Bluetooth
* Aceleración de GPU
* Aceleración de video codec
* Neural Engine
* Manejo de energía de CPU en modo reposo (CPU deep idle) 
* Modo reposo
* Cámara
* Touch Bar

Nota: en la MacBook Pro de 13 pulgadas, puedes usar Fn + teclas de la fila númerica (1-9, 0, y los siguientes dos) como F1..F12 en lugar de la Touch Bar.

## Bugs conocidos

* Si el Wi-Fi no funciona, intenta encendiéndolo y apagándolo en el menú de administración de red.
* Si el puerto de audífonos no funciona o solo uno de los canales funciona, intenta reiniciar tu computadora.

## Aplicaciones que no funcionan

El kernel de Asahi Linux está compilado para usar páginas de 16K. Esto ayuda al rendimiento, y también es un requisito en nuestro kernel para que funcione de la manera correcta con los IOMMUs del M1. Desafortunadamente existe software de Linux que tiene [problemas cuando se ejecuta en páginas de 16K](https://github.com/AsahiLinux/docs/wiki/Software-known-to-have-issues-with-16k-page-size). Los más conocidos son:

* Chromium (se necesita un voluntario para arreglarlo)
* Emacs (parche listo, pero aún no se ha publicado)
* Cualquier software que use jemalloc (p. ej Rust cuando se instala a través de los repositorios de Arch)
* Cualquier software que use libunwind (ya se tiene un parche, pero aún no se ha publicado)

Afortunadamente esta publicación sobre Asahi Linux ayudará a motivar a otros proyectos para que se le de una solución a los errores que existen y para darle el apoyo requerido a todos los tamaños de las páginas de ARM64 (64K, 16K y 4K). 16K da una mejora muy importante de rendimiento hasta en un 20%.

Hay una categoría de software que posiblemente nunca va a dar soporte a las páginas de tamaño 16K: algunos emuladores y capas de compatibilidad incluyendo [FEX](https://github.com/FEX-Emu/FEX). Android también es afectado, en caso de que alguien quiera ejecutarlo de manera nativa. Para los usuarios de estas herramientas, vamos a lanzar kernels con páginas de tamaño 4K, una vez que los cambios necesarios para que esto sea posible estén listas para utilizar.

## Más información

Visita nuestra documentación en [docs wiki](https://github.com/AsahiLinux/docs/wiki) para más información. Nos encantaría tener a más personas trabajando en la documentación, siéntete libre de aportar. Ya que nuestro proyecto se ha estado desarrollando muy rápido debes de tener en cuentaque algunas partes de la documentación podrían estar desactualizadas.

Te recomendamos que leas:
* ["When will Asahi Linux be done?"](https://github.com/AsahiLinux/docs/wiki/%22When-will-Asahi-Linux-be-done%3F%22)
* [Introduction to Apple Silicon](https://github.com/AsahiLinux/docs/wiki/Introduction-to-Apple-Silicon)
* [Open OS Ecosystem on Apple Silicon Macs](https://github.com/AsahiLinux/docs/wiki/Open-OS-Ecosystem-on-Apple-Silicon-Macs)
* [m1n1:User Guide](https://github.com/AsahiLinux/docs/wiki/m1n1%3AUser-Guide)

Si eres un desarrollador o sabes de ingeniería inversa, aquí tenemos algo para ti:
* [SW:Hypervisor](https://github.com/AsahiLinux/docs/wiki/SW:Hypervisor)

Y si estás muy aburrido:
* [Trivia](https://github.com/AsahiLinux/docs/wiki/Trivia)

## FAQ

### ¡Quiero donar!

¡Gracias! Asahi Linux está siendo desarrollado por un grupo de voluntarios, todos bajo el liderazgo de marcan. Puedes apoyarlo directamente a través de [Patreon](https://patreon.com/marcan) y [GitHub Sponsors](https://github.com/sponsors/marcan). Nada de esto sería posible sin su apoyo. Las donaciones le permiten dedicar una gran parte de su tiempo al proyecto y también a comprar hardware para realizar pruebas.

Martin Povišer está trabajando en añadir soporte de audio para Asahi Linux, él también cuenta con una página de [GitHub Sponsors](https://github.com/sponsors/povik). ¡Por favor apoya sus esfuerzos para que pueda hacer que las máquinas de Apple Silicon se conviertan en la plataforma con mejor soporte para audio de Linux!

### ¿Puedo hacer dual-boot con macOS y Linux?

¡Sí De hecho, esperamos que hagas esto, y el instalador no tiene la función de reemplazar macOS en este momento. Esto se debe a que todavía no tenemos un mecanismo para actualizar el firmware del sistema desde Linux, y hasta que que no logremos agregar esta función es mejor que tengas la instalación de macOS. 

Puedes tener tantas instalaciones de macOS y Linux como desees, todas deberían funcionar y será posible seleccionarlas desde el menú de arranque de Apple. Cada instalación de Linux se comporta como su propio sistema operativo y no debería interferir con los otros.

Ten en cuenta que tener una instalación de macOS en tu sistema significa que vas a perder alrededor de 70GB de espacio en tu disco (todo esto solamente para poder recibir actualizaciones, ya que el software que se utiliza para actualizar macOS es bastante ineficiente). En un futuro se espera que se cree un mecanismo para permitir tener actualizaciones de firmware desde Linux y una mejor integración, cuando esto sea una realidad nos sentiremos cómodos con la recomendación de tener solamente Linux como un único sistema operativo en estos dispositivos. Por supuesto, que esto solamente es recomendado si de verdad deseas borrar la macOS después de instalar Linux. 

### ¿Cómo cambio entre Linux y macOS?

Entra al menú de arranque manteniendo presionado el botón de encendido, después elige el sistema operativo que deseas inicializar. Lo puedes seleccionar mientras mantienes presionada la tecla Option para hacer seleccionarlo como el sistema operativo por defecto.

### ¡Ayuda, estoy en un bucle de boot!

No leíste las instrucciones, ¿verdad? :-)

Necesitas apagar en su totalidad la máquina, espera 15 segundos, después presiona y mantelo presionado hasta que la opción "Cargando opciones de inicio" aparezca en la pantalla. Después selecciona el nuevo sistema operativo que acabas de instalar, y sigue las instrucciones.

Si mantener presionado el botón de encendido hace que el dispositivo continúe reiniciando en lugar de mostrar el menú de arranque, entonces significa que te has encontrado con un error muy poco común. Esto no debería ocurrir a día de hoy, pero en caso de que ocurra, no te preocupes. Tu dispositivo sigue funcionando correctamente. Tienes que esperar a que el logo de Apple desaparezca al final del bucle, después debes de contar 3 segundos y rápidamente presionar, soltar y luego mantener presionado el botón de encendido. Esto debería hacer que en la pantalla se muestre el menú de arranque de nuevo. Selecciona macOS como tu opción de arranque por defecto y eso debería solucionar el error. No creemos que nadie se vuelve a encontrar con este error de nuevo, pero un usuario tuvo este error en una versión muy temprana de la pre-alpha del instalador, después de que ocurriera un error relacionado a la red. Hemos cambiado el código para evitar que este error vuelva a ocurrir, pero nos gustaría mencionar la forma de arreglar por si acaso.

### ¿Lo puedo instalar sin Internet?

El instalador está diseñado para ser usado con conexión a Internet. Lo puedes utilizar sin necesita de contar con red si es que cuentas con una copia de todos los archivos que necesitas, hasta el momento no contamos con una forma sencilla para hacer que esto funcione con los usuarios menos experimentados. Por favor haznos saber si este es tu caso para que nuestro equipo pueda agregar esta funcionalidad en el futuro.

### ¿Lo puedo instalar a un usb/disco externo?

Las máquinas Apple Silicon no pueden arrancar ningún sistema desde dispositivos de almacenamiento externos. Puede parecer que eliges un dispositivo externo al volumen de macOS, pero el funcionamiento de los componentes de arranque están siendo copiados al disco interno para hacer que funcione. No está totalmente claro si este mecanismo podría ser utilizado por sistemas operativos de terceros por razones técnicas.

En lugar de eso, nosotros recomendamos el uso de la opción *UEFI environment only* en la opción del instalador solo para instalar solamente lo necesario en a tu disco interno. Esto solo requiere alrededor de 3GB de espacio disponible, y después va a iniciar de manera automática desde cualquier USB conectado con el bootloader UEFI. Nota: instalar la imagen Asahi Linux desktop a un dispositivo USB de manera automática aún no tiene soporte, aunque si te animas a hacerlo no es muy difícil de hacerlo manualmente :-)

### ¿Cómo lo desinstalo?

El instalador no tiene una opción para desinstalarlo por ahora, pero todo lo que tienes que hacer es eliminar la partición que se crearon usando el software que desees, p. ej `diskutil`. Puedes cambiar el tamaño de la partición de macOS de nuevo a su tamaño original si lo deseas.

Si haces más de una instalación y/o desinstalaciones de los sistemas operativos, podrás darte cuenta que algunas partes del proceso de instalación pueden tomar más tiempo de lo usual. Esto se debe a que se dejan diferentes archivos de las políticas de arranque. Contamos con un [script](https://github.com/AsahiLinux/asahi-installer/blob/main/tools/cleanbp.sh) que te ayudará a limpiar esos archivos. Úsalo con precaución; necesitas ejecutarlo desde recoveryOS o con SIP deshabilitado.

### ¿Qué pasa con el uso del uso de almacenamiento?

Cada sistema operativo necesita alrededor de 3GB de espacio de disco, además del espacio requerido por el sistema de archivos del sistema operativo root/boot. 2.5GB son usados por la partición "stub" de macOS, que incluye componentes críticos como el bootloader de Apple y firmware, y una copia completa de la copia de seguridad de la imagen de macOS. Esto se requiere por el diseño de estas plataformas. Reservaremos 2.5GB (aunque la imagen de recuperación pesa solamente alrededor de 1GB) para poder tener actualizaciones y evitar problemas causados por la gran cantidad de sistema de archivos APFS.    

### ¿Ya hay aceleración de GPU?

¡Nop! Aún estamos trabajando en eso y estamos progresando en ese aspecto en privado. Mientras tanto, el renderizado de software es bastante bueno gracias a la capacidad de rendimiento con la que cuenta la familia de M1. La imagen de Asahi Linux Desktop configura una sesión de X.Org, con transparencia y sombras, y no se siente lenta. Muchas personas ya están usando esta distribución como su sistema operativo del día al día.

Una vez que la aceleración de GPU esté disponible, los usuarios que ya cuentan con Asahi Linux podrán obtener sus ventajas solamente actualizando sus paquetes.

### ¿El audio funciona?

El puerto de audífonos funciona en los modelos de M1 (M1 Pro y los modelos Max tienen nuevos codecs que aún no cuentan con compatibilidad). Ya tenemos drivers funcionales para los speakers, pero existen problemas de seguridad (no queremos destrozar tus speakers) y calidad (queremos que suenen mejor que en macOS) en los que aún necesitamos trabajar, ya que el soporte automático de los speakers DSP todavía está en una etapa muy temprana en el ecosistema de audio de Linux. Por lo que, no todavía no hemos habilitado esta característica para los usuarios comunes. Cuando se complete esta implementación, una simple actualización de paquetes es lo único que será necesario para contar con el soporte para audio.

### ¿El modo reposo funciona?

No del todo. s2idle funciona, lo que nos permite poner los dispositivos USB/NVMe en modo reposo, pero el driver de Wi-Fi todavía necesita trabajo para que soporte en su totalidad el modo reposo en estas máquinas, y el driver de PCI también necesita algunos ajustes. Cuando se completen estos retoques vamos a habilitar el soporte s2idle en nuestras kernels. 

Posteriormente el sistema completo para modo reposo será habilitado con una simple actualización de sistemas.

### ¡El notch!

Esa no es la pregunta, pero asumiendo que quieres saber lo que estamos haciendo respecto al notch: en la M1 Pro y Max, Asahi Linux recorta la pantalla para que el notch esté "escondido", y el entono de escritorio ve una pantalla rectángular de 16:10. Vamos a continuar con esta forma de trabajo por ahora, pero en el futuro vamos a permitir el uso de diferentes usos de pantalla que inclutan el notch, para que el entorno de escritorio que implementen formas de evitar el notch puedan hacer controlar el estado de la pantalla. 

### ¿Asahi es solamente Arch Linux en ARM?

¡Básicamente! Mucho de nuestro trabajo se encuentra en el kernel y algunos paquetes esenciales, y nosotros dependemos en la excelente compatibilidad de Linux con los sistemas ARM64. Las imágenes de Asahi Linux están basadas de Arch Linux ARM y nosotros solamente añadimos unos [cuantos paquetes](https://cdn.asahilinux.org/aarch64/asahi/). Puedes convertir Arch Linux ARM en Asahi Linux solamente añadiendo o quitando este repositorio y todos los paquetes relevantes, aunque una kernel básica de Arch Linux ARM no va a arrancar en esta máquinas por el momento.

Si te interesa, [estos](https://github.com/AsahiLinux/asahi-alarm-builder/) son los scripts que usamos para compilar las imágenes de Asahi Linux tomando como base el tarball básico de Arch Linux ARM. También patrocinamos un espejo de ALARM como parte de nuestro proyecto (jp.mirror.archlinuxarm.org).

Como parte de nuestro proyecto, aportamos fixes y mejores a un número de diferentes paquetes, por ejemplo, soporte para Mesa por Apple GPU ya está en camino (está siendo probado en macOS), también hicimos un fork de xkeyboard-config donde vamos a añadir ajustes para distribución de teclado para darle un mejor soporte a las Macs.

### ¿Puedo instalar otras distros de Linux?

¡Por supuesto! Nuestro objetivo es trabajar con otros desarrolladores para traer soporte total para tus distros favoritas a estas máquinas.

Una vez dicho eso, en este momento ninguna otra distribución de Linux da una imagen de instalación oficial para Apple Silicon, y las imágenes predeterminadas de ARM64 no van a funcionar hasta que les des los cambios necesarios al kernel; por lo que, instalar otra distro es más que nada un proceso manual. Algunos usuarios tienen [instrucciones de instalación](https://github.com/AsahiLinux/docs/wiki/SW:Alternative-Distros) para otras distros, en el futuro vamos a añadir algunas de las opciones al instalador de Asahi Linux. Recuerda que estas instrucciones son proporcionadas por usuarios y no podemos dar apoyo total a tales proyectos.

Si eres un desarrollador de alguna distribución y estás interesado en soportar la dispositivos Apple Silicon, por favor contáctanos. Nos encantaría trabajar contigo. Te puedes poner en contacto con nosotros a través de nuestros [canales de IRC](/community-es/).

También nos encantaría escuchar las opiniones de distribuciones que no están basadas en Linux. Snapshots de OpenBSD ya se pueden instalar después de configurar el entorno de arranque UEFI, revisa esta [página](https://www.openbsd.org/arm64.html)  para más información.

### ¿Voy a arruinar mi máquina? ¿Qué tan seguro es?

Aspiramos a hacer el instalador tan seguro como sea posible. Todo las operaciones que se necesitan hacer en los discos se realizan por sí solas usando herramientas nativas de macOS (`diskutil`) y el instalador no es realmente peligroso.

De hecho, no hemos visto ninguna pérdida de datos o alguna máquina que haya sido dañada durante toda la etapa de desarrollo de Asahi Linux, además de los errores obvios ("Por accidente borré todo mi disco"). Las máquinas Apple Silicon son casi a prueba de errores: puedes iniciar en [modo recuperación](https://support.apple.com/guide/apple-configurator-2/revive-or-restore-a-mac-with-apple-silicon-apdd5f3c75ad/mac) y para "recuperarlas" usando otra máquina conectada a través de un cable USB. Para los que no cuentan con otra máquina con macOS para utilizar, tenemos estas [herramientas de código abierto](https://github.com/libimobiledevice/idevicerestore) que funcionan en Windows y también en Linux.

Como con todo proyecto de código abierto, especialmente en las versiones alfa como la que tenemos, no podemos hacer ninguna promesa. Podrías perder tus datos. Es probable que nunca ocurra, pero si es que llegara a pasar, no nos culpes a nosotros.

Mientras que el instalador intenta no dejarse hacer ninguna operación que sea peligrosa para tu máquina, obviamente no hay nada que te impida de borrar todos los datos de tu sistema macOS una vez que inicies en Linux; tú eres, por supuesto, en total control de tu propia computadora. Para aquellos que quieran usar herramientas para particionado y manejo de discos, deberías evitar modificar las primeras y últimas particiones del disco NVMe interno. Si modificas esto podrías dejar tu sistema operativo inutilizado y necesitarías una recuperación DFU. En particular, si no usas las imágenes de Asahi Linux y usas el instalador de terceros usando el modo UEFI, nunca escojas "usar el disco entero" cuando lo estés instalando.

### ¿Qué son esas aterradoras advertencias de seguridad? 

Durante la segunda etapa de la instalación después del primer reinicio, el instalador necesita poner tu nuevo sistema operativo en modo "Seguridad Permisiva" para poder arrancar kernels operativos de terceros. Esto solo afecta al sistema operativo que has instalado, tu instalación de macOS no es afectada de ninguna forma. A diferencia las Mac con CPUs de Intel y plataformas como Android, las Macs de Apple Silicon mantienen un estado de seguridad para cada sistema operativo instalado. Eso significa que no existe ningún efecto en tu macOS. Puedes continuar usando todas las características más altas de seguridad o DRM, como FileVault, aplicaciones de iOS, Apple Pay, Netflix in 4K, etc. 

Si estás preocupado acerca de las integridad de la información/confidencialidad en tu volumen de macOS, recomendamos FileVault. Esto hará que los datos de tu macOS sea totalmente inaccesible a otros sistemas operativos sin tener que iniciar sesión con tus credenciales de macOS.

### ¿Necesitas llamar a Apple para poder instalar Asahi Linux?

Todos los sistemas operativos en las máquinas de Apple Silicon, necesitan ciertos componentes de Apple. Ya que nosotros no las podemos distribuir por nuestra cuenta, el instalador va descargarlos directamente de los servidores de Apple. En el futuro agregaremos una opción para permitir el uso de instalación sin conexión a Internet. 

Durante el inicio de la instalación (cuando se haga el volumen la opción predeterminada de arranque), hay un proceso que se ejecuta sin tu conocimiento que está relacionado a autenticar la nueva instalación del sistema operativo con la ayuda de los servidores de Apple (desde su punto de vista, ellos verán como si estuvieras verificando tu instalación normal de macOS, no sabrán que estás instalando Linux).  Esto es parte del modo "Seguridad completa", que se usa en Asahi Linux antes de que la instalación se cambie a modo "Seguridad permisiva". Si esto te preocupa puedes utilizar el instalador de Asahi Linux desde el modo de recuperación (mantén el botón de encendido -> Opciones -> Utilidades -> menú -> Terminal). Si haces esto se activará un método alterno que se llama "Seguridad reducida", eliminando el requisito de número de teléfono, número que el instalador usará de manera automática. Recuerda que aun así los componentes se tendrán que descargar de los servidores de Apple (pero eso no requiere ningún identificador único que esté en la máquina, es una simple descarga HTTPS).

### ¿Tienes soporte para Secure Boot/Encriptación completa de disco/etc?

Las máquinas de Apple Silicon son unas de las pocas plataformas de propósito general que te permiten instalar un sistema operativo personalizado mientras mantienes una cadena segura de arranque (boot). Instalar el bootloader requiere acceso físico a la máquina y también a tus credenciales de propietario (esta es la razón por la que necesitamos que mantengas presionado el botón de encendido para iniciar el arranque al final del proceso de instalación). Por lo tanto, estamos interesados en seguir apoyando esta cadena de arranque en Linux para que se tenga una mayor seguridad y sea convierta en un sistema más resistente contra atacantes, tomando ventaja de SEP de Apple, Touch ID, y mucho más, mientras que aún se le da la oportunidad al usuario final tener total control de su sistema operativo. Estamos diseñando el proceso de arranque Asahi Linux en una forma en la que se permita usar estas opciones en un futuro, pero algunas pequeñas partes de este trabajo aún no están listas, así que por favor ponte al tanto. 

Mientras tanto, recomendamos que los usuarios que estén preocupados por la seguridad física activen FileVault in macOS. Esto añadirá un requisito de inicio de sesión para entrar en modo de recuperación, lo que evitará que un atacante con acceso físico pueda vulnerar tu sistema operativo en alguna forma. m1n1 aún no cuenta con un modo de arranque seguro, pero tampoco tiene ningún accesos local a las características mientras sea instalado de la forma apropiada. Asegurar U-Boot y GRUB y el resto de Linux es un ejercicio que se le dejará al lector.

El instalador de Asahi Linux no tiene la opción de configurar FDE para ti. Aunque, puedes usar la opción de solo UEFI y agregar tu propia configuración tradicional de LUKS de forma manual. Se espera que los usuarios interesados en estas tecnologías hagan sus propias configuraciones al menos por ahora.

### Tengo otra pregunta

¡Pásate por nuestro canal de IRC y haz tus preguntas! Puedes visitarnos en #asahi en OFTC. Revisa nuestra [página de comunidad](/community-es/) para más detalles.