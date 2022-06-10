# Docker Compose Commands

## Iniciar docker compose
*Inicie la pila de aplicaciones con el docker-compose upcomando. Agregaremos la -dbandera para ejecutar todo en segundo plano.*
```
docker-compose up -d
```

## Ver registros
*La -fbandera "sigue" el registro, por lo que le dará una salida en vivo a medida que se genera.*
```
docker-compose logs -f
```

*Si desea ver los registros de un servicio específico, puede agregar el nombre del servicio al final del comando de registros*
```
docker-compose logs -f <name-service>
```

## Destruir docker compose
**Advertencia**
*Eliminación de volúmenes: De forma predeterminada, los volúmenes con nombre en su archivo de redacción NO se eliminan cuando se ejecuta docker-compose down. Si desea eliminar los volúmenes, deberá agregar la --volumes bandera.*
```
docker-compose down
```
