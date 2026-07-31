---
title: Ethernet
tags: [network, protocol]
created: 2026-07-22
status: draft
links:
  - https://www.ieee802.org/3
related: —
---

**Ethernet** (II) — это семейство L1-технологий и L2-протоколов построения проводных LAN и MAN. 

На канальном уровне применяет **Ethernet-кадры**.

## Адресация

### Формат адреса

Для идентификации аппартных интерфейсов в Ethernet-сетях применяются 48-битные **MAC-адреса**: `00:1A:2B:3C:4D:5E`.

MAC-адрес подразделяется на две равные части:
- **OUI**, Organizationally Unique Identifier — производитель
- **Device ID** — конкретное устройство

MAС-адреса хранятся в ROM-памяти (**BIA**, Burned-In Address), но современные ОС позволяют позволяют его подменять (**MAC Spoofing**).

### Виды адресов

|Вид|Адрес|
|---|-----|
|**Unicast**|`00:1A:2B:8A:9C:55`|
|**Broadcast**|`FF:FF:FF:FF:FF:FF`|
|**Multicast**|`01:00:5E:XX:XX:XX`|

## Строение кадра

|Название|Размер (байт)|Описание|
|--------|-------------|--------|
|**Preamble**|7|Последовательность бит (`10101010...`), предшествующая началу кадра|
|**Start Frame Delimeter**, SFD|1|Последовательность бит (`10101011`), начинающая кадр|
|**Destination MAC**|6|—|
|**Source MAC**|6|—|
|**EtherType**[^1], E-Type|2|Используемый L3-протокол|
|**Полезная нагрузка** — Payload|46-1500|Данные L3-протокола|
|**Frame Check Sequence**, FCS|4|Контрольная сумма|

## Примечания

[^1]: https://standards.ieee.org/develop/regauth/ethertype/eth.txt