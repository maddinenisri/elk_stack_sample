# ELK Stack Docker containers

## Commands

### Start all containers
#### Need to increase host system docker memory allocation from 2GB to higher.

```{engine='bash'}
docker-compose up -d
```

### Find documents from elastic search usign curl command

```{engine='bash'}
curl localhost:9200/logstash-*/_search?pretty=true
```

### Publish messages using NC command

```{engine='bash'}
nc localhost 5000 < sourcelogs/test.log
```

### Crearte Index and Upload template into Elastic Search

```
curl -XPUT http://localhost:9200/geo
curl -XPUT localhost:9200/geo/_mapping/place --data-binary @mapping_place.json
```

### Upload sample data

```
curl -XPOST http://localhost:9200/geo/place/ --data-binary @place_brisbane.json
curl -XPOST http://localhost:9200/geo/place/ --data-binary @place_sydney.json
curl -XPOST http://localhost:9200/geo/place/ --data-binary @place_melbourne.json
```

### Search Places

```
curl -s -XGET http://localhost:9200/geo/place/_search
```

### Search and Filter data

```
curl -s -XPOST http://localhost:9200/geo/place/_search --data-binary @query_distance_from_cairns.json
curl -s -XPOST http://localhost:9200/geo/place/_search --data-binary @query_distance_from_hobart.json
curl -s -XPOST http://localhost:9200/geo/place/_search --data-binary @query_distance_from_canberra.json
curl -s -XPOST http://localhost:9200/geo/place/_search --data-binary @query_distance_from_hobart_filter_1500km.json
```

### Reference:
#### https://github.com/rudijs/elasticsearch-geolocation-demo
#### http://www.sanjeevnandam.com/blog/logstash-convert-zipcodepostal-code-to-geo_point-latitudelongitude
