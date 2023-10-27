

# Primer entrega - Raspberry y SSH - Grupo 1
# Índice 
1. [Introducción](#introducción)
2. [Instalación del Sistema Operativo](#instalacion-del-sistema-operativo)
3. [Conexion de la Raspberry](#conexion-de-la-Raspberry)
4. [Configuracion de la Raspberry Pi](#configuracion-de-la-Raspberry-Pi)
5. [Conexion SSH al raspberry Pi](#conexion-SSH-al-raspberry-Pi)
6. [Comandos desde la Computadora externa](#comandos-desde-la-Computadora-externa)
7. [Conclusión](#conclusión)

# Introducción:

Nosotros somos el grupo 1, conformado por: Ferreyra Octavio -Galleguillo Lucas - Hlavach Joaquin - Lucero Octavio. En este apartado veremos la instalación de un servicio SSH en una Raspberry PI, es necesario tener una placa Raspberry. Instalaremos el sistema operativo correspondiente en la Raspberry Pi y generaremos una conexion SSH entre dos computadoras.

El objetivo de esta entrega es establecer las bases para el trabajo en el ordenador Raspberry Pi, instalando un sistema operativo y estableciendo una conexión a través del protocolo SSH con otras computadoras en el mismo sistema LAN.

## Instalacion del Sistema Operativo


En el primer paso, introucimos la tarjeta de memoria MicroSD a una computadora y usaremos el programa Raspberry Pi Imager.

Para instalar el Raspberry Pi imager, deberemos usar el siguiente comando:
```bash
sudo apt install rpi-imager
```

Al utilizar el comando "sudo" usara los permisos del superuser, seguido de un apt el cual es el gestor de paquetes predeterminado de Ubuntu y por ultimo el install acompañado del nombre del paquete que hace referencia al Raspberry Imager.

Luego, instalaremos el sistema operativo Raspberry Pi OS Lite (x64). Seleccionamos este sistema operativo sin escritorio ya que se utilizara unicamente la terminal. Con este paso ya podremos comenzar a trabajar en la interfaz.

## Conexion de la Raspberry

Retiramos la memoria MicroSD de la computadora y la conectamos al Raspberry. Conectamos los perifericos(monitor y teclado) y conectamos una red LAN, acompañado de un conector micro-USB para alimentar la Raspberry. Creamos un usuario. Colocamos un nombre de usuario y contraseña, para logearnos cada vez que utilizemos la Raspberry. Al iniciar sesión, se mostrara la terminal.

## Configuracion de la Raspberry Pi

Una vez en la terminal, habilitaremos el acceso SSH desde la misma. Para ello, configuraremos mediante el siguiente comando:

```bash
sudo raspi-config
```

Cuando ejecutemos el comando, aparecera un menu de herraimientas en el cual seleccionaremos el punto 6(Advances Options) y luego A4("SSH").La herramienta te preguntará si deseas **activar el servidor SSH**, lo que deberás confirmar antes de cerrar los ajustes con “Finalizar”.

Como alternativa a _raspi-config_, puedes utilizar la herramienta de línea de comandos _systemctl_ para configurar en tu Raspberry Pi el SSH. Simplemente introduce los dos comandos siguientes en la terminal:

```Bash
sudo systemctl enable ssh
sudo sta start ssh
```

## Conexion SSH al raspberry Pi

En la terminal del Raspberry Pi, ejecutaremos el siguiente comando:

```Bash
hostname –I
```

Este comando nos dará la dirección IP del ordenador Raspberry.

## Comandos desde la Computadora externa

Dentro de la terminal, usaremos el siguiente comando:

```Bash
ssh Nombredeusuario@direccion-IP
```

En el parámetro “Nombre de usuario”, introduce el nombre de tu propio perfil (En nuestro caso grupo1). Cuando te pregunte, introduce “yes” en la terminal para continuar. Por último, introduce la contraseña para que el usuario seleccionado se conecte a la línea de comandos del Raspberry.

Ahora al estar conecatado con la Raspberry y una computadora externa, puede instalar paquetes desde la computadora externa y estos se veran tambien en la Raspberry. Como por ejemplo el paquete cmatrix, a traves del comando:

```bash
sudo apt install cmatrix
```

Esto lo instalara en la computadora externa y en el Raspberry. Esto lo podemos comprobar ejecutando el siguiente comando en la terminal de las Raspberry:

```bash
cmatrix
```

# Conclusión

En la primera entrega, logramos instalar el sistema operativo con sus respectivas configuraciones para posteriormente realizar una conexion mediante el protocolo SSH entre una Raspberry y una PC.