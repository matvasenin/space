---
title: Ethernet
tags: [network, protocol]
created: 2026-07-22
updated: 2026-07-22
status: draft
links:
  - https://www.ieee802.org/3/
  - https://standards.ieee.org/develop/regauth/ethertype/eth.txt
---

Ethernet — доминирующая технология проводных локальных (LAN) и городских (MAN) сетей, осуществляющая **пакетную передачу кадров**.

## Строение кадра (Ethernet II)
|Название|Размер (байт)|Описание|
|--------|-------------|--------|
|Преамбула — Preamble|7|Последовательность бит (`10101010...`), предшествующая началу кадра.|
|Разделитель начала кадра — Start Frame Delimeter, SFD|1|Последовательность бит (`10101011`), начинающая кадр.|
|MAC-адрес получателя — Destination MAC|6|—|
|MAC-адрес отправителя — Source MAC|6|—|
|EtherType, E-Type|2|Тип вышестоящего протокола.|
|Полезная нагрузка — Payload|46-1500|Данные вышестоящего протокола.|
|Контрольная сумма — Frame Check Sequence, FCS|4|—|