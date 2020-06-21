# techmongo

```
cd /usr/local/mongodb/bin/

mkdir -p node1/db
mkdir -p node2/db
mkdir -p node3/db

mongod -port 27017 -dbpath node1/db -replSet firstReplSet
mongod -port 27018 -dbpath node2/db -replSet firstReplSet
mongod -port 27019 -dbpath node3/db -replSet firstReplSet
```
mongo shell: 

```
mongo -port 27017
> db.isMaster();
> rs.initiate(); joins replicaset - ONLY in primary or first started node
>rs.add("127.0.0.1:27018")
>rs.add("127.0.0.1:27019")
>rs.conf(); 
```
> NOTE: localhost vs 127.0.0.1

verify:

```
cd /usr/local/mongodb/bin/
mongo -port 27018
```

```
cd /usr/local/mongodb/bin/
mongo -port 27019
```

one is primary and other 2 are secondary


