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



