# filebeat-exchange

## Description

This is filebeat ingest pipeline for parsing exchange logs with template and dashboard.

## Fields Mappins:

microsoft.exchange.client_ip -> source.ip
microsoft.exchange.server_ip -> destination.ip
microsoft.exchange.original_client_ip -> client.ip
microsoft.exchange.original_server_ip -> server.ip

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
