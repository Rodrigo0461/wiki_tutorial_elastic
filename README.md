
Tutorial Consultas básicas ElasticSearch

1 - Consultar configuración y versión de elasticsearch instalda
```ruby
=> curl http://localhost:9200

{
  "name" : "destinity_master",
  "cluster_name" : "my_cluster",
  "cluster_uuid" : "vtfH83UqS8KSY4voQ1xRew",
  "version" : {
    "number" : "7.0.0",
    "build_flavor" : "default",
    "build_type" : "deb",
    "build_hash" : "76cefb0",
    "build_date" : "2018-11-13T12:10:18.050782Z",
    "build_snapshot" : false,
    "qualified" : "7.0.0-alpha1",
    "lucene_version" : "8.0.0",
    "minimum_wire_compatibility_version" : "6.6.0",
    "minimum_index_compatibility_version" : "6.0.0-beta1"
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
            "number_of_shards" : 2,
            "number_of_replicas" : 2
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




