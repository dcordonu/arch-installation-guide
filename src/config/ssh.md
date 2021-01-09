# SSH

SSH (Secure SHell) es un protocolo cuya función principal es acceder a un servidor remoto mediante un canal seguro en el que toda la información está cifrada. Permite:

* Copiar datos de forma segura con el comando `rsync`.
* Simular sesiones FTP cifradas.
* Gestionar claves RSA para evitar introducir contraseñas al conectar a los equipos.
* Redirigir tráfico de ventanas X para ejecutar programas gráficos remotamente.

El paquete `openssh` implementa el protocolo y provee el comando `ssh`. Por ejemplo, para conectar con el servidor en la IP 10.0.0.50 con las credenciales del usuario *diego*:

```bash
ssh diego@10.0.0.50
```

>Es necesario que el servidor al que se conecta tenga instalado y en ejecución un servicio SSH.

## Configurar clave RSA

Para conectar mediante SSH es necesario introducir la contraseña del usuario con cuya cuenta se vaya a acceder. Sin embargo, para evitarlo es posible configurar una clave RSA en la máquina *guest* e instalar la clave pública en cada uno de los servidores a los que se quiere conectar.

La clave se genera con el comando `ssh-keygen`:

```bash
ssh-keygen -t rsa
ssh-add ~/.ssh/id_rsa
```
