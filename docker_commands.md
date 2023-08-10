# Docker Commands

## Build docker image
```
docker build -t <name-image> .
```

## Sign up with docker
```
docker login -u <YOUR-USER-NAME>
```

## Publish docker image
*Give the <name-image> image a new name*
```
docker tag <name image> YOUR-USER-NAME/<image-name>
```
*Push image*
```
docker push YOUR-USER-NAME/getting-started
```

## Start container
```
docker run -dp <HOST-PORT>:<CONTAINER-PORT> YOUR-USER-NAME/getting-started
```

## Logs of container
```
docker logs <container-id>
```

## Create volume
```
docker volume create <name-volume>
```

## Inspect volume
```
docker volume inspect <name-volume>
```

## Create network
```
docker network create <name-network> --network-alias <name-alias>
```

## Docker scan
*Cuando haya creado una imagen, es una buena práctica escanearla en busca de vulnerabilidades de seguridad usando el docker scancomando. Docker se ha asociado con Snyk para proporcionar el servicio de análisis de vulnerabilidades.*

*iniciar sesión en Docker Hub para escanear sus imágenes*
```
docker scan --login
```

*Escanee sus imágenes*
```
docker scan <name-image>
```

## Check ip container
```
docker inspect -f '{{range.NetworkSettings.Networks}}{{.IPAddress}}{{end}}' <name-container>
```

## Eliminar las imágenes, los contenedores, los volúmenes y las redes sin utilizar o pendientes
*Docker proporciona un solo comando que eliminará cualquier recurso (imágenes, contenedores, volúmenes y redes) que estén pendientes (no asociados con un contenedor):*
```
docker system prune
```

*Para eliminar adicionalmente los contenedores detenidos y todas las imágenes no utilizadas (no solo aquellas pendientes), añada el indicador -a al comando:*
```
docker system prune -a
```

## Eliminar imágenes de Docker

**Eliminar imágenes de Docker**
*Utilice el comando docker images con el indicador -a para localizar el ID de las imágenes que quiere eliminar. Esto le mostrará todas las imágenes, incluidas las capas de imagen intermedias. Cuando localice las imágenes que desee eliminar, puede pasar su ID o etiqueta a docker rmi:*

*Enumerar:*
```
docker images -a
```

*Eliminar:*
```
docker rmi Image Image
```

**Eliminar imágenes pendientes**
*Las imágenes de Docker constan de varias capas. Las imágenes pendientes son capas que no tienen relación con imágenes etiquetadas. Ya no sirven para nada y ocupan espacio en el disco. Se pueden ubicar añadiendo el indicador de filtro -f junto con el valor dangling=true al comando docker images. Si está seguro de que quiere eliminarlas, puede utilizar el comando docker images purge:*

*Enumerar:*
```
docker images -f dangling=true
```

*Eliminar:*
```
docker images purge
```

**Eliminar imágenes según un patrón**
*Puede encontrar todas las imágenes que coinciden con un patrón utilizando una combinación de docker images y grep. Cuando esté conforme, puede eliminarlas utilizando awk para pasar los ID a docker rmi. Tenga en cuenta que Docker no proporciona estas utilidades y que estas no están necesariamente disponibles en todos los sistemas:*

*Enumerar:*
```
docker images -a |  grep "pattern"
```

*Eliminar:*
```
docker images -a | grep "pattern" | awk '{print $3}' | xargs docker rmi
```

**Eliminar todas las imágenes**
*Es posible enumerar todas las imágenes de Docker de un sistema añadiendo -a al comando docker images. Una vez que esté seguro de que desea eliminarlas por completo, puede añadir el indicador -q para pasar el ID de la imagen a docker rmi:*

*Enumerar:*
```
docker images -a
```

*Eliminar:*
```
docker rmi $(docker images -a -q)
```

## Eliminar contenedores

**Eliminar uno o más contenedores específicos**
*Utilice el comando docker ps con el indicador -a para localizar el nombre o la ID de los contenedores que desee eliminar.*

*Enumerar:*
```
docker ps -a
```

*Eliminar:*
```
docker rm ID_or_Name ID_or_Name
```

