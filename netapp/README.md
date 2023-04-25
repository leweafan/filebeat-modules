# Elasticsearch Ingest Pipeline for Netapp with ECS (filebeat-netapp)

## Description

This is filebeat ingest pipeline for parsing netapp audit logs.
## Load files to Elastic

You can use curl to upload ingest pipeline and component template:

```
curl -X PUT -H "Content-Type: application/json" -k 'https://elasticsearch:9200/_ingest/pipeline/filebeat-8.6.2-netapp-audit-pipeline' -d @/path/to/file/filebeat-8.6.2-netapp-audit-pipeline
```

Also you can use Kibana Dev Tools to upload ingest pipeline and component template:

```
PUT _ingest/pipeline/filebeat-8.6.2-netapp-audit-pipeline
{content_from_filebeat-8.6.2-netapp-audit-pipeline}
```

## Test ingest pipeline

To test ingest pipeline you can use Dev Tool Console:

```
POST /_ingest/pipeline/filebeat-8.6.2-netapp-audit-pipeline/_simulate
{
  "docs": [
    {
      "_source": {
        "@timestamp": "2023-03-20T11:39:52.178Z",
        "message" : "Sat Apr 22 2023 20:53:25 +03:00 [kern_audit:info:2094] 8203e814000ad8c8 :: FAS2750_CLUSTER:ssh :: 10.10.10.10:50700 :: FAS2750_CLUSTER:sherlock :: Login Attempt :: Error: User sherlock doesn't exist."
      }
    }
  ]
}
```

## Details

Full module and test files available [here](https://github.com/leweafan/beats/tree/netapp/filebeat/module/netapp)
