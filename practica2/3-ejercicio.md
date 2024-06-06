### Crear contenedor de Postgres sin que exponga los puertos. Usar la imagen: postgres:11.21-alpine3.17

```
docker run -d --name my-postgres-container postgres>11.21-alpine3.17
```
<img width="578" alt="image" src="https://github.com/MaxCar31/2024A-ISWD633-GR1/assets/141116497/bf93d244-001c-4a2e-8436-7310790c8a18">

### Crear un cliente de postgres. Usar la imagen: dpage/pgadmin4

```
docker run -d --name my-pgadmin-container -p 80:80 -e PGADMIN_DEFAULT_EMAIL=admin@example.com -e PGADMIN_DEFAULT_PASSWORD=admin dpage/pgadmin4
```
<img width="575" alt="image" src="https://github.com/MaxCar31/2024A-ISWD633-GR1/assets/141116497/8aa2d6c0-0bd1-4ed2-ac27-6489eef4564c">


La figura presenta el esquema creado en donde los puertos son:
- a: (completar con el valor)
- b: (completar con el valor)
- c: (completar con el valor)

![Imagen](imagenes/esquema-ejercicio3.PNG)

## Desde el cliente
### Acceder desde el cliente al servidor postgres creado.
<img width="927" alt="image" src="https://github.com/MaxCar31/2024A-ISWD633-GR1/assets/141116497/fc07929d-323f-47f4-a03d-4945c3a340f9">
<img width="926" alt="image" src="https://github.com/MaxCar31/2024A-ISWD633-GR1/assets/141116497/126e4891-0832-46b4-bfc4-c8e353813c50">


### Crear la base de datos info, y dentro de esa base la tabla personas, con id (serial) y nombre (varchar), agregar un par de registros en la tabla, obligatorio incluir su nombre.

## Desde el servidor postgresl
### Acceder al servidor
### Conectarse a la base de datos info

Para ello es de preferencia es mejor que ambos contenedores esten en la misma network. 

<img width="789" alt="image" src="https://github.com/MaxCar31/2024A-ISWD633-GR1/assets/141116497/f39d146d-17a7-4e66-b7c8-7a03c77ddd8c">

Con nuestras variables de entorno creadas en my-postgres, vamos a conectarlo con mi cliente,

<img width="475" alt="image" src="https://github.com/MaxCar31/2024A-ISWD633-GR1/assets/141116497/f5f483fd-eb1b-4d6c-86d0-bda5f944ac77">

Ahora creamos un server y conectamos con las variables de entorno. 

<img width="351" alt="image" src="https://github.com/MaxCar31/2024A-ISWD633-GR1/assets/141116497/b6c844b1-3f33-4171-bb26-6de38c6b4bfb">


### Realizar un select *from personas
<img width="696" alt="image" src="https://github.com/MaxCar31/2024A-ISWD633-GR1/assets/141116497/0b8de631-c5d8-4710-8672-2f33d8ea2dee">
