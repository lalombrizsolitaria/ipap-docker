# ENTORNO PHP (Symfony) - PHP 8.1 - MYSQL

## _Entorno de desarrollo en PHP 8.1, MySQL, Symfony 6 e incluye PhpMyAdmin_

### Estructura

- Generación de entorno con docker-compose (/.docker).
- Dockerfile para PHP 8.1 (/.docker/php). 
- El archivo php.ini (/.docker/php) reemplazará al del contenedor generado.
- Dockerfile para Nginx (/.docker/nginx) y archivos de configuración.
- Archivo .env (/.docker) donde se establecen parámetros generales de nombre del proyecto, timezone de PHP y conexión a la BD.

### Pasos a seguir

Descargar el proyecto desde GitHub. Se generará un directorio "ipap-docker".

```sh
git clone https://github.com/lalombrizsolitaria/ipap-docker.git
```

Una vez descargado el repo, ingresar a "/ipap-docker/.docker", y ejecutar...

```sh
docker-compose up --build -d
```

### Configuración de Symfony

Verificar que los contenedores estén funcionando, puede hacerlo con: 

```sh
docker ps -a
```

Ingresar a la terminal del contenedor de php, puede ser "_ipap-sy-php-1_", o por su id.

```sh
docker exec -it ipap-sy-php-1 /bin/bash
```

Al ingresar al contenedor, deberá ejecutar...


```sh
composer install
php bin/console make:migration
php bin/console doctrine:migrations:migrate
```


- Proyecto (https://github.com/lalombrizsolitaria/ipap-docker)
- Editor online de Markdown (https://dillinger.io/)
