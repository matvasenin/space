---
title: Сетевая модель TCP/IP
tags: [network, model]
created: 2026-07-23
updated: 2026-07-23
status: draft
links:
  - https://datatracker.ietf.org/doc/html/rfc1122
  - https://datatracker.ietf.org/doc/html/rfc1123
---

**TCP/IP** (ранее **DoD**, Departure of Defense) — сетевая модель, превзошедшая [OSI](osi.md) на практике.

## Уровни
|Название|Тип данных (PDU)|Функции|Примеры|
|--------|----------------|-------|-------|
|4. **Прикладной** — Application|Данные|Обеспечение взаимодействия приложений|DHCP, DNS, FTP, HTTP, LDAP, SNMP, SMTP, IMAP, BGP|
|3. **Транспортный** — Transport|Сегмент / датаграмма|Доставка и контроль передачи данных|TCP, UDP, QUIC|
|2. **Сетевой** — Network|Пакет|Логическая адресация, маршрутизация|IP, ARP, ICMP, OSPF, IS-IS|
|1. **Канальный** — Link|Кадр (фрейм)|Физическая адресация|Ethernet, MAC|