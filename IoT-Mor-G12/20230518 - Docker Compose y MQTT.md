# Instalación de Docker
https://edu.codigoiot.com/mod/lesson/view.php?id=3888&pageid=3802

## Requisitos para instalar Docker
1. Procesador compatible con virtualización
2. Sistema operativo compatible con KVM
	- Activar la compatibilidad con KVM en la máquina virtual: Virtuar Box > Configuracion > Sistema > Aceleración > KVM
3. Se requieren 4GB de RAM

#Instalación de Docker

1. Se instalara con el script fácilito
https://docs.docker.com/engine/install/ubuntu/#install-using-the-convenience-script

- curl -fsSL https://test.docker.com -o test-docker.sh
- sudo sh test-docker.sh

2. Comprobar la instalación
- docker --version

3. Comprobar que Docker funcione
- sudo systemctl status docker

## Probar Docker

1. sudo docker run hello-world

### Creación de una aplicación multi-contenedor con Docker

1. Crear los volumenes

mkdir -p ~/DockerVolumes/Mosquitto/config
mkdir -p ~/DockerVolumes/MySQL/config
mkdir -p ~/DockerVolumes/MySQL/data
mkdir -p ~/DockerVolumes/NodeRED/config
mkdir -p ~/DockerVolumes/NodeRED/data

2. Crear el archivo YAML

mkdir -p ~/DockerCompose
touch ~/DockerCompose/compose.yaml

3. Clonar el repositorio de Docker Compose
https://github.com/codigo-iot/servidor-IoT-basico-docker-compose/tree/main

4. Clonar el contenido del archivo compose.yaml del repositorio al de la carpeta compose ~/Documunets/DockerCompose

5. Cambiar la contraseña de mysql en la linea 19 el archivo yaml

5. Ejecutar el archivo compose
- docker compose up -d

## Introduccion a Mosquitto
https://edu.codigoiot.com/course/view.php?id=851

## Temas

miCasa
miCasa/plantaBaja/cocina/temperatura
miCasa/plantaBaja/cocina/humedad
miCasa/plantaBaja/sala/temperatura
miCasa/plantaBaja/sala/humedad
miCasa/plantaBaja/patio/temperatura
miCasa/plantaBaja/patio/humedad
miCasa/plantaAlta/


miCasa/plantaBaja/+/temperatura

miCasa/plantaBaja/cocina/temperatura
miCasa/plantaBaja/sala/temperatura
miCasa/plantaBaja/patio/temperatura


miCasa/plantaBaja/#

miCasa/plantaBaja/cocina/temperatura
miCasa/plantaBaja/cocina/humedad
miCasa/plantaBaja/sala/temperatura
miCasa/plantaBaja/sala/humedad
miCasa/plantaBaja/patio/temperatura
miCasa/plantaBaja/patio/humedad


miCasa/plantaBaja


#

QOS

## Ejemplo de mosquitto

### Realizar suscripcion

mosquitto_sub -h localhost -p 1883 -t codigoIoT/test -q 1 -i hugo_sub

mosquitto_sub -h localhost -t codigoIoT/test

docker exec -it [id_contenedor] mosquitto_sub -h localhost -t codigoIoT/test

### Realizar publicación

mosquitto_pub -h localhost -p 1883 -q 1 -i hubo_pub -t codigoIoT/test -m "Hola mosquitto"

mosquitto_pub -h localhost -t codigoIoT/test -m "Hola mosquitto"

docker exec -it [id_contenedor] mosquitto_pub -h localhost -t codigoIoT/test -m "Hola mosquitto"

# Notas

Consutalr ids de contedor con
- docker ps

## Chat publico
IP: 18.194.125.194

1. Suscribirse
docker exec -it [id_contenedor] mosquitto_sub -h 18.167.125.194 -t codigoIoT/test


2. Publicar
sudo docker exec -it [id_contenedor] mosquitto_pub -h 18.194.125.194 -t codigoIoT/test -m "Este es el mensaje 2"













