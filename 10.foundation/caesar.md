---
title: Caesar Cipher
tags: [crypto, cipher]
created: 2026-08-02
status: draft
links: —
related: —
---

**Шифр Цезаря** (Caesar Cipher) — классический шифр перестановки, названный в честь римского императора.

## Принцип работы

Каждая буква исходного сообщения заменяется другой, имеющей сдвиг на $N$ позиций в алфавите.

## Реализация

### Python

```py
import string
alphabet = string.ascii_uppercase # "ABC...XYZ"

# Шифрование
def encode(message: str, shift: int) -> str:
  output = ""
  for char in message:
    # Вычисление нового индекса
    idx = (alphabet.index(char.upper()) + shift) % len(alphabet)
    # Добавление буквы в шифротекст
    output += alphabet[idx]
  return output

# Расшифрование
def decode(ciphertext: str, shift: int) -> str:
  return encode(ciphertext, len(alphabet) - shift)

print(encode("HELLO", 3)) # --> KHOOR
print(decode("KHOOR", 3)) # --> HELLO
```