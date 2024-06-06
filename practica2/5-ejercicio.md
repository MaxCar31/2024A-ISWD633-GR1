## Esquema para el ejercicio

![image](https://github.com/MaxCar31/2024A-ISWD633-GR1/assets/141116497/ca2e160b-5191-46c9-8bd8-ee4e944fd5bf)


### Crear la red
# COMPLETAR

```
docker network create net-wp -d bridge
```

### Crear el contenedor mysql a partir de la imagen mysql:8, configurar las variables de entorno necesarias

```
docker run -d --name contenedor-mysql --network net-wp -e MYSQL_ROOT_PASSWORD=rootpassword -e MYSQL_DATABASE=wordpress -e MYSQL_USER=wpuser -e MYSQL_PASSWORD=wppassword mysql:8
```

### Crear el contenedor wordpress a partir de la imagen: wordpress, configurar las variables de entorno necesarias

```
docker run -d --name contenedor-wordpress --network net-wp -e WORDPRESS_DB_HOST=contenedor-mysql:3306 -e WORDPRESS_DB_USER=wpuser -e WORDPRESS_DB_PASSWORD=wppassword -e WORDPRESS_DB_NAME=wordpress -p 9300:80 wordpress
```
<img width="958" alt="image" src="https://github.com/MaxCar31/2024A-ISWD633-GR1/assets/141116497/3a132aea-18e8-44f6-b400-9eff65c79e92">

En el esquema, el puerto a es el puerto mapeado para acceder al contenedor de WordPress desde el host. En este caso, el puerto a es 9300.

Ingresar desde el navegador al wordpress y finalizar la configuración de instalación.

<img width="406" alt="image" src="https://github.com/MaxCar31/2024A-ISWD633-GR1/assets/141116497/6514daf9-ed35-44fc-a8cd-8969edadca7b">

Desde el panel de admin: cambiar el tema y crear una nueva publicación.
Ingresar a: http://localhost:9300/ 
recordar que a es el puerto que usó para el mapeo con wordpress

<img width="922" alt="image" src="https://github.com/MaxCar31/2024A-ISWD633-GR1/assets/141116497/d7a6deed-5c3c-477d-b5ee-9e7611bf6b4e">
<img width="924" alt="image" src="https://github.com/MaxCar31/2024A-ISWD633-GR1/assets/141116497/6a5b0d95-9c92-488f-8d5e-4fdadd2c6c9a">


### Eliminar el contenedor wordpress
<img width="800" alt="image" src="https://github.com/MaxCar31/2024A-ISWD633-GR1/assets/141116497/cbc4797a-7622-4e78-83e8-b502c5610c3c">

### Crear nuevamente el contenedor wordpress
<img width="960" alt="image" src="https://github.com/MaxCar31/2024A-ISWD633-GR1/assets/141116497/bbfbf17b-8aad-4b76-a1b6-f27cd7183e4e">

Ingresar a: http://localhost:9300/ 
recordar que a es el puerto que usó para el mapeo con wordpress
<img width="897" alt="image" src="https://github.com/MaxCar31/2024A-ISWD633-GR1/assets/141116497/44dce252-761d-4c8d-bacc-898866dafa67">

### ¿Qué ha sucedido, qué puede observar?

Al recrear el contenedor de WordPress, el sitio web debería estar en el mismo estado que antes de eliminar el contenedor. Esto es porque la base de datos MySQL sigue existiendo y contiene todos los datos de WordPress, incluyendo las publicaciones, configuraciones y el tema seleccionado. La persistencia de los datos en MySQL asegura que al iniciar un nuevo contenedor de WordPress, éste pueda conectarse a la misma base de datos y recuperar toda la información.

Verificar Conexiones

```
docker network inspect net-wp
```
<img width="786" alt="image" src="https://github.com/MaxCar31/2024A-ISWD633-GR1/assets/141116497/b87f3189-f108-4a4d-adfc-6b41466d9ba8">



