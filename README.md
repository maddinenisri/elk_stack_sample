#ELK Stack Docker containers

##Commands

###Start all containers
####Need to increase host system docker memory allocation from 2GB to higher.

```{engine='bash'}
docker-compose up -d
```

###Find documents from elastic search usign curl command

```{engine='bash'}
curl localhost:9200/logstash-*/_search?pretty=true
```

###Publish messages using NC command

```{engine='bash'}
nc localhost 5000 < sourcelogs/test.log
```
