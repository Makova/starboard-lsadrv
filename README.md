starboard-lsadrv
================

Versión del controlador del núcleo Hitachi StarBoard para Linux (LSaDrv)

Parcheada versión de LSaDrv con correcciones de 3.10 y para 64 bits.

Trabajo patrocinado por: [Talaria](http://www.talaria.fr/).

## Instalación
----------------------

Ejecutar en una terminmal los siguientes pasos:

## Instalar todas las librerías de 32 bits necesarios para ejecutar el software StarBoard en ordenadores de 64 bits:
```
sudo apt-get install libjpeg62:i386 libxtst6:i386 libusb-0.1-4:i386 libstdc++6:i386 libfreetype6:i386 libsm6:i386 libglib2.0-0:i386 libxrender1:i386 libfontconfig1:i386 libqtgui4:i386
```
## Descargar el driver actualizado e instalar el **.deb**:

`wget http://www.charmexdocs.com/int/software/SBS0962_LINUX.zip`

`unzip SBS0962_LINUX.zip`

`cd SBS0962_LINUX/StarBoardSoftware`

`sudo dpkg -i StarBoardSoftware_9.62_i586.deb`

## Esto debería de dar una advertencia:
`
 "None of the pre-compiled kernel modules seems to be compatible with your operating system."
`
> Al finalizar la instalación saldrá una advertencia diciendo que no puede montar el módulo, también puede salir otra advertencia del módulo coach y esto también se tendrá que solucionar instalando desde la siguiente ruta:

`sudo /usr/local/StarBoardSoftware/install.sh`

## Ahora compilar e instalar el driver arreglado:

`sudo apt-get install git`

`git clone https://github.com/mmuman/starboard-lsadrv.git`

`cd starboard-lsadrv/lsadrv`

`make`

```sudo cp `uname -r`/lsadrv.ko /lib/modules/`uname -r`/kernel/drivers/usb/input```

`sudo depmod`

`sudo modprobe lsadrv`

## Iniciar el servidor::

`sudo service starboardservice start`

## O reiniciar el sistema:

`sudo reboot`

Trabajos anteriores
--------------

* [ALT Linux patches](http://packages.altlinux.org/en/Sisyphus/srpms/kernel-modules-lsadrv-std-pae)
    * lsadrv-build-3.10.patch (fixes build but introduces a crash)
    * ioctl_and_mutex.patch (fixes for ioctl signatures and deprecated init_MUTEX)
