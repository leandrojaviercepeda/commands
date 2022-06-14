# Mongo shell commands

## connect to instance
```
mongo --host $HOST --port $PORT
```

## connec to replica set
```
mongo "mongodb://$HOST:$PORT,$HOST:$PORT,$HOST:$PORT/?replicaSet=replA"

```

## export collection from database
```
mongoexport --host="mongodb0.example.com" --port=27017 --collection=collection_name --db=db_name --out=movies.json [additional options]
```

## import databases
