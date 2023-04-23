# Filebeat modules and ingest pipelines

To protect our infrastructure I have analyzed our SW/HW logs and Elastic SIEM patterns and found that a lot of authentication messages patterns missing in filebeat tests and messages not parsed and not categorized appropriately that's why Elastic SIEM skips these events.

Below listed modules I have used and checked does it have event.category authentication.

| Event module  | Event dataset | Event category = Authentication | Issue | PR |
| ------------- | ------------- | ------------------------------- | ----- | -- |
| Checkpoint | checkpoint.firewall | OK |
| Cisco | cisco.asa | Missing |
| Elasticsearch | elasticsearch.server |  Missing | [Issue](https://github.com/elastic/beats/issues/32249) |
| Fortinet | fortinet.firewall | Missing |
| Fortinet | fortinet.fortimanager | Missing | [Issue1](https://github.com/elastic/beats/issues/34023) [Issue2](https://github.com/elastic/beats/issues/35176)|
| IIS | iis.access | N/A |
| IIS | iis.error | N/A |
| Juniper	| juniper.junos |	Missing |
| Kafka |	kafka.log | PR - in progress | [Issue](https://github.com/elastic/beats/issues/32229) | [PR - in progress](https://github.com/elastic/beats/pull/34683) |
| Mongodb |	mongodb.log | PR - in progress | [Issue](https://github.com/elastic/beats/issues/32248) | [PR - in progress](https://github.com/elastic/beats/pull/34731) |
| MSSQL |	mssql.log	| Missing |
| MySQL | mysql.error	| PR accepted | [Issue](https://github.com/elastic/beats/issues/32231) | [PR accepted](https://github.com/elastic/beats/pull/34810) |
| MySQL |	mysql.slowlog	| N/A |
| Netflow	| netflow.log	| N/A |
| Nginx	| nginx.access| N/A |
| Nginx	| nginx.error	| PR - in progress | [Issue](https://github.com/elastic/beats/issues/32157) | [PR - in progress](https://github.com/elastic/beats/pull/34704) |
| Oracle | oracle.database_audit | PR - in progress | [Issue](https://github.com/elastic/beats/issues/30975) |[PR - in progress](https://github.com/elastic/beats/pull/35127) |
| Postgresql |postgresql.log	| PR - in progress | [Issue](https://github.com/elastic/beats/issues/32228) | [PR - in progress](https://github.com/elastic/beats/pull/34744) |
| Rabbitmq	| rabbitmq.log| OK | [Issue](https://github.com/elastic/beats/issues/32255) |
| Redis	| redis.log |	N/A |
| Squid	| squid.log	| ? |
| System | system.auth |  Some patterns missing | [Issue](https://github.com/elastic/beats/issues/35044) |
| System | system.syslog | N/A |

Filebeat modules which I plan to create from existing logstash patterns:

| Module | Status | Comment |
| -------| ------ | ------- |
| ACS |
| Atlassian Confluence | | There is elastic integration |
| Atlassian Jira | | There is elastic integration |
| Authelia|
| Brocade | 
| ESET |
| Gitlab |
| HP 3par |
| HP 3par-vsp |
| HP BladeSwitch |
| HP ILO |
| HP MSA |
| Microsoft Exchange | [PR - in progress](https://github.com/elastic/beats/pull/35004) |
| Mikrotik |
| Multifactor |
| Nemesida |
| Netapp |
| Netgear |
| Netscaler |
| Nextcloud |
| Nexus |
| Oracle alert.log dataset | [Issue](https://github.com/elastic/beats/issues/34056) |
| Pleasant Password Server |
| Postfix | [PR - in progress](https://github.com/elastic/beats/pull/34980) |
| Unify |
| VMware ESXi |
| VMware vCenter |
| VMware NSX-V |
| VMware vROPs |
| Windows Firewall |
| Other | | add later |
