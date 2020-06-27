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

```
cd /usr/local/mongodb/bin/
mongo -port 27018
>rs.slaveOk(); - to be run on every connection?
```

```
cd /usr/local/mongodb/bin/
mongo -port 27019
>rs.slaveOk(); - to be run on every connection?
```

one is primary and other two are secondary


on primary:

```
use twoDB
db.twoColl.insert({"name":"onetest"});
db.twoColl.insert({"name":"twotest"});
db.twoColl.insert({"name":"threetest"});
db.twoColl.find();
```

on secondary:

```
use twoDB
db.twoColl.find();
```
