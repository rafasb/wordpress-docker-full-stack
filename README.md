# wordpress-docker-full-stack
Parametrización de Wordpress sobre docker-compose con base de datos mysql, datos persistentes y proxy inverso (NPM) para certificado SSL

Referencias:

* https://docs.docker.com/samples/wordpress/
* https://docs.docker.com/engine/install/
* https://docs.docker.com/engine/install/linux-postinstall/
* https://docs.docker.com/compose/install/
* https://github.com/jc21/nginx-proxy-manager

Pre-requisitos:

* Instalar docker y docker-compose
* Crear grupo docker y añadir al usuario al grupo. Hacer logout y login
* Instalar y configurar git (Claves, user.email y user.name)

Notas:

* NPM: 
    * Consola de administración en http://\<IPdeHOST\>:81
    * usuario (Email): admin@example.com    
    * Password: changeme 
    * El primer paso al acceder es cambiar los datos de administrador y su contraseña.


* Variables de entorno:
    Todos los valores de las variables de entorno deben ser cambiados para garantizar la seguridad (nombres de base de datos, nombres de usuario y sus contraseñas)

* Es necesario editar el fichero hosts (en Windows o en Linux) para poner un nombre asociado al host del despliegue.
