
Tutorial Consultas básicas ElasticSearch

Instalar elasticsearch

```ruby
wget https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-6.4.0.deb
wget https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-6.4.0.deb.sha512
shasum -a 512 -c elasticsearch-6.4.0.deb.sha512 
sudo dpkg -i elasticsearch-6.4.0.deb
```

Principales metodos de Elasticsearch
```ruby
 Post API
 Get API
 Delete API
 Update API
```


1 - Consultar configuración y versión de elasticsearch instalda
```ruby
=> curl http://localhost:9200
{
  "name" : "I5pYMV1",
  "cluster_name" : "elasticsearch",
  "cluster_uuid" : "NFdgjyA0REClV8Y8qI4ydA",
  "version" : {
    "number" : "6.4.0",
    "build_flavor" : "default",
    "build_type" : "deb",
    "build_hash" : "595516e",
    "build_date" : "2018-08-17T23:18:47.308994Z",
    "build_snapshot" : false,
    "lucene_version" : "7.4.0",
    "minimum_wire_compatibility_version" : "5.6.0",
    "minimum_index_compatibility_version" : "5.0.0"
  },
  "tagline" : "You Know, for Search"
}

```

2. - Consultar status de cluster elasticsearch
```ruby
 ⇒  curl -XGET 'localhost:9200/_cluster/health?pretty'
{
  "cluster_name" : "elasticsearch-dev",
  "status" : "red",
  "timed_out" : false,
  "number_of_nodes" : 1,
  "number_of_data_nodes" : 1,
  "active_primary_shards" : 2,
  "active_shards" : 2,
  "relocating_shards" : 0,
  "initializing_shards" : 0,
  "unassigned_shards" : 7,
  "delayed_unassigned_shards" : 0,
  "number_of_pending_tasks" : 0,
  "number_of_in_flight_fetch" : 0,
  "task_max_waiting_in_queue_millis" : 0,
  "active_shards_percent_as_number" : 22.22222222222222
}
  
```
3. - Crear indice en elastic, por ejemplo crear indice de nombre test
```ruby
curl -XPUT   -H 'Content-Type: application/json'  'http://localhost:9200/test/' -d '{
    "settings" : {
        "index" : {
            "number_of_shards" : 1,
            "number_of_replicas" : 0
        }
    }
}'
```

4. - Consultar indices creados y disponibles
```ruby
curl 'http://localhost:9200/_cat/indices?v'
# output
#health status index uuid                   pri rep docs.count docs.deleted store.size pri.store.size
#red    open   test  n0n7yaH_Qa6EhhS2cnxIXA   3   2          0            0       522b           522b
```
5. - Busqueda por indice LOGGER / ELASTICSEARCH
 
 Busqueda por indice log
```ruby
 curl -XGET "http://localhost:9200/log/_search?pretty"
```
 
 





