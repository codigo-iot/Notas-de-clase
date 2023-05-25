# Arrancar el contenedor de docker

## Requisitos:

1. El usuario actual tiene que estar en el grupo de sudo y docker

    ```groups $USER```

Para agregar el usuario al grpo docker:

    ```sudo usermod -aG docker $USER```

Para agregar el usuario al grupo de sudoers

```
su
sudo usermod -aG sudo newuser
exit
```

2. Deben estar creados todos los directorios de volumenes
```
mkdir -p ~/DockerVolumes/Mosquitto/config
mkdir -p ~/DockerVolumes/MySQL/config
mkdir -p ~/DockerVolumes/MySQL/data
mkdir -p ~/DockerVolumes/NodeRED/config
mkdir -p ~/DockerVolumes/NodeRED/data
```

3. Asegurarse de que en la carpeta Compose este el archivo YAML únicamente con el volumen de data descomentado para NodeRed

```
mkdir -p ~/DockerCompose
touch ~/DockerCompose/compose.yaml
```

Esta seccion está principalmente orientada a quienes no pueden arrancar el contenedor y les pide el siguiente arrchivo: settings.js

## Diagnostico del sistema
Me ayuda a saber si arranqué correctamente los contenedores
```
docker ps -a
```

En esta sección podemos ver que contenedores están funcionando

Para saber si el contenedor de NodeRed está funcionando, es necesario intentar arrancarlo

```
docker start $(docker ps -a -q)
```

Si tu contenedor no arranca, usa el comando 
```
docker logs [id_contenedor]
```
Para corregir el problema es necesario hacer o siguiente

1. Detener el contenedor con problemas

    ```docker stop [id_contenedor]```

2. Borrar el contenedor
    
    ```docker rm [id_contenedor]```
3. Borrar la imagen del contenedor
    
    ```docker images```
    ```docker rmi [id_imagen]```
    
4. Detener compose
- dirigirse a carpeta compose
- Detener compose
    ```docker compose down```
- Opcional: Si has probado todos los pasos previamente y no puedes arrancar nodeRed, reinicia aqui tu maquina virtual completa

5. Reiniciar Docker

    ```sudo systemctl restart docker```

6. Arrancar compose
- dirigirse a carpeta compose
- modificar el compose.yaml para que solo use el volumen data
- Arrancar compose
    ```docker compose up -d```
- Opcional: Si ya has intentado todos los comandos varias veces y no logras arrancar nodeRed en Compose con volumenes, pon aqui el YAML del repositorio, que no usa volumenes y repite

## Exportar un Flow

1. Hacer clic en el boton hamburguesa
2. Seleccionar la opción export 
3. Seleccionar lo que se quiere exportar

## Crear un repositorio de este ejercicio

1. Dirigirse a github.com e iniciar sesion
2. Hacer clic en el boton de crear nuevo repositorio
3. Configurar el nuevo repositorio
- Nombre de repositorio
- Desicripción de repositorio
- Activar la casilla Add README file
- Hacer clic en el boton repositorio
4. Clonar el repositorio a la maquina virtual
- Abrir el directorio GitHub con terminal 

    ```cd ~/Documents/GitHub```
- Clonar el repositorio

    ```git clone [url https del repo]```
5. Colocar el archivo flows.json recien descargado en el repositorio
6. Hacer el commit y el push
7. Hacer documentación del repositorio

## Referencias

- Referencia de documentación del flow1 https://github.com/codigo-iot/flow1-NodeRed

- Ejemplo de repositorio actualizado https://github.com/hugoescalpelo/flow1-g12/tree/main

