# Elasticsearch Ingest Pipeline for Mikrotik with ECS (filebeat-mikrotik)

## Description

This is filebeat ingest pipeline for parsing mikrotik logs.

## Load files to Elastic

You can use curl to upload ingest pipeline and component template:

```
curl -X PUT -H "Content-Type: application/json" -k 'https://elasticsearch:9200/_ingest/pipeline/filebeat-8.6.2-mikrotik-log-pipeline' -d @/path/to/file/filebeat-8.6.2-mikrotik-log-pipeline
```

Also you can use Kibana Dev Tools to upload ingest pipeline and component template:

```
PUT _ingest/pipeline/filebeat-8.6.2-mikrotik-log-pipeline
{content_from_filebeat-8.6.2-mikrotik-log-pipeline}
```

## Test ingest pipeline

To test ingest pipeline you can use Dev Tool Console:

```
POST /_ingest/pipeline/filebeat-8.6.2-mikrotik-log-pipeline/_simulate
{
  "docs": [
    {
      "_source": {
        "@timestamp": "2023-03-20T11:39:52.178Z",
        "message" : "<190>Apr 28 21:54:41 testhost ZABIL DROP FWD forward: in:vrrp-WAN out:NIC1-INET, src-mac 94:f7:ad:19:87:9c, proto TCP (ACK,FIN), 65.49.20.78:443->10.219.109.202:55153, NAT 65.49.20.78:443->(91.228.165.160:55153->10.219.109.202:55153), len 40"
      }
    }
  ]
}
```

## Details

Full module and test files available [here](https://github.com/leweafan/beats/tree/mikrotik/filebeat/module/mikrotik)
