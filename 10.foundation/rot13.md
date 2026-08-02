---
title: ROT13
tags: [crypto, cipher]
created: 2026-08-02
status: draft
links: —
related: —
---

**ROT13** — частный случай [шифра Цезаря](caesar.md).

Не требует ключа — его сдвиг всегда равен 13.

## Реализация

### Python

```py
import codecs

# Кодирование
data = "Hello"
encoded = codecs.encode(data, "rot_13") # --> Uryyb

# Декодирование
decoded = codecs.decode(data, "rot_13") # --> Hello
```