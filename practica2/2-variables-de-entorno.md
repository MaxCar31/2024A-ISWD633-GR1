# Variables de Entorno
### ¿Qué son las variables de entorno?
# COMPLETAR
Las variables de entorno son pares clave-valor que se utilizan para configurar el entorno en el que se ejecutan las aplicaciones. Estas variables permiten a los sistemas operativos y aplicaciones acceder a información de configuración necesaria sin tener que codificar estos valores directamente en el software. 

### Para crear un contenedor con variables de entorno

```
docker run -d --name <nombre contenedor> -e <nombre variable1>=<valor1> -e <nombre variable2>=<valor2>
```

### Crear un contenedor a partir de la imagen de nginx:alpine con las siguientes variables de entorno: username y role. Para la variable de entorno rol asignar el valor admin.

# COMPLETAR

```
docker run -d --name my-nginx-container -e username=user1 -e role=admin nginx:alpine
```

# CAPTURA CON LA COMPROBACIÓN DE LA CREACIÓN DE LAS VARIABLES DE ENTORNO DEL CONTENEDOR ANTERIOR

![image](https://github.com/MaxCar31/2024A-ISWD633-GR1/assets/141116497/b313a2fa-04ba-4e96-a42a-b3c2283e8df4)
![image](https://github.com/MaxCar31/2024A-ISWD633-GR1/assets/141116497/e48faca8-9338-4343-8802-128daaf73f0f)


### Crear un contenedor con mysql:8 , mapear todos los puertos
# COMPLETAR

```
docker run -P -d --name my-mysql-container -e MYSQL_ROOT_PASSWORD=my-secret-pw mysql:8
```
![image](https://github.com/MaxCar31/2024A-ISWD633-GR1/assets/141116497/f7622096-93a6-4b4b-a528-115922f53f2c)


### ¿El contenedor se está ejecutando?
# COMPLETAR

```
docker ds
```
![image](https://github.com/MaxCar31/2024A-ISWD633-GR1/assets/141116497/be15c06d-81d9-4c81-9f41-71bbcea20e50)


### Identificar el problema
# COMPLETAR

Si my-mysql-container no aparece en la lista de contenedores en ejecución, verifica los logs del contenedor para identificar el problema:

```
docker logs my-mysql-container
```

Revisar los logs para cualquier mensaje de error o advertencia que pueda indicar por qué el contenedor no se está ejecutando correctamente. 

### Eliminar el contenedor creado con mysql:8 
# COMPLETAR

```
docker stop my-mysql-container
docker rm my-mysql-container
```


### Para crear un contenedor con variables de entorno especificadas
- Portabilidad: Las aplicaciones se vuelven más portátiles y pueden ser desplegadas en diferentes entornos (desarrollo, pruebas, producción) simplemente cambiando el archivo de variables de entorno.
- Centralización: Todas las configuraciones importantes se centralizan en un solo lugar, lo que facilita la gestión y auditoría de las configuraciones.
- Consistencia: Asegura que todos los miembros del equipo de desarrollo o los entornos de despliegue utilicen las mismas configuraciones.
- Evitar Exposición en el Código: Mantener variables sensibles como contraseñas, claves API, y tokens fuera del código fuente reduce el riesgo de exposición accidental a través del control de versiones.
- Control de Acceso: Los archivos de variables de entorno pueden ser gestionados con permisos específicos, limitando quién puede ver o modificar la configuración sensible.

Previo a esto es necesario crear el archivo y colocar las variables en un archivo, **.env** se ha convertido en una convención estándar, pero también es posible usar cualquier extensión como **.txt**.

```
docker run -P -d --name my-mysql-env-container --env-file=.env mysql:8
```


**Considerar**
Es necesario especificar la ruta absoluta del archivo si este se encuentra en una ubicación diferente a la que estás ejecutando el comando docker run.

### Crear un contenedor con mysql:8 , mapear todos los puertos y configurar las variables de entorno mediante un archivo
# COMPLETAR
docker run -P -d --name my-mysql-env-container --env-file=.env mysql:8
# CAPTURA CON LA COMPROBACIÓN DE LA CREACIÓN DE LAS VARIABLES DE ENTORNO DEL CONTENEDOR ANTERIOR 

![image](https://github.com/MaxCar31/2024A-ISWD633-GR1/assets/141116497/ea72b6c3-5dc4-4293-84ab-92df3717e076)

### ¿Qué bases de datos existen en el contenedor creado?
# COMPLETAR

docker exec -it my-mysql-container mysql -u root -p
Enter password: my-secret-pw
SHOW DATABASES;

![image](https://github.com/MaxCar31/2024A-ISWD633-GR1/assets/141116497/d4cc000e-48f7-40f8-b2df-1e6311ca3c9c)
![image](https://github.com/MaxCar31/2024A-ISWD633-GR1/assets/141116497/abb5eece-b63e-419e-9e89-8cc11c611171)



