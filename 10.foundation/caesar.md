---
title: Caesar Cipher
tags: [crypto, cipher]
created: 2026-08-02
status: draft
links: —
related: —
---

**Шифр Цезаря** (Caesar Cipher) — классический [шифр](encryption.md) перестановки, названный в честь римского императора. Является частным случаем [аффинного шифра](affine-cipher.md).

## Принцип работы

Каждая буква исходного сообщения заменяется другой, имеющей сдвиг на $N$ позиций в алфавите.

## Реализация

### Python

```py
import string
alphabet = string.ascii_uppercase # "ABC...XYZ"

# Шифруем
def encode(message: str, shift: int) -> str:
  output = ""
  for char in message:
    # Делаем проверку на спец. символы (напр. "{")
    if char.upper() not in alphabet:
      output += char
      continue
    # Вычисляем индекс буквы в алфавите
    idx = (alphabet.index(char.upper()) + shift) % len(alphabet)
    # Сопоставляем регистры
    if char.islower():
      output += alphabet[idx].lower()
    else:
      output += alphabet[idx]
  return output

# Дешифруем
def decode(ciphertext: str, shift: int) -> str:
  return encode(ciphertext, len(alphabet) - shift)

print(encode("Hello", 3)) # -> Khoor
print(decode("Khoor", 3)) # -> Hello
```