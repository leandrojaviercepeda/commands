# Install docker and docker-compose

## Install docker

1. Cambiar a usuario root
```
sudo su
```

2. Actualizar paquetes
```
apt-get update
```

3. Instalar dependencias
```
apt-get install \
ca-certificates \
curl \
gnupg \
lsb-release
```

4. Descargar clave publica
```
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
```

5. Agregar al path
```
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

6. Actualizar paquetes
```
apt-get update
```

## Instalar docker-compose

1. Instalar dependencias
```
apt-get install docker-ce docker-ce-cli containerd.io
```

1. Instalar docker-compose
```
apt install docker-compose
```
