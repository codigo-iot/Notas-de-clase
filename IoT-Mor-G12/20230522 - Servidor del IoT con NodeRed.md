# Servidor del Internet de las Cosas con NodeRed

https://edu.codigoiot.com/course/view.php?id=997

## Requisitos

- Tener instalado NodeRed por Docker
- Comprobar que NodeRed esté funcionando
	- netstat -an | grep 1880
- Comprobar que docker esté corriendo
	- sudo systemctl status docker
- Comprobar el estado de los contenedores
	- docker container ls -a
	Alternativemente:
	- docker ps -a
- Arrancar todos los contedores
	- docker start $(docker ps -a -q)
- Abrir NodeRed
	- http://localhost:1880
	
## Instalar los nodos dashboard

1. Abrir NodeRed
2. Abrir Manage Palette
3. Pestaña install
4. Buscar dashsboard
	- Instalar los nodos node-red-dashboard

## Ejercicio 1: Timestamp con NodeRed
https://edu.codigoiot.com/mod/lesson/view.php?id=3895&forceview=1

1. Asegurarse que el contenedor funciona con volumenes
- Comprobar que el archivo compose usa volumenes para la carpeta /data del contenedor de nodeRed
- Detener el contenedor de NodeRed docker stop [id_contenedor]
- Borrar el contenedor docker rm [id_contenedor]
- Detener compose con el comando docker compose down
- Correr el archivo compose con los cambios de volumenes sudo docker compose up -d desde el directorio donde se encuentra el archivo YAML

2. Agregar un nodo inject
3. Agregar nodo debug
4. Hacer clic en deploy	
5. Ir a la pestaña debug





#Referencias
- NodeRed 2022 https://edu.codigoiot.com/course/view.php?id=278

- NodeRed https://nodered.org/
- NodeRed Docker https://nodered.org/docs/getting-started/docker
- Documentación de NodeRed https://nodered.org/docs/user-guide/nodes


## Metodo alternativo para compose
- Comprobar que el archivo compose usa volumenes para la carpeta /data del contenedor de nodeRed
- docker stop [id_contenedor]
- docker rm [id_contenedor]
- docker images
- docker rmi [id_imagen]
- dirigirse a carpeta compose
- docker compose down
- modificar el compose.yaml
- docker compose up -d

