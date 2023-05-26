# Ejercicios de NodeRed y MySQL

## Requisitos previos

1. Arrancar el sistema de docker
- docker ps -a
- docker start $(docker ps -a -q)
- netstat -an | grep tcp
2. El archivo compose debe hacer uso de volumenes en el contenedor de mosquitto para que haga uso de un archivo mosquitto.conf personalizado que permita las conexiones externas

- Detener el contenedor de nodeRed

	```docker stop [id_contenedor]```
	
- Eliminar el contenedor de nodeRed

	```docker rm [id_contenedor]```
	
- Eliminar la imagen de nodeRed

	```
	docker images
	docker rmi [id_contenedor]
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
	- localhost (mosquitto)
	- Tema: codigoIoT/mqtt/clima
	- Output: a String
3. Agregar un nodo JSON. Siempre convertir a JavaScript Object
4. Agregar dos nodos function

Nodo function temperatura

msg.payload = msg.payload.temp;
msg.topic = "Temperatura";
return msg;

Nodo function humedad

msg.payload = msg.payload.hum;
msg.topic = "Humedad";
return msg;

5. Crear una pestaña y dos grupos de informacion
- Pestaña: Clima local
- Grupo1: Indicadores
- Grupo2: Gráclksfica
6. Agregar 2 nodos gauge y configurarlos
- Asociarlos al grupo indicadores
- Determine etiquetas y rangos
7. Agregar el nodo chart
- Asociarlos al grupo indicadores
