# Ejercicios de NodeRed

## Requisitos previos

1. Arrancar el sistema de docker
- docker ps -a
- docker start $(docker ps -a -q)
- netstat -an | grep tcp

## [Flow 2: Nodo Function](https://edu.codigoiot.com/mod/lesson/view.php?id=3896&pageid=3821)

1. Entrar a [localhost:1880](http://localhost:1880)
2. Exportar el flow 1 haciendo clic en Menu > Exportar > Current Flow > JSON > formatted > download. Opcional, tomarlo del repositorio de clase anterior.
3. Importar el flow 1 haciendo clic en Menu > Importar > Seleccionar un archivo para importar > Importar > Importar una copia
4. Configurar el nodo function haciendo doble clic sobre el
5. Agregar el codigo del [ejemplo ](https://edu.codigoiot.com/mod/lesson/view.php?id=3896&pageid=3824) a la pestaña On Message
6. Activar el nodo Debug y asegurarse de que el nodo inject este lanzando mensajes cada 5 segundos
7. Hacer clic en Deploy.

## [Flow 3: Panel de control con Nodos Dashboard](https://edu.codigoiot.com/mod/lesson/view.php?id=3897)

### Requisitos
Contar con los nodos dashboard

### Instrucciones

1. Duplicar el flow 2 con las mecanicas de exportar e importar
2. Renombrar el flow a Flow 3
3. Agregar el nodo texto
4. Crear una pestaña en la sección Dashboard
5. Crear un grupo
6. Configurar el nodo texto para que se visualice en el grupo recien creado
7. Hacer clic en Deploy y consultar el [Dashboard](http://localhost:1880/ui)

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




## Notas

- El icono azul en los nodos indica que esos nodos no estan desplegados
- Las dobles diagonales indican comentarios //
- Documentacion [toString](https://nodejs.org/api/buffer.html#buftostringencoding-start-end)
- Formas de poner texto en codigo en markdown

~~~
Texto
~~~

```
Texto
```
- Para desactivar un flow hacer clic en la pestaña del flow, hacer clic en el boton disable, clic en done y clic en deploy
- Para cambiar el nombre de un flow hacer doble clic en la pestaña y cambiar el nombre
- Los nodos con un triangulo anaranjado no están configurados


