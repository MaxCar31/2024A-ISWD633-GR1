## Esquema para el ejercicio
![Imagen](imagenes/esquema-ejercicio3.PNG)

### Crear red net-wp
```
docker network create net-wp
```

### Para que persista la información es necesario conocer en dónde mysql almacena la información.
# COMPLETAR LA SIGUIENTE ORACIÓN. REVISAR LA DOCUMENTACIÓN DE LA IMAGEN EN https://hub.docker.com/)
En el esquema del ejercicio la carpeta contenedor (a) es (COMPLETAR CON LA RUTA)
Ruta carpeta host: .../ejercicio3/db

### ¿Qué contiene la carpeta db del host?

La carpeta db del host contiene los archivos de base de datos de MySQL, incluyendo los datos de las tablas, los índices y la información del esquema de la base de datos.

### Crear un contenedor con la imagen mysql:8  en la red net-wp, configurar las variables de entorno: MYSQL_ROOT_PASSWORD, MYSQL_DATABASE, MYSQL_USER y MYSQL_PASSWORD
# COMPLETAR CON EL COMANDO

```
docker run -d --name mi_mysql --network net-wp -v Users/LabP3E004/Desktop/Practica3/db:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=root_password -e MYSQL_DATABASE=mi_base_datos -e MYSQL_USER=usuario -e MYSQL_PASSWORD=password mysql:8
```
### ¿Qué observa en la carpeta db que se encontraba inicialmente vacía?

Ahora la carpeta db contiene los archivos del sistema de base de datos MySQL, tales como los archivos de configuración y los datos de las bases de datos.

### Para que persista la información es necesario conocer en dónde wordpress almacena la información.
# COMPLETAR LA SIGUIENTE ORACIÓN. REVISAR LA DOCUMENTACIÓN DE LA IMAGEN EN https://hub.docker.com/)
En el esquema del ejercicio la carpeta contenedor (b) es (COMPLETAR CON LA RUTA)
Ruta carpeta host: .../ejercicio3/www

### Crear un contenedor con la imagen wordpress en la red net-wp, configurar las variables de entorno WORDPRESS_DB_HOST, WORDPRESS_DB_USER, WORDPRESS_DB_PASSWORD y WORDPRESS_DB_NAME (los valores de estas variables corresponden a los del contenedor creado previamente)

```
docker run -d --name mi_wordpress --network net-wp -v Users/LabP3E004/Desktop/Practica3/www:/var/www/html -e WORDPRESS_DB_HOST=mi_mysql -e WORDPRESS_DB_USER=usuario -e WORDPRESS_DB_PASSWORD=password -e WORDPRESS_DB_NAME=mi_base_datos wordpress
```

### Personalizar la apariencia de wordpress y agregar una entrada

Acceder a la interfaz de WordPress en tu navegador
Iniciar sesión con tus credenciales de WordPress.
Personalizar la apariencia en el menú de temas y agrega una nueva entrada en el panel de administración

### Eliminar el contenedor y crearlo nuevamente, ¿qué ha sucedido?

Después de eliminar y volver a crear el contenedor, todas las personalizaciones y entradas añadidas siguen presentes. Esto se debe a que los datos de WordPress y MySQL están almacenados en los volúmenes del host (.../ejercicio3/www para WordPress y .../ejercicio3/db para MySQL), asegurando la persistencia de los datos.


