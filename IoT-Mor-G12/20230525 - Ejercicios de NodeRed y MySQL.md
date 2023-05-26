# Ejercicios de NodeRed y MySQL

## Requisitos previos

1. Arrancar el sistema de docker
- docker ps -a
- docker start $(docker ps -a -q)
- netstat -an | grep tcp
2. El archivo compose debe hacer uso de volumenes en el contenedor de mosquitto para que haga uso de un archivo mosquitto.conf personalizado que permita las conexiones externas

- Detener el contenedor de mosquitto

	```docker stop [id_contenedor]```
	
- Eliminar el contenedor de mosquitto

	```docker rm [id_contenedor]```
	
- Eliminar la imagen de mosquitto

	```
	docker images
	docker rmi [id_cimagen]
	```
- Detener docker compose. Hay que entrar al directorio de compose

	```docker compose stop```
	

- Actualizar el archivo compose para que use el volumen que apunta al archivo mosquitto.conf y el archivo YAML

- Levantar docker compose

	```docker compose up -d``

## [Flow4: Estación climatica distribuida](https://edu.codigoiot.com/mod/lesson/view.php?id=3899)

### Requisitos

- Tener funcionando NodeRed

## Instrucciones

1. Crear un nuevo flow
2. Agregar un nodo mqtt
	- Agregar un nuevo broker y agregar únicamente la url
	- Server: mosquitto
	- Tema: ```codigoIoT/mqtt/clima```
	- Output: a String
3. Agregar un nodo JSON. Siempre convertir a JavaScript Object
4. Agregar dos nodos function

Nodo function temperatura

```
msg.payload = msg.payload.temp;
msg.topic = "Temperatura";
return msg;
```

Nodo function humedad

```
msg.payload = msg.payload.hum;
msg.topic = "Humedad";
return msg;
```

5. Crear una pestaña y dos grupos de informacion
- Pestaña: Clima local
- Grupo1: Indicadores
- Grupo2: Gráfica
6. Agregar 2 nodos gauge y configurarlos
- Asociarlos al grupo indicadores
- Determine etiquetas y rangos
7. Agregar el nodo chart
- Asociarlos al grupo indicadores
8. Abrir el dashboard en [localhost:1880/](http://localhost:1880/)
9. Probar el flow enviando el siguiente JSON por terminal con mosquitto

```
{
	"temp":18,
	"hum":51
}
```


	Comando de docker para mosquitto

	```
		docker exec -it [id_contenedor] mosquitto_pub -t codigoIoT/mqtt/clima -m '{"temp":18;"hum":51}'
	```
	
# [Introducción a MySQL](https://edu.codigoiot.com/course/view.php?id=1001)

- Una DB es un conjunto de información
- MySQL Server es un programa que recibe querys y devuelve información de la DB

## Configurar volumenes externos en MySQL con Docker

- Detener el contenedor de MySQL

	```docker stop [id_contenedor]```
	
- Eliminar el contenedor de MySQL

	```docker rm [id_contenedor]```
	
- Eliminar la imagen de MySQL

	```
	docker images
	docker rmi [id_imagen]
	```
- Detener docker compose. Hay que entrar al directorio de compose

	```docker compose stop```
	

- Actualizar el archivo compose para que use el volumenes. Debe ser el archivo de la carpeta DockerCompose, no el del repositorio. Descomentar la linea del archivo de configuración

- Mover el archivo my.cnf al directorio del volumen asignado para la configuración de MySQL

- Levantar docker compose

	```docker compose up -d```

## Crear una Base de Datos

- Entrar a MySQL

	```
	docker exec -it [id_contenedor] mysql -p
	```

- Crear base de datos

	```
	CREATE DATABASE <cursoode_db>;
	```

- Seleccionad base de datos

	```
	USE [nombre_db];
	```
	
- Crear una tabla en la DB

	```
	CREATE TABLE clima (id INT(6) UNSIGNED AUTO_INCREMENT PRIMARY KEY, fecha TIMESTAMP DEFAULT CURRENT_TIMESTAMP, nombre VARCHAR(248) NOT NULL, temperatura FLOAT(4,2) NOT NULL, humedad INT (6) NOT NULL);
	```

- Consultar talba

	```
	SHOW TABLES;
	```
- Describir la tabla

	```
	DESCRIBE [nombre_tabla];
	
- Agregar un dato

	```
	INSERT INTO [nombre_tabla] (columnas) VALUES (valores);
	```
	
	```
	INSERT INTO clima (nombre,temperatura,humedad) VALUES ("Hugo Escalpelo",21,50);
	```
	
- Consultar dato

	```
	SELECT * FROM clima;
	```
- Consulta condicional

	```
	SELECT * FROM clima WHERE id=2;
	SELECT * FROM clima WHERE temperatura=21.5;
	SELECT * FROM clima WHERE nombre="Hugo Escalpelo";
	```

## Referencias

- 10,000 horas no es fuciciente para ser un experto https://www.youtube.com/watch?v=FVK_i7arszw

- Documentación de MySQL para tipos de datos https://dev.mysql.com/doc/refman/8.0/en/integer-types.html






