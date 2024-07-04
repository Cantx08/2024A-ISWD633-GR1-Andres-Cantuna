## Esquema para el ejercicio
![Imagen](imagenes/esquema-ejercicio3.PNG)

### Crear red net-wp
```
docker network create net-wp -d bridge
```

### Para que persista la información es necesario conocer en dónde mysql almacena la información.
# COMPLETAR LA SIGUIENTE ORACIÓN. REVISAR LA DOCUMENTACIÓN DE LA IMAGEN EN https://hub.docker.com/)
En el esquema del ejercicio la carpeta contenedor (a) es **/var/lib/mysql**
Ruta carpeta host: .../ejercicio3/db

### ¿Qué contiene la carpeta db del host?
El directorio db del host se encuentra vacío.

### Crear un contenedor con la imagen mysql:8  en la red net-wp, configurar las variables de entorno: MYSQL_ROOT_PASSWORD, MYSQL_DATABASE, MYSQL_USER y MYSQL_PASSWORD
```
docker run -d --name mysql-container --network net-wp --env-file=mysqlenv.txt -v C:/Users/ASUS/Documents/GitHub/2024A-ISWD633-GR1-Andres-Cantuna/practica3/ejercicio3/db:/var/lib/mysql  -p 3307:3306 mysql:8
```

### ¿Qué observa en la carpeta db que se encontraba inicialmente vacía?
Actualmente, contiene registros y directorios provenientes del contenedor mysql.

### Para que persista la información es necesario conocer en dónde wordpress almacena la información.
# COMPLETAR LA SIGUIENTE ORACIÓN. REVISAR LA DOCUMENTACIÓN DE LA IMAGEN EN https://hub.docker.com/)
En el esquema del ejercicio la carpeta contenedor (b) es /var/www/html
Ruta carpeta host: .../ejercicio3/www

### Crear un contenedor con la imagen wordpress en la red net-wp, configurar las variables de entorno WORDPRESS_DB_HOST, WORDPRESS_DB_USER, WORDPRESS_DB_PASSWORD y WORDPRESS_DB_NAME (los valores de estas variables corresponden a los del contenedor creado previamente)
docker run -d --name wordpress-container --network net-wp --env-file=wordpressenv.txt -v C:/Users/ASUS/Documents/GitHub/2024A-ISWD633-GR1-Andres-Cantuna/practica3/ejercicio3/www:/var/www/html  -p 9300:80 wordpress

### Personalizar la apariencia de wordpress y agregar una entrada

### Eliminar el contenedor y crearlo nuevamente, ¿qué ha sucedido?

Los datos persisten, es decir, todas las modificaciones realizadas previamente se mantienen. Al momento de utilizar volúmenes desde el host, los datos de MySQL y WordPress no se perderán, aún cuando se hayan eliminado sus respectivos contenedores. 



