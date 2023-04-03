# filebeat-exchange

## Description

This is filebeat ingest pipeline for parsing exchange logs with template and dashboard.


## Load files to Elastic

You can use curl to upload ingest pipeline and component template:

```
curl -X PUT -H "Content-Type: application/json" -k 'https://elasticsearch:9200/_ingest/pipeline/filebeat-8.6.2-exchange-log-pipeline' -d @/path/to/file/filebeat-8.6.2-postfix-log-pipeline
curl -X PUT -H "Content-Type: application/json" -k 'https://elasticsearch:9200/_component_template/exchange-mapping' -d @/path/to/file/exchange-mapping.json
```

Also you can use Kibana Dev Tools to upload ingest pipeline and component template:

```
PUT _ingest/pipeline/filebeat-8.6.2-exchange-log-pipeline
{content_from_filebeat-8.6.2-exchange-log-pipeline}

PUT _component_template/exchange-mapping
{content_from_exchange-mapping.json}
```

## Test ingest pipeline

To test ingest pipeline you can use Dev Tool Console:

```
POST /_ingest/pipeline/filebeat-8.6.2-exchange-log-pipeline/_simulate
{
  "docs": [
    {
      "_source": {
        "@timestamp": "2023-03-20T11:39:52.178Z",
        "message" : "2023-03-28T10:54:18.804Z,,,,server1,/o=TEST/ou=Exchange Administrative Group (FYDIBOHF23SPDLT)/cn=Recipients/cn=usere339c092,,ROUTING,RESOLVE,27389006448778,<29634534.206435.1680000849959@test3.com>,066694bd-bf3b-497b-a1d3-08db2f7ac5dc,mail1@test.com,,27289,1,mail1@test.com,,SUBJECT-XXX,test@test.com,test@test.com,,Incoming,,,,S:DeliveryPriority=Normal;S:AccountForest=test.com,Email,a785cbe6-132d-48f6-9a37-08db2f7ac7d2,15.01.2507.023"
      }
    }
  ]
}
```

## Fields Mappins:

* microsoft.exchange.client_ip -> source.ip
* microsoft.exchange.server_ip -> destination.ip
* microsoft.exchange.original_client_ip -> client.ip
* microsoft.exchange.original_server_ip -> server.ip

## TODO

Fields mapping:
* microsoft.exchange.message_id -> email.message_id
* microsoft.exchange.message_subject -> email.subject
* microsoft.exchange.directionality -> email.direction
* microsoft.exchange.recipient_address -> email.to.address
* microsoft.exchange.sender_address -> email.from.address
* microsoft.exchange.sender_address -> email.sender.address
* microsoft.exchange.internal_message_id -> email.local_id
* microsoft.exchange.return_path -> email.reply_to.address
* email.cc.address
* email.bcc.address

## Details

Full module and test files available [here](https://github.com/leweafan/beats/tree/ms_exchange/filebeat/module/microsoft)
