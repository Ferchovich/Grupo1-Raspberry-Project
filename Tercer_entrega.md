# Tercer entrega - Xorg - Grupo 1
# Índice 
1. [Introducción](#introducción)
2. [Instalación del servidor dhcp](#instalación-del-servidor-dhcp)
3. [Configuración](#configuración)
4. [Conclusión](#conclusión)

# Introducción:

Nosotros somos el grupo 1, conformado por: Ferreyra Octavio -Galleguillo Lucas - Hlavach Joaquin - Lucero Octavio. En este apartado veremos la instalación del servidor DHCP. Luego de instalarla en la raspberry, luego lo configuraremos para que la Raspbery sea el servidor DHCP de la red lan de cada mesa. Con esto nuestra Raspberry ya quedaría lista para que nos conectemos a ella desde nuestras PC y generaremos nuestra red LAN.

Donde nuestro objetivo sera configurarlo de manera que el switch que usamos será el que forme la red LAN y nos conectaremos a él con nuestras notebooks. Además, a este mismo switch se conectará la raspberry para que brinde el servicio a los dispositivos de la red.

## Instalación del servidor dhcp

En el primer paso, prenderemos y conectaremos la raspberry. Antes de comenzar con la instalación de dicho servidor, es necesario actualizar el listado de paquetes mediante el comando:

```bash
sudo apt update
sudo apt upgrade
```
Luego una vez ya inciada, para instalar el servidor dhcp, deberemos usar el siguiente comando:

```bash
sudo apt install isc-dhcp-server
```

Al utilizar el comando "sudo" usara los permisos del superuser, seguido de un apt el cual es el gestor de paquetes predeterminado de Ubuntu y por ultimo el install acompañado del nombre del paquete que hace referencia al servidor DHCP.

## Configuración
Primero que todo hay que editar el archivo etc/network/interfaces e introducir los siguientes parámetros:

```bash
auto eth0
    iface eth0 inet static
    address 192.168.1.2
    netmask 255.255.255.0
    gateway 192.168.1.1
```
En este paso, lo que hacemos es asignarle una ip al servidor dhcp de nuestra Raspberry, también definiremos una ip gateway y una máscara de red.

Luego tendremos que editar el archivo etc/dhcp/dhcpd.conf y seleccionamos el rango de ip's para nuestra red:

```
subnet 192.168.1.0 netmask 255.255.255.0 {
    range 192.168.1.100 192.168.1.200;
    option routers 192.168.1.1;
    option domain-name-servers 8.8.8.8, 8.8.4.4;
}
```

El servicio DHCP sólo debe estar disponible para la red interna. Por eso, debe aceptar conexiones por la interfaz interna (eth0, en este caso). Esto puede indicarse en el archivo de configuración/etc/default/isc-dhcp-server

```bash
INTERFACESv4="eth0"
INTERFACESv6=""
```
Otro paso que realizamos fue editar el archivo etc/dhcpcd.conf para agregar los siguientes comandos:

```bash
interface eth0
static routers=192.168.1.1
dhcp-range=192.168.1.3,192.168.10,255.255.255.0,24h
```

Posteriormente reiniciamos el servicio dhcp:

```bash
sudo service isc-dhcp-server restart
sudo systemctl enable isc-dhcp-server
sudo reboot
sudo systemctl start isc-dhcp-server
```

# Conclusión

En esta tercer entrega, pudimos instalar el servidor DHCP para luego configurarla y asi poder usar el switch de manera que forme la red LAN y nos conectaremos a él con nuestras notebooks. Además, a este mismo switch se conectará la raspberry para que brinde el servicio a los dispositivos de la red.