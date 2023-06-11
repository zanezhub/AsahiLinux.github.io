---
title: About
date:  "2021-01-05T20:00:00+09:00"
draft: false
---

# Acerca de Asahi Linux

Asahi Linux es un proyecto y una comunidad que tiene como objetivo importar Linux a las nuevas Macs Apple Silicon, comenzando por la Mac Mini M1 del 2020, la MacBook Air, y la MacBook Pro. 

Nuestro objetivo no es solamente lograr que Linux pueda usarse en estas máquinas sino también mejorarlo hasta el punto que se pueda usar como un sistema operativo totalmente funcional para su uso diario. Hacer esto requiere una cantidad muy grande de trabajo, debido a que la Apple Silicon carece de documentación. Estamos principalmente enfocados en aplicar ingeniería inversa a la arquitectura que utiliza la GPU de Apple para poder desarrollar un driver de código abierto para la misma.

Asahi Linux está construida por una comunidad de desarrolladores apasionados por el código libre y abierto.

## El nombre

Asahi significa "el sol naciente" en Japonés, y también es el nombre de un cultivo de manzana .旭りんご (*asahi ringo*) es lo que conocemos como la manzana McIntosh, el tipo de manzana que le dio a la Mac su nombre.

## El logo

<img src="/img/AsahiLinux_logomark.svg" alt="Asahi Linux logo" width="100">

