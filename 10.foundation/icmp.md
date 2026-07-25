---
title: ICMP
tags: [network, protocol]
created: 2026-07-23
status: draft
links:
  - https://datatracker.ietf.org/doc/html/rfc792
---

**Internet Control Message Protocol** (**ICMP**) — L3-протокол, дополняющий [IP](ip.md) передачей служебной информации. Применяет **ICMP-сообщения**, инкапсулируемые в IP-датаграммы.

## Строение сообщения (ICMPv4)
|Поле|Размер (байт)|Описание|
|----|-------------|--------|
|**Type**|1|>>>|
|**Code**|1|Уточняет тип сообщения. Перечень доступен [здесь](https://www.iana.org/assignments/icmp-parameters/icmp-parameters.xhtml)|
|**Checksum**|2|—|
|**Rest of Header**, Header Data|4|Хранит данные для некоторых типов сообщений|

### Type
|Значение|Наименование|Описание|
|--------|------------|--------|
|0|**Echo Reply**|—|
|3|**Destination Unreachable**|—|
|4|**Source Quench**|Перегрузка сети. Заменено[^1] [ECN](ip.md) и механизмами [TCP](tcp.md)|
|5|**Redirect**|Наличие более оптимального пути для IP-пакетов|
|8|**Echo Request**|—|
|9|**Router Advertisement**|Анонс маршрутизатора. Вытеснено [DHCP](dhcp.md)|
|10|**Router Solicitation**|Поиск маршрутизаторов. Вытеснено [DHCP](dhcp.md)|
|11|**Time Exceeded**|—|
|12|**Paremeter Problem**|Некорректный заголовок IP-датаграммы|
|13|**Timestamp Request**|Запрос синхронизации времени. Вытеснено [NTP](ntp.md)|
|14|**Timestamp Reply**|Синхронизация времени. Вытеснено [NTP](ntp.md)|

## Примечания
[^1]: https://datatracker.ietf.org/doc/html/rfc6633