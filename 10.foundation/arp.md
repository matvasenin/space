---
title: ARP
tags: [network, protocol]
created: 2026-07-22
status: draft
links:
  - https://datatracker.ietf.org/doc/html/rfc826
  - https://www.iana.org/assignments/arp-parameters/arp-parameters.xhtml
---

**Address Resolution Protocol** (**ARP**) — L2.5-протокол, позволяющий разрешать логический IP-адрес в физический MAC-адрес.

Протокол хранит в памяти специальную **ARP-таблицу**:
```
192.168.1.1	08:00:19:00:2F:C6
192.168.1.2	08:00:5A:22:A7:22
192.168.1.3	08:00:20:99:AC:52
```
Если значение отсутствует в таблице, отправляется широковещательное **ARP-сообщение**.

## Строение сообщения
|Поле|Размер (байт)|Описание|
|----|-------------|--------|
|**Физический тип** — Hardware Type, HTYPE|2|Идентификатор канального протокола|
|**Логический тип** — Protocol Type, PTYPE|2|Идентификатор ([EtherType](ethernet.md)) сетевого протокола|
|**Физическая длина** — Hardware Length, HLEN|1|Длина физического адреса в байтах|
|**Логическая длина** — Protocol Length, PLEN|1|Длина логического адреса в байтах|
|**Операция** — Operation, OpCode|2|>>>|
|**Физический адрес отправителя** — Sender Hardware Address, SHA|4|—|
|**Логический адрес отправителя** — Sender Protocol Address, SPA|4|—|
|**Физический адрес получателя** — Target Hardware Address, THA|4|—|
|**Логический адрес получателя** — Target Protocol Address, TPA|4|—|

### Операция
|Значение|Наименование|Описание|
|--------|------------|--------|
|1|ARP Request|Who has **X.X.X.X**? Tell Y.Y.Y.Y|
|2|ARP Response|X.X.X.X is at **00:0A:0B:0C:0D:0E**|