La página web y el logo de Asahi Linux fueron diseñados por [soundflora*](https://soundflora.tokyo). Puedes encontrar el logo [aquí](https://github.com/AsahiLinux/artwork/tree/main/logos). 

# FAQ

## ¿Cuáles son los dispositivos compatibles?

Todas las Macs de Apple con el chip M1, y también las generaciones futuras según lo permita el tiempo de desarrollo. El primer dispositivo será la Mac Mini con el chip M1. 

## ¿Asahi es una distribución de Linux?

Asahi Linux es proyecto que tiene en mente desarrollar compatibilidad para las nuevas Macs. Eventualmente lanzaremos un remix de [Arch Linux ARM](https://archlinuxarm.org/), listo para su instalación para los usuarios finales, como una distribución con el mismo nombre. La mayor parte del trabajo está en la darle soporte al hardware, a los drivers, y a las herramientas. La distribución se convertirá en un paquete fácil y cómodo de instalar por los usuarios para darles acceso a las versiones más recientes del software que desarrollamos.

Esperamos que el apoyo sea exportado a otras distribuciones. Los usuarios experimentos siempre serán libres para usar la distribución que sea de su gusto y también para agregar los parches/software necesario antes de que esto ocurra.

## ¿Apple lo permite? ¿No se necesita un jailbreak?

Apple te permite utilizar kernels personalizados en las Macs Apple Silicon sin necesidad un jailbreak. Esto no es ningún tipo de error, es una característica que Apple añadió a estos dispositivos. Eso significa que a diferencia de los dispositivos iOS, Apple no pretende prohibirte de elegir un sistema operativo diferente (aunque probablemente no tienen pensando en ayudar con el desarrollo necesario para lograrlo).

## ¿Es legal?

Mientras no se tome código de macOS para darle soporte a Linux, el resultado es completamente libre de ser distribuido por los usuarios para su uso, como si no fuese un trabajo derivado de macOS. Por favor revisa nuestras [políticas de Derechos de Autor e Ingeniería Inversa](/copyright) para más información.

## ¿Cómo se va a distribuir?

Todo el desarrollo toma lugar en nuestro [GitHub](https://github.com/AsahiLinux). Todas las contribuciones se hacen con la intención de ser compartidas a su respectiva categoría de proyectos (empezando con el kernel de Linux) y ser compartidas tan pronto como sea posible. El código contará con una dos licencias, GPL como la licencia para compartir a otros proyectos y MIT como una licencia permisiva; esto se hace con la finalidad de que el trabajo pueda ser utilizado en otros sistemas operativos de ser posible.

## ¿Esto convertirá a las Apple Silicon Macs en una plataforma completamente abierta?

No, Apple todavía tiene el control sobre el proceso de inicialización (boot) y, por ejemplo, el firmware que corre en el *Secure Enclave Processor*. Aunque ningún dispositivo moderno es "completamente abierto" - hoy en día no existe ninguna computadora con software y hardware abierto (por mucho que las compañías lo intenten aparentar). Lo que cambia es el lugar en el que dibujas la línea entre los componentes "abiertos" y "cerrados". La línea que existe en las Macs Apple Silicon es cuando se cambia la imagen del kernel que se utiliza, mientras que el firmware permanece cerrado - lo que es muy similar a las PCs comunes, donde el firmware UEFI inicia el sistema operativo, mientras que el ME/PSP firmware permanece cerrado. Es un hecho que las plataformas convencionales de x86 son más intrusivas porque su firmware propietario tiene permitido robar el CPU del sistema operativo en cualquier momento a través de interrupciones SMM, mientras que en las Macs Apple Silicon no es el caso. Esto tiene un gran impacto en el rendimiento y estabilidad, no es simplemente un problema filosófico.  

## ¿Quién está detrás de Asahi Linux?

Asahi Linux es una comunidad y todos están invitados a colaborar. Si estás interesado revisar nuestra [página de contribución](/contribute-es). Los contribuidores más destacados son:

* [Hector Martin "marcan"](https://github.com/marcan), el líder el proyecto. marcan es alguien muy experimento en la ingeniería inversa y también un desarrollador con más de 15 años de experiencia en *portear* Linux y en ejecutar software no oficial en sistemas sin documentación y/o sistemas cerrados. Este es su proyecto más ambicioso hasta la fecha, y este proyecto está siendo financiado gracias a las [donaciones y patrocinio de la comunidad](/support-es). Sus proyectos anteriores incluyen PS4 Linux

*  His previous projects include [PS4 Linux](https://github.com/fail0verflow/ps4-linux), a Linux port to the proprietary hardware found on the PS4, capable of full 3D acceleration using OpenGL and Vulkan (radeon/amdgpu drivers); [AsbestOS](https://github.com/marcan/asbestos), a PS3 Linux bootloader for GameOS mode, and associated kernel patches to make Linux work on the PS3 Slim; and numerous contributions to the [Wii Homebrew ecosystem](https://wiibrew.org/), including being part of the team that developed [The Homebrew Channel](https://wiibrew.org/wiki/Homebrew_Channel) and [BootMii](https://wiibrew.org/wiki/BootMii), documenting much of the hardware, and contributing to open homebrew SDK tooling.

* [Alyssa Rosenzweig](https://rosenzweig.io/), the Asahi GPU lead. Alyssa is a Linux graphics hacker known for her work on reverse-engineering the Arm Mali GPUs to build the free Panfrost driver. She is an upstream Mesa3D developer, maintaining both the Panfrost and Asahi Mesa drivers.

* [Asahi Lina](https://github.com/asahilina), our GPU kernel sourceress. Lina joined the team to reverse engineer the M1 GPU kernel interface, and found herself writing the world's first Rust Linux GPU kernel driver. When she's not working on the Asahi DRM kernel driver, she sometimes hacks on open source VTuber tooling and infrastructure.

* [Dougall Johnson "dougallj"](https://github.com/dougallj), instruction set architecture extraordinaire. Dougall reverse-engineered much of the instruction set of the Apple GPU and has analyzed the timing of the Apple M1's CPU cores to infer microarchitectural details.

* [Sven Peter](https://github.com/svenpeter42). Sven has worked tirelessly on upstream Linux support for Apple's Device Address Resolution Table (DART) required for USB, PCIe, Ethernet, and Wi-Fi. He also added USB gadget support to m1n1, and is now working on DisplayPort and Thunderbolt support.

* [Mark Kettenis](https://github.com/kettenis), OpenBSD developer. Mark has written m1n1 and U-Boot drivers for the Apple M1 core peripherals, including the bringup needed for PCIe and NVMe (ANS). Mark has also written OpenBSD drivers for the Apple M1 as a parallel effort to the Linux port.

* [Martin Povišer](https://github.com/povik/), who is leading our audio kernel driver effort. Martin wrote and is upstreaming the Apple-specific SoC audio drivers as well as drivers for Apple-proprietary codecs and codec variants.

* [Janne Grunau](https://github.com/jannau), who implemented touchpad/keyboard support for the M1 series and is now maintaining the display controller (DCP) driver. He has also been involved in countless other bits and pieces, including device tree cleanup and submission.
