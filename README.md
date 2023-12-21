## Intalaremos las librerias
> sudo apt-get install php5-gd php5-json php5-curl
sudo apt-get install php5-intl php5-imagick

------------


## Descargamos el servidor
**crearemos una carpeta**
> sudo mkdir owncloud
cd owncloud

*descargaremos los ficheros de owncloud*
<p>
iremos a la pagina de owncloud, y vamos a los paquetes del servidor y copiaremos direccion de enlace de download unix del paso 1 y lo pegamos en nuestro codigo
</p>

**esperamos se descargue y descomprimimos**
> sudo tar -xvf owncloud-7.0.2.tar.bz2

<p>
esto genera una carpeta owncloud que sirve para moverla a nuestro servidor web
</p>

> sudo mv owncloud /var/www/html/
cd /var/www/htm/

**Para intalarlo hay que preparar la base de datos 192.168.1.200**
<p>
iniciamos sesion y vamos a base de datos y creamos el owncloud, luego creada entramos a privilegios en agregar un usuario y creamos el usuario, vamos donde tenemos el owncloud 
</p>

**en caso saliese errores de intalacion usamos**
> sudo ln -s /etc/php5/mods-available/mcrypt.ini /etc/php5/cli/conf.d/20-mcrypt.ini
sudo ln -s /etc/php5/mods-available/mcrypt.ini /etc/php5/apache2/conf.d/20-mcrypt.ini

**damos permisos para que lea en la web**
> sudo chmod 0775 owncloud –R
sudo chown -R www-data:www-data owncloud

**probamos en  el navegador si el servidor funciona**
<p>
meteremos los datos en un disco duro, para ello prepararemos una carpeta de datos
</p>


## Configurar Ip del servidor
**definimos una ip manual en caso no este**
> sudo vi /etc/network/interfaces

<p>
editamos el fichero y cambiamos el dhcp por static y usamos parametros
</p>
>  address 192.168.1.200
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
        dns-nameservers 8.8.8.8 8.8.4.4

**Estos dependen de cada lan**

Editaremos la configuración Apache

> sudo vi /etc/apache2/apache2.conf

Añadiremos al final 
> ServerName localhost

**Instalaremos Librerias php**

sudo apt-get install php5 libapache2-mod-php5 php5-mcrypt 

**Instalaremos MySQL**

> sudo apt-get install mysql-server php5-mysql

** Instalaremos phpmyadmin**

> sudo apt-get install phpmyadmin

<p>
probamos si sirve la ip y creamos una base de datos
</p>

**Instalaremos el servidor FTP**

> sudo apt-get install vsftpd}

**Configurar servidor FTP**

> sudo vi /etc/vsftpd.conf

**descomentamos estas líneas**

> anonymous_enable=NO
local_enable=YES
write_enable=YES
local_umask=022
local_root=/var/www

**reseteamos**
> sudo service vsftpd restart

**Damos permisos a la carpeta /var/www**

> sudo chown [Tu Usuario]:www-data /var/www –R
sudo chmod 0775 /var/www -R

<p>
Ya estaria todo
</p>

