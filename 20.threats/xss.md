---
title: Cross-Site Scripting (XSS)
tags: [category, category]
created: 2026-07-26
status: draft
links:
  - https://cwe.mitre.org/data/definitions/79.html
  - https://emb3d.mitre.org/threats/TID-319.html
related: —
---

**Межсайтовый скриптинг** (**Cross-Site Scripting**, **XSS**) — это уязвимость веб-приложения, позволяющая атакующему **выполнять произвольный JS-код** в клиентском браузере от лица **доверенного веб-сайта**.

**Контекстом атаки** могут выступать:
- Тело HTML-тега:
```html
<!-- Целевой элемент -->
<p>...</p>
<!-- Payload — дочерний элемент -->
<script>print()</script>
<img src=x onerror=print()>
<svg onload=print()>
```
- Текстовый HTML-атрибут:
```html
<!-- Целевой элемент -->
<input value="...">
<!-- Payload — закрытие тега -->
<input value=""><script>print()</script>"
```
- Ссылочный HTML-атрибут:
```html
<!-- Целевой элемент -->
<a href="..." />
<!-- Payload — псевдо-URL -->
<a href="javascript:print()" />
```
- Обработчик события:
```html
<!-- Целевой элемент -->
<button onclick="fn('...')" />
<!-- Payload — закрытие функции -->
<button onclick="fn(''); print(); //')"
```

> [!NOTE]
> Ранее в качестве PoC для XSS использовалась функция `alert()`, но с выпуском **Chrome 92** (20 июля 2021) данная возможность была **закрыта** для междоменных `<iframe>`. Альтернативой является функция `print()`, вызывающая системный диалог печати веб-страницы. 

## Разновидности

### Отражённые
Возникают при небезопасной подстановке данных из HTTP-запроса (query-параметры, POST-тело) сразу в HTML-ответ.

### Хранимые
Возникают при небезопасной подстановке хранимых данных в HTML-ответ.

### Основанные на DOM
Возникают при небезопасной подстановке данных на клиентской стороне с помощью JavaScript. Обычно приводят к измененям в DOM, от чего и получили своё название.

## Предотвращение

### Экранирование содержимого
Метод борьбы, реализуемый путём замены опасных символов на **сущности** (**entities**):
- `&` — `&amp;`
- `<` — `&lt;`
- `>` — `&gt;`

#### Python
```python
import html
# Параметр quote отвечает за экранирование кавычек. 
safe_content = html.escape(unsafe_content, quote = True)
```

#### Go
Ручное:
```go
import "html"
safeContent := html.EscapeString(unsafeContent)
```
Автоматическое, основанное на шаблонах:
```go
import (
  "html/template"
  "net/http"
)
func handler(w http.ResponseWriter, r *http.Request) {
  tmpl := template.Must(template.New("page").Parse(`<p>{{.Input}}</p>`))
  tmpl.Execute(w, struct{ Input string }{Input: r.FormValue("input")})
}
```
> [!NOTE]
> При использовании шаблонов (`html/template`) экранирование адаптируется к контексту атаки.

#### PHP
```php
<?php
// Если кавычки стоит оставить, необходимо убрать ENV_QUOTES.
$safeContent = htmlspecialchars($unsafeContent, ENV_QUOTES | ENV_HTML5, "UTF-8");
?>
```
