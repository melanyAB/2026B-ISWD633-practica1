## Esquema para el ejercicio
![Imagen](esquema-ejercicio3.PNG)

### Crear red net-wp
```
docker network create net-wp
```

### Para que persista la información es necesario conocer en dónde mysql almacena la información.
# COMPLETAR LA SIGUIENTE ORACIÓN. REVISAR LA DOCUMENTACIÓN DE LA IMAGEN EN https://hub.docker.com/
En el esquema del ejercicio carpeta del contenedor (a) es /var/lib/mysql

Ruta carpeta host: .../ejercicio3/db

### ¿Qué contiene la carpeta db del host?
Se encuentra completamente vacía, ya que acaba de ser creada en el host y aún no se ha vinculado ni inicializado ningún contenedor de base de datos sobre ella.

### Crear un contenedor con la imagen mysql:8  en la red net-wp, configurar las variables de entorno: MYSQL_ROOT_PASSWORD, MYSQL_DATABASE, MYSQL_USER y MYSQL_PASSWORD
```
docker run -d --name mysql-wp --network net-wp -e MYSQL_ROOT_PASSWORD=123ab -e MYSQL_DATABASE=wordpress -e MYSQL_USER=usuario1 -e MYSQL_PASSWORD=456 -v "%cd%\db:/var/lib/mysql" mysql:8
```

### ¿Qué observa en la carpeta db que se encontraba inicialmente vacía?
Ahora contiene todas las carpetas y archivos internos de MySQL.

### Para que persista la información es necesario conocer en dónde wordpress almacena la información.
# COMPLETAR LA SIGUIENTE ORACIÓN. REVISAR LA DOCUMENTACIÓN DE LA IMAGEN EN https://hub.docker.com/
En el esquema del ejercicio la carpeta del contenedor (b) es /var/www/html/

Ruta carpeta host: .../ejercicio3/www

### Crear un contenedor con la imagen wordpress en la red net-wp, configurar las variables de entorno WORDPRESS_DB_HOST, WORDPRESS_DB_USER, WORDPRESS_DB_PASSWORD y WORDPRESS_DB_NAME (los valores de estas variables corresponden a los del contenedor creado previamente)
```
docker run -d --name wordpress-wp --network net-wp -p 9500:80 -e WORDPRESS_DB_HOST=mysql-wp -e WORDPRESS_DB_USER=usuario1 -e WORDPRESS_DB_PASSWORD=456 -e WORDPRESS_DB_NAME=wordpress -v "%cd%\www:/var/www/html" wordpress
```

### Personalizar la apariencia de wordpress y agregar una entrada

### Eliminar el contenedor y crearlo nuevamente, ¿qué ha sucedido?

Al eliminar el contenedor y crearlo nuevamente, la información no se pierde el sitio conserva el tema personalizado y la entrada publicada, ocurre porque los archivos de WordPress se guardan en la carpeta www del host y los datos de la base de datos en la carpeta db, que existen fuera del contenedor

