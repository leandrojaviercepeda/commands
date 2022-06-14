# Comandos utiles de Linux

## Almacenamiento

**Almacenamiento de un directorio**
*Para encontrar el tamaño de un directorio específico diferente de su directorio de trabajo actual . El ducomando le permite especificar un directorio para examinar:*

```
du -h /var
```

**Almacenamiento de los n directorios mas grandes dado un directorio raiz**
*Reemplazar '*' por el directorio raiz que se quiere analizar, si se quiere cambiar la cantidad de directorios a obtener, ej: du -hs /var/ | sort -nr | head -5*

```
du -hs * | sort -nr | head -5
```

**Lipiar el contenido de un archivo**
```
echo "" > <file_name>
```

**Limpiar todos los archivos con *.<extension> de un directorio**
```
for file in /<parent>/<child>/*.*
do
  cat /dev/null > $file
done
```

**Buscar archivos**
```
find / -type f -name "*.extension"
```

## Log en systemd
*Los logs en systemd se denominan journals. Los journals no se almacenan en formato de texto plano en el disco, como sí lo hacían en SysV Init, sino que lo hacen en formato binario y pueden leerse e interpretarse mediante las utilidades de systemd, por ejemplo, journalctl.*

**Vaciar los logs por temporización**
*Por ejemplo, podemos vaciar los logs por temporización, eliminando todas las entradas en journal cuya antigüedad sea mayor a n días:*
```
journalctl --vacuum-time=<days_amount>d
```

**Vaciar los logs por tamaño**
*Por ejemplo, podemos vaciar los logs por temporización, eliminando todas las entradas en journal cuyo tamaño sea mayor a n:*
```
journalctl --vacuum-size=<size_amount>M
```

## Configurar journalctl

**Configurar el daemon de registros para que almacene como máximo un tamaño determinado**
*Para ello podemos editar el archivo /etc/systemd/journald.conf y agregar (o modificar) esta línea: "SystemMaxUse=<size_amount>M"*
```
sudo nano /etc/systemd/journald.conf
```

*Luego reiniciar el daemon de logs:*
```
sudo systemctl restart systemd-journald
```