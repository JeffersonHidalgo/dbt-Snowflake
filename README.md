# dbt-Snowflake
university Exercise/Practice dbt and snowflake 
### Jefferson Hidalgo Abreu 2021-1203

# Proyecto Final: Snowflake, dbt y Docker

Este proyecto final integra **Snowflake**, **dbt** y **Docker** para construir y administrar un entorno de análisis de datos escalable y eficiente. A continuación, se describen las tecnologías utilizadas, su instalación y ejecución.

## Tecnologías Utilizadas

### Snowflake
Snowflake es una plataforma de almacenamiento y análisis de datos basada en la nube. Su arquitectura permite almacenar datos estructurados y no estructurados con un rendimiento óptimo y escalabilidad automática.

Características principales:
- Almacenamiento y procesamiento de datos en la nube.
- Escalabilidad automática.
- Seguridad avanzada y cifrado de datos.

### dbt (Data Build Tool)
dbt es una herramienta de transformación de datos que permite a los equipos de analistas y científicos de datos crear modelos de datos versionados, documentados y probados directamente en su almacén de datos.

Características principales:
- Transformaciones SQL gestionadas.
- Documentación automática.
- Integración con CI/CD.

### Docker
Docker es una herramienta de contenedores que permite ejecutar aplicaciones de manera aislada en cualquier entorno. Este proyecto utiliza Docker para garantizar un entorno consistente durante el desarrollo y la ejecución.

Características principales:
- Portabilidad de aplicaciones.
- Consistencia entre entornos.
- Escalabilidad y fácil implementación.

## Requisitos Previos
Asegúrate de tener instalados:
- [Docker](https://www.docker.com/): Última versión.
- Acceso a [Snowflake](https://www.snowflake.com/).
- [dbt CLI](https://docs.getdbt.com/dbt-cli/installation).

## Instalación y Configuración

### Configurar Docker
1. Clona este repositorio:
   ```bash
   git clone https://github.com/usuario/proyecto-final.git
   cd proyecto-final
   ```
2. Construye el contenedor Docker:
   ```bash
   docker build -t proyecto-snowflake-dbt .
   ```
3. Ejecuta el contenedor:
   ```bash
   docker run -p 8080:8080 -d proyecto-snowflake-dbt
   ```

### Configurar Snowflake
1. Inicia sesión en tu cuenta de Snowflake.
2. Crea un esquema y una base de datos:
   ```sql
   CREATE DATABASE proyecto_final;
   CREATE SCHEMA proyecto_schema;
   ```

### Configurar dbt
1. Instala dbt CLI (si aún no lo tienes):
   ```bash
   pip install dbt
   ```
2. Configura tu archivo `profiles.yml` para conectar dbt con Snowflake:
   ```yaml
   default:
     target: dev
     outputs:
       dev:
         type: snowflake
         account: your_account
         user: your_user
         password: your_password
         role: your_role
         database: proyecto_final
         schema: proyecto_schema
         warehouse: your_warehouse
   ```
3. Ejecuta dbt:
   ```bash
   dbt run
   dbt test
   ```

## Imágenes del Proyecto
1. Arquitectura del proyecto:
   ![Arquitectura del Proyecto](./assets/arquitectura.png)
2. Flujo de Transformaciones en dbt:
   ![Flujo dbt](./assets/dbt.png)
3. Contenedor Docker en ejecución:
   ![Docker Container](./assets/docker.png)

## Uso
- Ingresa al contenedor de Docker:
  ```bash
  docker exec -it <container_id> bash
  ```
- Ejecuta las transformaciones de dbt:
  ```bash
  dbt run
  ```

## Contribuciones
Las contribuciones a este proyecto son bienvenidas. Por favor, abre un **issue** o envía un **pull request** para sugerencias y mejoras.

## Licencia
Este proyecto está bajo la Licencia MIT. Consulta el archivo `LICENSE` para más información.
