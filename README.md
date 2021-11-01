# Wordpress docker full stack
Parametrización de Wordpress sobre docker-compose con base de datos mysql, datos persistentes y proxy inverso (NPM) para certificado SSL.

Nos permitirá disponer de un servidor wordpress, con certificado SSL gratuito de Let's Encrypt. 

## Pre-requisitos

En el equipo o máquina virtual donde vamos a instalar el servidor wordpress:

1) Instalar docker: https://docs.docker.com/engine/install/ y https://docs.docker.com/engine/install/linux-postinstall/ 

2) Instalar docker-compose: https://docs.docker.com/compose/install/

Asegurate de:
* El usuario debe disponer de permisos de `sudo`.
* Crear grupo docker y añadir al usuario al grupo `usermod -a -G docker $USER`. Hacer logout y login.
* Si vas a usar GIT no solo para clonar: Instalar y configurar GIT (Claves, user.email y user.name). 

## Instrucciones básicas

1) Clonar el directorio con: `git clone https://github.com/rafasb/wordpress-docker-full-stack.git`

2) Cambiar el directorio con `cd wordpress-docker-full-stack`

3) Ejecutar `docker-compose up -d`

## Tras el arranque

1) Accedemos a la consola de administración del proxy inverso (NPM) mediante `http://\<IPdeHOST\>:81`.

2) Usamos las credenciales:
    * usuario (Email): admin@example.com    
    * Password: changeme

3) Como primer paso al acceder cambiaremos los datos de administrador y su contraseña.

4) En caso de no disponer de acceso al servidor DNS: Es necesario editar el fichero hosts (en Windows o en Linux) para poner un nombre asociado al host del despliegue. 

5) Configuraremos los `proxy host` con el nombre del servidor y destino la IP del host con wordpress y el puerto 8000 (si se mantiene el valor del ejemplo).

## Para producción

* Variables de entorno:
    Todos los valores de las variables de entorno deben ser cambiados para garantizar la seguridad (nombres de base de datos, nombres de usuario y sus contraseñas).
* Para que funcione el servicio de Let's Encrypt, el servicio NPM debe ser accesible públicamente con el FQDN (nombre DNS).
* En caso de disponer de acceso al servidor DNS: Crear los nombre de host a utilizar con las direcciones IP del servidor NPM.
* Es posible separar este proyecto en dos máquina, creando dos docker-compose.yml, uno para el worpress y otro para el NPM.
* Combiene no emplear las versiones latest y fijarlas en el docker-compose.
* Combiene disponer de un registro de imágenes docker para almacenar las versiones empleadas de las imágenes.
* Disponer de un sistema de backup para el directorio `datos`

## Referencias

* https://docs.docker.com/samples/wordpress/
* https://github.com/jc21/nginx-proxy-manager