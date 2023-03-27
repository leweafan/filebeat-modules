# filebeat-postfix
Filebeat postfix module

This is filebeat ingest pipeline for parsing postfix logs.

I've used parsing for logstash available here https://github.com/whyscream/postfix-grok-patterns.

You can use curl to upload ingest pipeline and component template:

```
curl -X PUT -H "Content-Type: application/json" -k 'https://elasticsearch:9200/_ingest/pipeline/filebeat-8.6.2-postfix-log-pipeline' -d @/path/to/file/filebeat-8.6.2-postfix-log-pipeline
curl -X PUT -H "Content-Type: application/json" -k 'https://elasticsearch:9200/_component_template/postfix-mapping' -d @/path/to/file/postfix-mapping.json
```

Also you can use Kibana Dev Tools to upload ingest pipeline and component template:

```
PUT _ingest/pipeline/filebeat-8.6.2-postfix-log-pipeline
{content_from_filebeat-8.6.2-postfix-log-pipeline}

PUT _component_template/postfix-mapping
{content_from_postfix-mapping.json}
```

## Details

Full module and test files available [here](https://github.com/leweafan/beats/tree/postfix/filebeat/module/postfix)

In contrast to Logstash ingest pipeline can't use reusable patterns until it loaded to Elasticsearch by developers. 
So may be in future this module will be improved.

In contrast to Logstash postfix patterns I've tried to use ECS fields.

Unfortunately I haven't been able to use fields email.from.address and email.to.address instead of postfix.var.from & postfix.var.to.

