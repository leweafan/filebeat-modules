# Filebeat modules and ingest pipelines

To protect our infrastructure I have analyzed our SW/HW logs and Elastic SIEM patterns and found that a lot of authentication messages patterns missing in filebeat tests and messages not parsed and not categorized appropriately that's why Elastic SIEM skips these events.

Below modules I have used and checked does it have event.category authentication.

| Event module  | Event dataset | Event category = Authentication | Issue | PR |
| ------------- | ------------- | ------------------------------- | ----- | -- |
| Checkpoint | checkpoint.firewall | OK |
| Cisco | cisco.asa | Missing |
| Elasticsearch | elasticsearch.server |  Missing | [Issue](https://github.com/elastic/beats/issues/32249) |
| Fortinet | fortinet.firewall | Missing |
| Fortinet | fortinet.fortimanager | Missing | [Issue](https://github.com/elastic/beats/issues/34023) |
| IIS | iis.access | N/A |
| IIS | iis.error | N/A |
| Juniper	| juniper.junos |	Missing |
| Kafka |	kafka.log | PR - in progress | [Issue](https://github.com/elastic/beats/issues/32229) | [PR - in progress](https://github.com/elastic/beats/pull/34683) |
| Mongodb |	mongodb.log | PR - in progress | [Issue](https://github.com/elastic/beats/issues/32248) | [PR - in progress](https://github.com/elastic/beats/pull/34731) |
| MSSQL |	mssql.log	| Missing |
| MySQL | mysql.error	| PR accepted | [Issue](https://github.com/elastic/beats/issues/32231) | [PR accepted](https://github.com/elastic/beats/pull/34810) |
| MySQL |	mysql.slowlog	| N/A |
| netflow	| netflow.log	| N/A |
| nginx	| nginx.access| N/A |
| nginx	| nginx.error	| PR - in progress | [Issue](https://github.com/elastic/beats/issues/32157) | [PR - in progress](https://github.com/elastic/beats/pull/34704) |
| Oracle | oracle.database_audit | PR - in progress | [Issue](https://github.com/elastic/beats/issues/30975) |[PR - in progress](https://github.com/elastic/beats/pull/35127) |
| Postgresql |postgresql.log	| PR - in progress | [Issue](https://github.com/elastic/beats/issues/32228) | [PR - in progress](https://github.com/elastic/beats/pull/34744) |
| Rabbitmq	| rabbitmq.log| OK | [Issue](https://github.com/elastic/beats/issues/32255) |
| Redis	| redis.log |	N/A |
| Squid	| squid.log	| ? |
| System | system.auth |  Some patterns missing | [Issue](https://github.com/elastic/beats/issues/35044) |
| System | system.syslog | N/A |

Filebeat modules which I plan to create 
| Module | Status |
| ------------- | ------------- | 
| Microsoft Exchange | [PR - in progress](https://github.com/elastic/beats/pull/35004) |
| Mikrotik | |
| Netscaler	| |
| Oracle alert.log dataset | [Issue](https://github.com/elastic/beats/issues/34056) |
| Postfix | [PR - in progress](https://github.com/elastic/beats/pull/34980) |
