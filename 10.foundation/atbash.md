---
title: Atbash Cipher
tags: [crypto, cipher]
created: 2026-08-02
status: draft
links: —
related: —
---

**Атбаш** (Atbash Cipher) — классический шифр перестановки, изначально применяемый на алфавите иврита.

## Принцип работы

Каждая буква исходного сообщения заменяется другой, имеющей противоположную позицию в алфавите.

## Реализация

### Python

```py
import string
alphabet = string.ascii_uppercase # "ABC...XYZ"

# Шифрование
def encode(message: str) -> str:
  output = ""
  for char in message:
    # Вычисление нового индекса
    idx = -1 * (alphabet.index(char) + 1)
    # Добавление буквы в шифротекст
    output += alphabet[idx]
  return output

# Расшифрование
def decode(ciphertext: str) -> str:
  return encode(ciphertext)

print(encode("HELLO")) # -> SVOOL
print(decode("SVOOL")) # -> HELLO
```