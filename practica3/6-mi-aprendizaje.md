## Comparación de Conocimientos Antes y Después de la Práctica
- Antes de realizar esta práctica, mis conocimientos sobre Docker eran principalmente teóricos, con poca experiencia práctica en la implementación de entornos completos. A continuación, detallo los principales aprendizajes logrados y sus beneficios para mi formación profesional.

## Principales Aprendizajes
Redes Docker:

- Aprendí a crear redes personalizadas (docker network create) y conectar contenedores a estas redes, mejorando la comunicación interna entre servicios.
Volúmenes en Docker:

- Desarrollé habilidades para crear y gestionar volúmenes nombrados (docker volume create) y bind mounts, asegurando la persistencia de datos a través de la eliminación y recreación de contenedores.
Implementación de Servicios:

- Configuré un entorno completo con PostgreSQL y Drupal, utilizando variables de entorno para configurar servicios y asegurar su correcto funcionamiento.
Administración de Bases de Datos:

- Utilicé pgAdmin para administrar PostgreSQL, conectándome a través del nombre del contenedor, lo que facilitó la gestión y resolución de problemas de conexión.
Persistencia de Datos:

- Implementé soluciones de persistencia tanto para PostgreSQL como para Drupal, garantizando la continuidad de los datos y configuraciones a pesar de la recreación de contenedores.

### Resolución de Problemas

- Enfrenté un problema de conexión con pgAdmin, que solucioné utilizando el nombre del contenedor (server-postgres) en lugar de la dirección IP. Esta solución destacó la importancia de los nombres de contenedor en redes Docker personalizadas.

### Beneficio para la Formación Profesional
- Este ejercicio práctico ha mejorado significativamente mis habilidades técnicas en Docker, cruciales para la ingeniería de software moderna. La capacidad de implementar y gestionar entornos de desarrollo y producción con Docker es altamente valorada en la industria, preparándome mejor para desafíos reales en el desarrollo de software y en infraestructura de TI. Esta experiencia práctica fortalece mi base teórica y me proporciona una ventaja competitiva en el ámbito profesional.
