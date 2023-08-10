# Mongo shell commands

## connect to instance
```
mongo --host $HOST --port $PORT
```

## connec to replica set
```
mongo "mongodb://$HOST:$PORT,$HOST:$PORT,$HOST:$PORT/?replicaSet=replA"

```

q0yTEfe7Nw1LBl9kIbLHO0Iw6AoI9UmcCaoFdiNQikuD8abHJWrMjsJ1CiElmbAuE3hNMifjMTFsBuyvOPpQjA==

## mongodump/mongorestore
```
mongodump --host 192.168.3.105:27017 --db ShoppingManager --out /home/lcepeda/Descargas
mongodump --host 192.168.3.105:27017 --db UserManager --out /home/lcepeda/Descargas
mongodump --host 192.168.3.105:27017 --db NotificationManager --out /home/lcepeda/Descargas
```

```
mongorestore --host abi-las-dev-brs-bolt-cosmosdb.mongo.cosmos.azure.com:10255 --authenticationDatabase admin -u abi-las-dev-brs-bolt-cosmosdb -p q0yTEfe7Nw1LBl9kIbLHO0Iw6AoI9UmcCaoFdiNQikuD8abHJWrMjsJ1CiElmbAuE3hNMifjMTFsBuyvOPpQjA== --db ShoppingManager --writeConcern="{w:0}" --ssl /home/lcepeda/Descargas/ShoppingManager

mongorestore --host abi-las-dev-brs-bolt-cosmosdb.mongo.cosmos.azure.com:10255 --authenticationDatabase admin -u abi-las-dev-brs-bolt-cosmosdb -p q0yTEfe7Nw1LBl9kIbLHO0Iw6AoI9UmcCaoFdiNQikuD8abHJWrMjsJ1CiElmbAuE3hNMifjMTFsBuyvOPpQjA== --db UserManager --writeConcern="{w:0}" --ssl /home/lcepeda/Descargas/UserManager

mongorestore --host abi-las-dev-brs-bolt-cosmosdb.mongo.cosmos.azure.com:10255 --authenticationDatabase admin -u abi-las-dev-brs-bolt-cosmosdb -p q0yTEfe7Nw1LBl9kIbLHO0Iw6AoI9UmcCaoFdiNQikuD8abHJWrMjsJ1CiElmbAuE3hNMifjMTFsBuyvOPpQjA== --db NotificationManager --writeConcern="{w:0}" --ssl /home/lcepeda/Descargas/NotificationManager
```
