# filebeat-postfix

## Description

This is filebeat ingest pipeline for parsing postfix logs with template and siem rules.

Here you will find 3 files:
- Ingest Pipeline
- Component Template
- SIEM Rules

I've used parsing for logstash available here https://github.com/whyscream/postfix-grok-patterns.

IMHO ingest pipelines have some benefits:
- it can be loaded without installing logstash
- it has visual editor
- it has sumulation

## Load files to Elastic

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

## Test ingest pipeline

To test ingest pipeline you can use Dev Tool Console:

```
POST /_ingest/pipeline/filebeat-8.8.0-postfix-log-pipeline/_simulate
{
  "docs": [
    {
      "_source": {
        "@timestamp": "2023-03-20T11:39:52.178Z",
        "message" : "Mar 24 13:58:01 mailsrv postfix/smtpd[25469]: NOQUEUE: reject: RCPT from 061238241086.static.ctinets.com[61.238.241.86]: 550 5.12.345 <user@example.com>: Recipient address rejected: Some error message; from=<wumt5@cchfdc.com> to=<user@example.com> proto=ESMTP helo=<ecsolved.com>"
      }
    }
  ]
}
```

## Details

Full module and test files available [here](https://github.com/leweafan/beats/tree/postfix/filebeat/module/postfix)

In contrast to Logstash ingest pipeline can't use reusable patterns until it loaded to Elasticsearch by developers. 
So may be in future this module will be improved.

In contrast to Logstash postfix patterns I've tried to use ECS fields.

Unfortunately I haven't been able to use fields email.from.address and email.to.address instead of postfix.var.from & postfix.var.to.

