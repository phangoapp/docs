# Requisitos mínimos

Los requísitos mínimos son como mínimo la versión 5.4 de PHP junto a la extensión gd, aunque está última no es obligatoria. También recomendaría un sistema operativo tipo Unix como MacOS o GNU/Linux para desarrollo, aunque no debería dar de problemas con Windows.

# Instalando Phango Framework

Instalar Phango es muy sencillo, sólo necesitamos [PHP](http://www.php.net), [GIT](https://git-scm.com/) y [Composer](https://getcomposer.org/). Por supuesto, para aprovechar al máximo el framework necesitas tener ciertos conocimientos de las 3 herramientas.

Para instalar Phango comenzaremos ejecutando git con este comando:

`git clone https://github.com/phangoapp/phango phango`  siendo **phango** el directorio donde guardaremos el codigo descargado desde github.

Una vez hecho esto necesitamos generar un fichero composer.json, que contendrá todas las dependencias que necesita Phango para funcionar. Podemos generar el composer.json inicial con este comando dentro del directorio **phango**:

`php create_composer.php`

Si sale algún mensaje de error, deberías revisar si tienes permisos para crear archivos en el directorio especificado.

Una vez creado el archivo podemos usar composer. Dependiendo de como hayamos instalado **composer** deberemos ejecutar el comando de una u otra manera, pero una manera típica es esta:

`php composer.phar install`

Si hemos instalado **composer** de forma global podríamos hacer esto:

`composer install`

Si todo va bien, composer nos dirá todos los módulos que se han descargado y si no hay errores podemos proceder a una configuración inicial.

# Configuración de servidor web para desarrollo.

La forma más sencilla de configurar para desarrollo si se usan versiones de PHP más recientes, a partir de la versión 5.4.0 (cosa que debería hacerse por defecto si queremos la máxima estabilidad y rendimiento) es usar el servidor que viene con el ejecutable de php. Para usarlo sólo necesita ejecutar el siguiente comando:

```bash
php -S localhost:8080
```
<aside class="warning">
<strong>ATENCIÓN</strong><br />
Si ejecutas php en windows, necesitas que el comando esté en tu path
</aside>

Para acceder a Phango sólo necesitas poner en tu navegador la dirección:

`http://localhost:8080`

Y ya tendríamos nuestra versión de Phango lista para el desarrollo.

## Otras opciones

Si usamos Apache para desarrollo podemos apuntar el document root directamente al directorio **phango** que creamos anteriormente. 

Un ejemplo de configuración para Apache con PHP como módulo sería este:

```xml
<VirtualHost *:80>
        ServerAdmin webmaster@localhost
        DocumentRoot /path/to/your/phango

        <Directory /path/to/your/phango/>
            Options Indexes FollowSymLinks
            AllowOverride All
            Require all granted
        </Directory>
</VirtualHost>
```
Si quieres usar PHP con php-fpm (es decir, como fastcgi), deberías de utilizar la versión 2.4 de apache y el módulo mod_proxy_fcgi. Una vez hayas configurado php-fpm, puedes configurar apache de esta manera:

```xml
<VirtualHost *:80>
        ServerAdmin webmaster@localhost
        DocumentRoot /path/to/your/phango

        <Directory /path/to/your/phango/>
            Options Indexes FollowSymLinks
            AllowOverride All
            Require all granted
        </Directory>
        
        ProxyPassMatch ^/(.*\.php(/.*)?)$ fcgi://127.0.0.1:9000/path/to/your/phango/$1
        DirectoryIndex /index.php index.php
</VirtualHost>
```
Algunos argumentos pueden variar dependiendo de la configuración de php-fpm.

[Más información sobre php-fpm y Apache aquí](https://wiki.apache.org/httpd/PHP-FPM).

Personalmente para desarrollo recomiendo usar php en Apache como módulo al ser muy sencillo de configurar y ya hacer algo más complejo cuando llegue la hora del deploying en previsión de la carga que vaya a tener nuestro sitio web.

Si quieres más información, o configurar Phango con otros webservers como NGINX, por favor, sigue la siguiente guía:

[Preparando Phango para producción](/advanced/deploying).

