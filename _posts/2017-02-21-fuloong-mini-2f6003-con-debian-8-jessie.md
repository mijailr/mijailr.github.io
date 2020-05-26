---
layout: post
title: "Fuloong Mini 2F6003 con Debian 8 Jessie"
category: Hardware
date: 2017-02-21
languages: [Bash]
---

En el laboratorio de Hardware de la Comuna Tecnológica Don Luís Zambrano tenemos disponibles unas Fuloong Mini 2F6003, sin embargo vienen con una distribución modificada de Debian cuyos repositorios ya no están disponibles.

{% include images.html
            img="public/images/fuloong/fuloong-mini.jpg"
            title="Fuloong Mini"
            caption="Fuloong Mini 2F6003" %}

Como requeríamos de un mirror local de Debian Jessie, decidimos darles uso, por lo que empezamos a averiguar como instalarla.

Sabemos que el procesador de esta máquina es un MipsEL Loongson2F (Little Endian) y por algún lado en internet, por lo que descargamos directo la distribución para este procesador desde [Debian MIPSEL](http://ftp.nl.debian.org/debian/dists/jessie/main/installer-mipsel/current/images/loongson-2f/netboot/) sin embargo, al intentar instalar desde una memoria USB y colocando los archivos nos daba un Kernel Panic. Por lo que leyendo en foros y otros sitios en internet, nos dimos cuenta de que era necesario actualizar el BIOS del Fuloong PMON-2000, el cual logramos conseguir en su última version "Estable" [pmon-LM60xx-1.3.6a.bin](http://github.com/mijailr/bootloaders)

Y configuramos un TFTP de la siguiente manera:

    |--- fuloong/
         |--- jessie/
              |--- initrd.gz
              |--- vmlinuz-3.16.0-4-loongson-2f
         |--- pmon-LM60xx-1.3.6a.bin

Conectamos el Fuloong al teclado, red y monitor y presionamos `<SUPR>` para obtener el prompt de PMON (Suponiendo que el servidor TFTP está en 192.168.1.1):

{% gist db5794341b0cb00d53e0d158bd76e158 pmon_upgrade.txt %}

Luego hacer un reboot y esta vez notaremos que hay diferencias cuando arranca el sistema, presionamos nuevamente `<SUPR>` para ingresar al PMON:

{% gist db5794341b0cb00d53e0d158bd76e158 pmon_load_debian.txt %}

Y ya con esto inicia la instalación de Debian Jessie.
