# Repositorio principal RabbitMQ - NestJS

## Composicion del proyecto

El repositorio cuenta con un `docker-compose.yml` 2 carpetas principales, `MongoDB y nginx`, las cuales tienen la configuracion para levantar los contenedores de MongoDB y Nginx

### Nginx

Funciona como balanceador de carga, el `docker-compose.yml` se encargara de crear 3 replicas del consumer, Nginx hara un balanceador de carga apuntando al puerto 4000, el distribuira las peticiones entre los 3 consumidores.

### Como correr el proyecto

Simplemente clona el proyecto

`git clone --recursive <URL>`

`cd <PROYECTO>`

`docker compose up -d`

## Rabbit Consumer

Es una aplicacion hibrida de Nest, acepta tanto peticiones HTTP como mensajes mediante RabbitMQ.

Cuenta con un endpoint que permite de acceder de forma directa a los datos en MongoDB.

`[GET] http://localhost:4000/api/consumer/users/`

Una vez corriendo Nginx se apunta hacia el puerto 4000, si se decide correr localmente el repositorio de rabbit-consumer, este apunta hacia el 3001

## Rabbit Producer

Es una aplicacion de Nest, basada solamente en HTTP, cuenta con 2 endpoint que apunten a los message pattern create-users y get-all-users

`[POST] http://localhost:3000/api/producer/users/`

`[GET] http://localhost:3000/api/producer/users/`
