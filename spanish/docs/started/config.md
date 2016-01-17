# Configurando Phango

A continuación procederemos a hacer una mínima configuración de Phango. Puede ver una visión más profunda de la configuración [aquí](advanced/config.md)

Podemos comenzar entrando en el directorio **settings** dentro del directorio donde instalamos Phango, siendo en nuestro ejemplo llamado **phango**.

Una vez ahí copiamos el archivo config.php.sample a config.php y abrimos este archivo que tendrá el siguiente contenido:

```php
<?php

use PhangoApp\PhaModels\Webmodel;
use PhangoApp\PhaRouter\Routes;
use PhangoApp\PhaView\View;

Routes::$root_url='/';

Routes::$app='phangoapp/welcome';

Routes::$apps=['phangoapp/welcome', 'phangoapp/lang', 'phangoapp/admin'];

/**
* Configure database. You can configure multiple databases for different models.
*/ 

Webmodel::$host_db['default']='localhost';
    
Webmodel::$db['default']='database_name';

Webmodel::$login_db['default']='root';

Webmodel::$pass_db['default']='';

/**
* Property for define the theme.
* 
*/

View::$folder_env=array('views/default');

View::$theme=basename(View::$folder_env[0]);

/**
* Define the admin folder
*/

define('ADMIN_FOLDER', 'admin');

# Define an email

define('SENDER_EMAIL', 'example@example.com');

?>
```

A continuación explicaremos linea a linea este archivo:

```php
use PhangoApp\PhaModels\Webmodel;
use PhangoApp\PhaRouter\Routes;
use PhangoApp\PhaView\View;
```
Estas tres lineas definen tres [espacios de nombres](http://php.net/manual/en/language.namespaces.php) que se corresponden con 3 clases básicas de Phango, la de los modelos(Webmodel), las vistas(View), y las rutas(Routes), que definiran los controles, urls, etc.

Phango es un framework que puede usarse con el paradigma MVC (aunque esto no es obligatorio) y por tanto es lógico que en la configuración se aplique a los 3 elementos básicos.

#Configurar clase Routes

```php
Routes::$root_url='/';

Routes::$app='phangoapp/welcome';

Routes::$apps=['phangoapp/welcome', 'phangoapp/lang', 'phangoapp/admin'];
```

A continuación configuraremos la clase Routes. Esta clase se encarga de todo lo relacionado con las urls y su procesamiento por parte de Phango para redirigir al controlador adecuado.

En `Routes::$root_url='/';` definiremos la url raíz de la web, esto es, si instalamos Phango con una url raíz llamada **http://www.example.com** podemos dejarlo como está, sin embargo, si instalamos Phango en una subcarpeta del **documentroot** de nuestro servidor y accedemos a la web con esta url **http://www.example.com/phango**, deberíamos configurar esta linea como `Routes::$root_url='/phango/';`

En `Routes::$app='phangoapp/welcome';` configuraremos lo que será la aplicación o **módulo** al que accederemos en primera instancia al acceder a **index.php**. Esto será explicado más tarde, pero simplemente saber que un módulo de Phango es como cualquier otro paquete que pueda descargarse usando composer desde packagist pero con ciertas características especiales, como incluir controladores, templates, archivos css, etc que también serán explicadas en su momento. Esto es, si tenemos un módulo de Phango en /path/to/phango/vendor/example/package, para que este fuera el módulo al que Phango viese como principal y siempre que fuera un paquete Phango válido deberíamos configurar esta linea como lo siguiente: `Routes::$app='example/package';`

En `Routes::$apps=['phangoapp/welcome', 'phangoapp/lang', 'phangoapp/admin'];` definiremos en un array los módulos a los que Phango tiene permiso para acceder. Al igual que en el anterior parámetro, los módulos son paquetes instalados en /path/to/phango/vendor



Si hemos creado una clase para Phango para usar con composer, podemos usar **config.php** para configurar propiedades estáticas de nuestra clase igualmente.






