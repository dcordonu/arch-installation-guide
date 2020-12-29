# Microcodes

Los fabricantes de procesadores publican actualizaciones de estabilidad y seguridad para el microcódigo de sus CPUs, que proporcionan correcciones de errores que pueden ser críticas. Por ello, es altamente recomendable que los poseedores de microprocesadores de AMD o Intel instalen el paquete correspondiente.

Para procesadores Intel:

```bash
pacman -S intel-ucode
```

Para procesadores AMD:

```bash
pacman -S amd-ucode
```

El modelo exacto de la CPU se puede obtener con el comando `cat /proc/cpuinfo`.
