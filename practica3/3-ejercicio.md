## Esquema para el ejercicio
![Imagen](imagenes/esquema-ejercicio3.PNG)

### Crear red net-wp
```
docker network create net-wp -d bridge
```

### Para que persista la información es necesario conocer en dónde mysql almacena la información.
# COMPLETAR LA SIGUIENTE ORACIÓN. REVISAR LA DOCUMENTACIÓN DE LA IMAGEN EN https://hub.docker.com/)
En el esquema del ejercicio la carpeta contenedor (a) es /var/lib/mysql.
Ruta carpeta host: .../ejercicio3/db.

### ¿Qué contiene la carpeta db del host?
Contiene los datos de la base de datos MySQL, como tablas, índices y registros.

### Crear un contenedor con la imagen mysql:8  en la red net-wp, configurar las variables de entorno: MYSQL_ROOT_PASSWORD, MYSQL_DATABASE, MYSQL_USER y MYSQL_PASSWORD
```
docker run -d --name mysql --network net-wp -e MYSQL_ROOT_PASSWORD=mi_contraseña_segura -e MYSQL_DATABASE=wordpress -e MYSQL_USER=usuario_wp -e MYSQL_PASSWORD=contraseña_wp -v "%WORK_DIR%/db:/var/lib/mysql" mysql:8
```

### ¿Qué observa en la carpeta db que se encontraba inicialmente vacía?
La carpeta db ahora contiene archivos y directorios relacionados con la base de datos MySQL, como tablas, índices y registros  
creados por MySQL.

### Para que persista la información es necesario conocer en dónde wordpress almacena la información.
# COMPLETAR LA SIGUIENTE ORACIÓN. REVISAR LA DOCUMENTACIÓN DE LA IMAGEN EN https://hub.docker.com/)
En el esquema del ejercicio la carpeta contenedor (b) es /var/www/html
Ruta carpeta host: .../ejercicio3/www

### Crear un contenedor con la imagen wordpress en la red net-wp, configurar las variables de entorno WORDPRESS_DB_HOST, WORDPRESS_DB_USER, WORDPRESS_DB_PASSWORD y WORDPRESS_DB_NAME (los valores de estas variables corresponden a los del contenedor creado previamente)
```
docker run -d --name wordpress --network net-wp -e WORDPRESS_DB_HOST=mysql:3306 -e WORDPRESS_DB_USER=usuario_wp -e WORDPRESS_DB_PASSWORD=contraseña_wp -e WORDPRESS_DB_NAME=wordpress -v "%WORK_DIR%/www:/var/www/html" -p 8080:80 wordpress
```

### Personalizar la apariencia de wordpress y agregar una entrada

### Eliminar el contenedor y crearlo nuevamente, ¿qué ha sucedido?

Después de eliminar y recrear el contenedor, todas las personalizaciones y entradas en WordPress se mantienen.



