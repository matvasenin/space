---
title: Ethernet
tags: [network, protocol]
created: 2026-07-22
status: draft
links:
  - https://www.ieee802.org/3
related: —
---

**Ethernet** (II) — это доминирующая технология проводных локальных (LAN) и городских (MAN) сетей, осуществляющая **пакетную передачу кадров**.

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