**Eliminar un contenedor al cerrarlo**
*Si al crear un contenedor sabe que no querrá conservarlo una vez que lo termine, puede ejecutar docker run --rm para eliminarlo automáticamente después de cerrarlo.*

*Ejecutar y eliminar:*
```
docker run --rm image_name
```

**Eliminar todos los contenedores terminados**
*Puede localizar contenedores utilizando docker ps -a y filtrarlos según su estado: “created”, “restarting”, “running”, “paused” o “exited”. A fin de revisar la lista de contenedores terminados, utilice el indicador -f para filtrar según el estado. Cuando haya verificado que desea eliminar esos contenedores, utilice -q para pasar los IDs al comando docker rm.*

*Enumerar:*
```
docker ps -a -f status=exited
```

*Eliminar:*
```
docker rm $(docker ps -a -f status=exited -q)
```

**Eliminar contenedores utilizando más de un filtro**
*Los filtros de Docker pueden combinarse repitiendo el indicador de filtro con un valor adicional. Esto da como resultado una lista de contenedores que cumplen cualquier condición. Por ejemplo, si desea eliminar todos los contenedores marcados como Created (un estado que se puede generar cuando ejecuta un contenedor con un comando no válido) o Exited, puede utilizar dos filtros:*

*Enumerar:*

```
docker ps -a -f status=exited -f status=created
```

*Eliminar:*
```
docker rm $(docker ps -a -f status=exited -f status=created -q)
```

**Eliminar contenedores según un patrón**
*Puede encontrar todos los contenedores que coinciden con un patrón utilizando la combinación de docker ps y grep. Cuando esté convencido de que tiene la lista que desea eliminar, podrá utilizar awk y xargs para proporcionar el ID a docker rmi. Tenga en cuenta que Docker no proporciona estas utilidades y que no están necesariamente disponibles en todos los sistemas:*

*Enumerar:*
```
docker ps -a |  grep "pattern”
```

*Eliminar:*
```
docker ps -a | grep "pattern" | awk '{print $3}' | xargs docker rmi
```

**Detener y eliminar todos los contenedores**
*Puede revisar los contenedores de su sistema con docker ps. Al añadir el indicador -a se mostrarán todos los contenedores. Cuando esté seguro de que desea eliminarlos, puede añadir el indicador -q para proporcionar los ID a los comandos docker stop y docker rm:*

*Enumerar:*
```
docker ps -a
```

*Eliminar:*
```
docker stop $(docker ps -a -q)
docker rm $(docker ps -a -q)
```

## Eliminar volúmenes

**Eliminar uno o más volúmenes específicos - Docker 1.9 y versiones posteriores**
*Utilice el comando docker volume ls para ubicar el nombre o los nombres de los volúmenes que desea eliminar. Luego, puede eliminar uno o más volúmenes con el comando docker volume rm:*

*Enumerar:*
```
docker volume ls
```

*Eliminar:*
```
docker volume rm volume_name volume_name
```

**Eliminar volúmenes pendientes: Docker 1.9 y versiones posteriores**
*Debido a que el punto de volúmenes debe existir independientemente de los contenedores, cuando se elimina un contenedor un volumen no se elimina automáticamente al mismo tiempo. Cuando un volumen existe y ya no está conectado a ningún contenedor, se denomina “volumen pendiente”. Para ubicarlos y confirmar que desea eliminarlos, puede utilizar el comando docker volume ls con un filtro a fin de limitar los resultados a volúmenes pendientes. Cuando esté conforme con la lista, puede eliminarlos con docker volume prune:*

*Enumerar:*
```
docker volume ls -f dangling=true
```

*Eliminar:*
```
docker volume prune
```

**Eliminar un contenedor y su volumen**
*Si creó un volumen sin nombre, puede eliminarlo al mismo tiempo que el contenedor utilizando el indicador -v. Tenga en cuenta que esto solo funciona con volúmenes sin nombre. Cuando el contenedor se elimina correctamente, se muestra su ID. Tenga en cuenta que no se hace referencia a la eliminación del volumen. Si no tiene nombre, se elimina silenciosamente del sistema. Si se nombra, permanece silenciosamente presente.*

*Eliminar:*
```
docker rm -v container_name
```