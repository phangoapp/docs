# Configurando Phango

A continuación procederemos a hacer una mínima configuración de Phango. Puede ver una visión más profunda de la configuración [aquí](advanced/config.md)

Podemos comenzar entrando en el directorio **settings** dentro del directorio donde instalamos Phango, siendo en nuestro ejemplo llamado **phango**.

Una vez ahí copiamos el archivo config.php.sample a config.php y abrimos este archivo que tendrá el siguiente contenido:

```php
<?php

use PhangoApp\PhaModels\Webmodel;
use PhangoApp\PhaRouter\Routes;

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

