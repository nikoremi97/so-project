## Miniproyecto Sistemas Operativos

**Universidad ICESI**  
**Curso:** Sistemas Operativos  
**Docente:** Daniel Barragán C.  
**Tema:**  Servicios web  
**Correo:** daniel.barragan at correo.icesi.edu.co  
**Estudiantes:**  
Nicolás Recalde A00065888  
Alejandro Bueno A00335472  
Rubén Ceballos A00054636  

## Objetivos
* Desplegar una aplicación en un servidor que ejecuta el sistema operativo Linux
* Realizar los ajustes y depuración necesarios para desplegar una
aplicación en Linux
* Realizar aplicaciones para obtener información del sistema operativo

## Descripción
Para el despliegue de una aplicación en un servidor se requiere conocer los procedimientos necesarios relacionados con la configuracion de las interfaces de red, ajustes de seguridad, instalación de dependencias, usuarios y herramientas de depuracíon del sistema operativo.

El siguiente proyecto consiste en el despliegue de una aplicación web para obtener información del sistema operativo (La aplicación debe permitir consulta uso de CPU, memoria y espacio en disco). Para este propósito se debe emplear el sistema operativo Ubuntu Server 16.04, el microframework flask y ambientes virtuales.

<p align="center">
  <img src="images/vista-despliegue.png" alt="webservice architecture"/>
</p>

## Desarrollo

Para el desarrollo de este proyecto se instaló y se trabajó sobre una máquina virtual UbuntuServer 16.04  

![][1]  

**El proceso fue el siguiente:** 

**1.Configuración de las interfaces de red**  

Una para LocalHost y otra para Adaptador Puente

![][2]  

Luego, establece una dirección IP a la interfaz enp0s8 y se levanta esta misma.
```
sudo ip addr add 192.168.1.68/24 dev enp0s8
sudo ip link set dev enp0s8 up
```  
![][8]

**2. Configuración de puertos**  

Abrimos el puerto 5000 por el cual se configurará el servicio y el puerto 22 para la conexión SSH mediante Putty.
```
sudo ufw allow 22
sudo ufw allow 5000
```  
![][9] 

**3. Configuración de otras dependencias**

Se inicia sesión en MTPutty.

![][19]

Ahora debemos instalar pip. Para esto ejecutamos los siguientes comandos.  
```
 sudo apt-get update
 sudo apt-get -y upgrade
```  
Verificamos que Python3 haya sido instalado e instalamos pip.
```
 python3 -V
 sudo apt-get install -y python3-pip
```
**4. Creación de ambientes virtuales**  

Ahora procedemos a la creación de un ambiente virtual.  
```
 sudo pip3 install virtualenv 
 virtualenv proyecto
```  
![][10]

Ahora vamos al ambiente e instalamos Flask.  
```
 source proyecto/bin/activate 
 pip install flask
```  
![][11]  

**5. Aplicación en Python**  

Se requiere realizar una apliación en Python para obtener la información del sistema operativo (La aplicación debe permitir consulta uso de CPU, memoria y espacio en disco).

Primero, se crea archivo proyecto.py
```
vi proyecto.py
```  
![][14] 

Se asignan permisos de ejecución y se inicia el servicio.

![][12]
 
 Se valida la ejecución del servicio mediante el comando netstat.
 
![][13]

Las solicitudes que se pueden ver al servicio se presentan más adelante.

Se realiza prueba del servicio mediante el comando curl.

| home | cpu | memory | disk |
| --- | --- | --- | --- |
| ![][15] | ![][16] | ![][17] | ![][18] |

Por último, se valida la funcionalidad del servicio en un navegador Web (Chrome).

![][20]

## Referencias
* https://www.digitalocean.com/community/tutorials/how-to-install-python-3-and-set-up-a-local-programming-environment-on-ubuntu-16-04  
* https://www.digitalocean.com/community/tutorials/how-to-set-up-a-firewall-with-ufw-on-ubuntu-16-04  
* https://stackoverflow.com/questions/19267591/how-to-store-os-system-output-in-a-variable-or-a-list-in-python  

[1]: images/ubuntuServer.JPG
[2]: images/conftarjetared.JPG
[3]: images/firewallport.JPG
[4]: images/sshstart.JPG
[5]: images/virtualenv.JPG
[6]: images/installflask.JPG
[7]: images/service.JPG
[8]: images/so1.PNG
[9]: images/so2.PNG
[10]: images/so3.PNG
[11]: images/so4.PNG
[12]: images/so5.PNG
[13]: images/so6.PNG
[14]: images/so7.PNG
[15]: images/so8.PNG
[16]: images/so9.PNG
[17]: images/so10.PNG
[18]: images/so11.PNG
[19]: images/so12.PNG
[20]: images/so13.gif
