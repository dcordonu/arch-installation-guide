# Disco RAM inicial

Es necesario reconstruir el script de arranque inicial para que sea capaz de leer las particiones LVM y de desencriptarlas, en caso de suministrarle la contraseña correcta.

Para ello basta con modificar el fichero de configuración `/etc/mkinitcpio.conf` que es leído cada vez que se regenera ese script. En concreto, a la línea

```bash
HOOKS = (base udev autodetect modconf block filesystems keyboard fsck)
```

hay que añadirle las opciones `encrypt` y `lvm2` después de `block`:

```bash
HOOKS = (base udev autodetect modconf block encrypt lvm2 filesystems keyboard fsck)
```

Sin embargo, para que el *hook* de LVM pueda funcionar y el sistema sea capaz de leer las particiones al inicio, hay que instalar el paquete `lvm2` puesto que no viene incluido en el sistema base:

```bash
pacman -Sy lvm2 --noconfirm
```

Este comando incluye una imagen del kernel que se quiere que cargue al inicio y ha de coincidir con el que se ha instalado usando `pacstrap`, en este caso:

```bash
mkinitcpio -p linux-zen
```
