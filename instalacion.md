# Instalacion de nextcloud



  En este documento se explicara todos los pasos a seguir a la hora de instalar nextcloud en nuestra maquina a traves de vagrant. Para ello, simplemente ves siguiendo los siguientes pasos:

  1. Lo primero de todo es descargar el [vagrantfile](https://elpuig.xeill.net/Members/vcarceler/smx-m07/actividades/dhcp-a5/vagrantfile)

  2. Una vez tenemos el vagrant tenemos que descargar [nextcloud](https://nextcloud.com/). Para ello pulsamos en "Get nextcloud" y en el desplegable pulsamos "Server packages", en la ventana que se abrira hacemos clic en Download nexcloud para decargarlo

  ![](/Nextcloud/img/N1.png)

  3. Cuando tenemos los dos ficheros colocamos los dos en la misma carpeta y abrimos el terminal. Nos colocamos en la carpeta utilizando el comando cd y ejecutamos el comando `vagrant up` y una vez este termine hacemos `vagrant ssh`

  ![](/Nextcloud/img/vagrant.up.png)

  4. Despues de hacer ssh ya estamos en la maquina virtual. Ahora lo que tenemos que hacer es instalar apache2, para ello, siendo sudo (si no lo eres ejecuta el momando `sudo -s`) ejecutamos los siguientes comandos:

~~~
  apt update
  apt install apache2
~~~

  5. Ahora lo que tenemos que hacer es utilizar el comando `cp` para copiar el zip de nexcloud, este esta en la carpeta compartida entre la maquina real y la virtual y lo tendremos que copiar en la carpeta `var/www/html`. Dentro de la carpeta compartida (`/vagrant/nextcloud`) ejecutamos el siguiente comando:

~~~
  cp nexcloud-22.2.0.zip /var/www/html/
~~~

  5.  El siguiente paso sera descomprimir el fichero, para ello primero tenemos que instalar el unzip. Siendo sudo (si no lo eres ejecuta el momando `sudo -s`) ejecuta el comando `apt update` y despues `apt install unzip`. Seguidamente dentro de la carpeta `/var/www/html` ejecutamos el comando `unzip nextcloud-22.2.0.zip`, despues si hacemos `ls` podremos ver que estan todos los ficheros

  ![](/Nextcloud/img/4.png)

  6. Despues de esto lo que tendremos que hacer es cambiarle los permisos a todos estos ficheros, para ellos dentro de esta carpeta ejecutamos todos estos comandos:

  ~~~
  chown -R www-data:www-data /var/www/html
  chmod -R 775 /var/www/html
  ~~~

  Despues de esto si hacemos `ls-l` veremos veremos los ficheros con los sigueitnes permisos:

  ![](/Nextcloud/img/7.png)

  7. 