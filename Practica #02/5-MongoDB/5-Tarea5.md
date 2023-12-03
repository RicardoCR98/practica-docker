***1. Crear contenedor de mongo sin que exponga sus puertos usar la imagen: mongo:3.6.23 y crear un cliente de mongo: mongo-express. Analizar qué variables de entorno son necesarias.***

Seguiremos estos pasos para la creación del servidor de mongo

1. **Crear el contenedor de MongoDB sin exponer puertos (servidor)**

- `docker run -d --name server-mongo -e MONGO_INITDB_ROOT_USERNAME=root -e MONGO_INITDB_ROOT_PASSWORD=root mongo:3.6.23`

En este ejemplo:

- `-d`: Ejecuta el contenedor en segundo plano.
- `--name server-mongo`: Asigna un nombre al contenedor.
- `-e MONGO_INITDB_ROOT_USERNAME=root -e MONGO_INITDB_ROOT_PASSWORD=root`: Configura el nombre de usuario y la contraseña del usuario root de MongoDB.

**Nota:** Aunque no estás exponiendo explícitamente puertos, el contenedor de MongoDB aún estará en ejecución en su red interna, pero no tendrás acceso directo desde el host.

2. **Crear el contenedor de mongo-express (cliente)**

- `docker run -d --name cliente-mongo-express -e ME_CONFIG_MONGODB_SERVER=server-mongo -e ME_CONFIG_MONGODB_ADMINUSERNAME=root -e ME_CONFIG_MONGODB_ADMINPASSWORD=root -p 8081:8081 mongo-express`

En este ejemplo:

- `-d`: Ejecuta el contenedor en segundo plano.
- `--name mongo-express`: Asigna un nombre al contenedor de mongo-express.
- -e ME_CONFIG_MONGODB_SERVER=mi-mongo-container: Indica el nombre del contenedor de MongoDB al que se conectará mongo-express.
- `-e ME_CONFIG_MONGODB_ADMINUSERNAME=root -e ME_CONFIG_MONGODB_ADMINPASSWORD=root`: Configura el nombre de usuario y la contraseña del usuario root de MongoDB para mongo-express.
- `-p 8081:8081`: Expone el puerto 8081 del host para acceder a mongo-express.


***2. Crear contenedor de postgres con la imagen: postgres:11.21-alpine3.17 y crear un cliente dpage/pgadmin4. Analizar qué variables de entorno son necesarias.***

1. **Crear el contenedor de PostgreSQL:**

- `docker run -d --name server-postgres -e POSTGRES_USER=root -e POSTGRES_PASSWORD=root -e POSTGRES_DB=mydatabase postgres:11.21-alpine3.17`

En este ejemplo:

- `-d`: Ejecuta el contenedor en segundo plano.
- `--name server-postgres`: Asigna un nombre al contenedor.
- `-e POSTGRES_USER=root -e POSTGRES_PASSWORD=root -e POSTGRES_DB=mydatabase`: Configura el nombre de usuario, contraseña y base de datos por defecto.

2. **Crear el contenedor de pgAdmin 4:**

- `docker run -d --name cliente-pgadmin -e PGADMIN_DEFAULT_EMAIL=admin@example.com -e PGADMIN_DEFAULT_PASSWORD=root -p 5050:80 dpage/pgadmin4`

En este ejemplo:

- `-d`: Ejecuta el contenedor en segundo plano.
- `--name mi-pgadmin-container`: Asigna un nombre al contenedor de pgAdmin 4.
- `-e PGADMIN_DEFAULT_EMAIL=admin@example.com -e PGADMIN_DEFAULT_PASSWORD=admin`: Configura el correo electrónico y la contraseña del usuario por defecto de pgAdmin 4.
- `-p 5050:80`: Expone el puerto 5050 del host para acceder a pgAdmin 4.

3. **Configurar pgAdmin 4 para conectarse a PostgreSQL:**

- Accede a pgAdmin 4 a través de tu navegador utilizando http://localhost:5050.
- Ingresa las credenciales que configuraste para el usuario por defecto.
- En el panel izquierdo, haz clic en "Add New Server".
- Completa la información requerida, incluyendo el nombre del servidor, host (nombre del contenedor de PostgreSQL), puerto (generalmente 5432), nombre de usuario y contraseña que configuraste para PostgreSQL.