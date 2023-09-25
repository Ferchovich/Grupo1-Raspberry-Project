# Segunda entrega - Xorg - Grupo 1
# Índice 
1. [Introducción](#introducción)
2. [Instalación de Xorg](#instalacion-de-xorg)
3. [Reiniciar Raspberry Pi](#reiniciar-raspberry-pi)
4. [Conexion SSH](#conexion-ssh)
5. [Comandos desde la computadora externa](#comandos-desde-la-computadora-externa)
6. [Instalar y ejecutar aplicaciones graficas](#instalar-y-ejecutar-aplicaciones-graficas)
7. [Conclusión](#conclusión)

# Introducción:

Nosotros somos el grupo 1, conformado por: Ferreyra Octavio -Galleguillo Lucas - Hlavach Joaquin - Lucero Octavio. En este apartado veremos la instalación del servidor grafico Xorg. Luego de instalarla en la raspberry, correremos aplicaciones grafica por ssh sin que nuestro servidor realice las tareas de procesamiento del video.

El objetivo de esta entrega es empezar a familiarizarse con en el ordenador Raspberry Pi, instalando un servidor grafico y visualizar aplicaiones graficas estableciendo una conexión a través del protocolo SSH sin que nuestro servidor realice las tareas de procesamiento del video, sino que simplemente se envíen los datos remotamente y podamos generar las ventanas y los gráficos en el host cliente.

## Instalacion de Xorg


En el primer paso, prenderemos y conctaremos la raspberry. Luego una vez ya inciada, para instalar el Xorg, deberemos usar el siguiente comando:

```bash
sudo apt install Xorg
```

Al utilizar el comando "sudo" usara los permisos del superuser, seguido de un apt el cual es el gestor de paquetes predeterminado de Ubuntu y por ultimo el install acompañado del nombre del paquete que hace referencia al Xorg.

## Reiniciar Raspberry Pi

Después de la instalación, es recomendable reiniciar tu Raspberry Pi para asegurarte de que los cambios surtan efecto, con el siguiente comando:

```bash
sudo reboot
```

Al utilizar "sudo" usaremos los permisos del superuser, seguido del "reboot" que lo que hara sera reiniciar la Rasperberry Pi.

## Conexion SSH

Una vez ya reiniciada la Raspberry Pi, en la terminal, ejecutaremos el siguiente comando:

```Bash
hostname –I
```

Este comando nos dará la dirección IP del ordenador Raspberry.

## Comandos desde la Computadora externa

Dentro de la terminal, usaremos el siguiente comando:

```Bash
ssh -X Nombredeusuario@direccion-IP
```

El "ssh" sirve para realiza la conexion y el prametro -X sirve para habilitar el reenvio del X11. En el parámetro “Nombre de usuario”, introduce el nombre de tu propio perfil (En nuestro caso grupo1). Cuando te pregunte, introduce “yes” en la terminal para continuar. Por último, introduce la contraseña para que el usuario seleccionado se conecte a la línea de comandos del Raspberry.


## Instalar y ejecutar aplicaciones graficas

Ahora al estar conecatado con la Raspberry y una computadora externa, podremos instalar y ejecutar aplicaciones graficas(en nuestro caso instalamos y ejecutamos gedit):

```bash
sudo apt install gedit
```

Esto lo instalara en la Raspberry. Lo podremos ejecutar al programa a taves del siguiente comando:

```bash
gedit
```

Gedit se visualizara en la computadora externa pero las tareas de procesamiento se realizaran en la Raspberry. Para comprobrar su funcinamiento escribimos en el archivo, y presionamos el boton de "save".

Luego la terminla de la Raspberry Pi ponemos el siguinete comando para comprobar que se haya guardado:

```bash
ls
```

El comando "ls" sirve para listar los archivos en la carpeta que estas parado.

# Conclusión

En esta segunda entrega, pudimos instalar el servicio Xorg y ejecutar aplicaciones graficas a traves de lo aprendido en la primera entrega, osea, a traves de una conexion ssh, permitiendo que la Raspberry haga el procesamiento de dato, pero que en la computadora externa se muestre graficamente. Y asi nos vamos familiarizando mas con la Raspberry.