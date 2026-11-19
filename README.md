# Практична робота № 1

**Дисципліна:** Основи побудови інформаційних систем та мереж

**Тема:** Спостереження за процесом звернення до вебресурсу. Побудова власної моделі рівнів взаємодії

| | |
|---|---|
| **Прізвище, ім'я** |Кожухар Світлана|
| **Група** |21|
| **Номер варіанта** |6|
| **Домен варіанта** |ietf.org|
| **Середовище виконання** | Windows  |
| **Версія curl** |curl 8.16.0 (Windows) libcurl/8.16.0 Schannel zlib/1.3.1 WinIDN|
| **Дата виконання** |18-19.11.2026 |

---

## Частина A. Збір експериментальних даних

### A.1. Запит із діагностичним виводом

**Команда:** 

```
curl.exe -v https://ietf.org
```

**Вивід:**
```
* Host ietf.org:443 was resolved.
* IPv6: (none)
* IPv4: 104.16.44.99, 104.16.45.99
*   Trying 104.16.44.99:443...
* schannel: disabled automatic use of client certificate
* ALPN: curl offers http/1.1
* ALPN: server accepted http/1.1
* Established connection to ietf.org (104.16.44.99 port 443) from 192.168.0.102 port 57586
* using HTTP/1.x
> GET / HTTP/1.1
> Host: ietf.org
> User-Agent: curl/8.16.0
> Accept: */*
>
* Request completely sent off
* schannel: remote party requests renegotiation
* schannel: renegotiating SSL/TLS connection
* schannel: SSL/TLS connection renegotiated
< HTTP/1.1 301 Moved Permanently
< Date: Wed, 18 Nov 2026 11:51:50 GMT
< Content-Type: text/html; charset=UTF-8
< Transfer-Encoding: chunked
< Connection: keep-alive
< Location: https://www.ietf.org/
< set-cookie: __cf_bm=.s_N_RMauvG3mlAKXf8kl6hlBjVqn8ujy3kXvynncMg-1795002710.0398312-1.0.1.1-MlNW9r2bh66jWpkDO.t00wafqNYUW0p14KUOb1VwkRGmYqUvK_5wMHlgd5Bq16d0UG6hDApNd_HgfFL.w8jJWYb2BIcdmBEsDyOzTXO7kbKsPpiMSVz8xuXfO40xcXu7; HttpOnly; SameSite=None; Partitioned; Secure; Path=/; Domain=ietf.org; Expires=Wed, 18 Nov 2026 12:21:50 GMT
< Server: cloudflare
< CF-RAY: a5c6c3f9b8963bbd-WAW
< alt-svc: h3=":443"; ma=86400
<
<html>
<head><title>301 Moved Permanently</title></head>
<body>
<center><h1>301 Moved Permanently</h1></center>
<hr><center>cloudflare</center>
</body>
</html>
* Connection #0 to host ietf.org:443 left intact

```

---

### A.2. Запит без захисту з'єднання

**Команда:**

```
curl.exe -v http://neverssl.com
```

**Вивід:**

```
* Host neverssl.com:80 was resolved.
* IPv6: 2600:1f13:37c:1400:ba21:7165:5fc7:736e
* IPv4: 34.223.124.45
*   Trying [2600:1f13:37c:1400:ba21:7165:5fc7:736e]:80...
*   Trying 34.223.124.45:80...
* Established connection to neverssl.com (34.223.124.45 port 80) from 192.168.1.117 port 53843
* using HTTP/1.x
> GET / HTTP/1.1
> Host: neverssl.com
> User-Agent: curl/8.16.0
> Accept: */*
>
* Request completely sent off
< HTTP/1.1 200 OK
< Date: Thu, 19 Nov 2026 06:55:29 GMT
< Server: Apache/2.4.68 ()
< Upgrade: h2,h2c
< Connection: Upgrade
< Last-Modified: Wed, 29 Jun 2022 00:23:33 GMT
< ETag: "f79-5e28b29d38e93"
< Accept-Ranges: bytes
< Content-Length: 3961
< Vary: Accept-Encoding
< Content-Type: text/html; charset=UTF-8
<
<html>
        <head>
                <title>NeverSSL - Connecting ... </title>
                <style>
                body {
                        font-family: Montserrat, helvetica, arial, sans-serif;
                        font-size: 16x;
                        color: #444444;
                        margin: 0;
                }
                h2 {
                        font-weight: 700;
                        font-size: 1.6em;
                        margin-top: 30px;
                }
                p {
                        line-height: 1.6em;
                }
                .container {
                        max-width: 650px;
                        margin: 20px auto 20px auto;
                        padding-left: 15px;
                        padding-right: 15px
                }
                .header {
                        background-color: #42C0FD;
                        color: #FFFFFF;
                        padding: 10px 0 10px 0;
                        font-size: 2.2em;
                }
                .notice {
                        background-color: red;
                        color: white;
                        padding: 10px 0 10px 0;
                        font-size: 1.25em;
                        animation: flash 4s infinite;
                }
                @keyframes flash {
                0% {
                        background-color: red;
                }
                50% {
                        background-color: #AA0000;
                }
                0% {
                        background-color: red;
                }
                }
                <!-- CSS from Mark Webster https://gist.github.com/markcwebster/9bdf30655cdd5279bad13993ac87c85d -->
                </style>

                <script>
                        var adjectives = [ 'cool' , 'calm' , 'relaxed', 'soothing', 'serene', 'slow',
                                                     'beautiful', 'wonderful', 'wonderous', 'fun', 'good',
                                                     'glowing', 'inner', 'grand', 'majestic', 'astounding',
                                                     'fine', 'splendid', 'transcendent', 'sublime', 'whole',
                                                     'unique', 'old', 'young', 'fresh', 'clear', 'shiny',
                                                     'shining', 'lush', 'quiet', 'bright', 'silver' ];

                        var nouns =       [ 'day', 'dawn', 'peace', 'smile', 'love', 'zen', 'laugh',
                                                     'yawn', 'poem', 'song', 'joke', 'verse', 'kiss', 'sunrise',
                                                     'sunset', 'eclipse', 'moon', 'rainbow', 'rain', 'plan',
                                                     'play', 'chart', 'birds', 'stars', 'pathway', 'secret',
                                                     'treasure', 'melody', 'magic', 'spell', 'light', 'morning'];

                        var prefix =
                                        // Choose 3 zen adjectives
                                        adjectives.sort(function(){return 0.5-Math.random()}).slice(-3).join('')
                                        +
                                        // Coupled with a zen noun
                                        nouns.sort(function(){return 0.5-Math.random()}).slice(-1).join('');
                        window.location.href = 'http://' + prefix + '.neverssl.com/online';
                </script>
        </head>
        <body>
        <noscript>
                <div class="notice">
                        <div class="container">
                                ⚠️ JavaScript appears to be disabled. NeverSSL's cache-busting works better if you enable JavaScript for <code>neverssl.com</code>.
                        </div>
                </div>
        </noscript>
        <div class="header">
                <div class="container">
                <h1>NeverSSL</h1>
                </div>
        </div>
        <div class="content">
        <div class="container">

        <h1 id="status"></h1>
        <script>document.querySelector("#status").textContent = "Connecting ...";</script>
        <noscript>

                <h2>What?</h2>
                <p>This website is for when you try to open Facebook, Google, Amazon, etc
                on a wifi network, and nothing happens. Type "http://neverssl.com"
                into your browser's url bar, and you'll be able to log on.</p>

                <h2>How?</h2>
                <p>neverssl.com will never use SSL (also known as TLS). No
                encryption, no strong authentication, no <a
                href="https://en.wikipedia.org/wiki/HTTP_Strict_Transport_Security">HSTS</a>,
                no HTTP/2.0, just plain old unencrypted HTTP and forever stuck in the dark
                ages of internet security.</p>

                <h2>Why?</h2>
                <p>Normally, that's a bad idea. You should always use SSL and secure
                encryption when possible. In fact, it's such a bad idea that most websites
                are now using https by default.</p>

                <p>And that's great, but it also means that if you're relying on
                poorly-behaved wifi networks, it can be hard to get online.  Secure
                browsers and websites using https make it impossible for those wifi
                networks to send you to a login or payment page. Basically, those networks
                can't tap into your connection just like attackers can't. Modern browsers
                are so good that they can remember when a website supports encryption and
                even if you type in the website name, they'll use https.</p>

                <p>And if the network never redirects you to this page, well as you can
                see, you're not missing much.</p>

        <a href="https://twitter.com/neverssl">Follow @neverssl</a>

        </noscript>

        </div>
        </div>

        </body>
</html>
* Connection #0 to host neverssl.com:80 left intact
```

---

### A.3. Запит до служби доменних імен

*Windows: `Resolve-DnsName ietf.org | Format-List`*

**Команда (перше виконання):**

```
Resolve-DnsName ietf.org | Format-List
```

**Вивід:**

```
Name       : ietf.org
Type       : AAAA
TTL        : 300
DataLength : 16
Section    : Answer
IPAddress  : 2606:4700::6810:2c63

Name       : ietf.org
Type       : AAAA
TTL        : 300
DataLength : 16
Section    : Answer
IPAddress  : 2606:4700::6810:2d63

Name       : ietf.org
Type       : A
TTL        : 300
DataLength : 4
Section    : Answer
IPAddress  : 104.16.44.99

Name       : ietf.org
Type       : A
TTL        : 300
DataLength : 4
Section    : Answer
IPAddress  : 104.16.45.99
```

**Команда (повторне виконання через 5–7 хвилин):**

```
Resolve-DnsName ietf.org | Format-List
```

**Вивід:**

```
Name       : ietf.org
Type       : AAAA
TTL        : 300
DataLength : 16
Section    : Answer
IPAddress  : 2606:4700::6810:2c63

Name       : ietf.org
Type       : AAAA
TTL        : 300
DataLength : 16
Section    : Answer
IPAddress  : 2606:4700::6810:2d63

Name       : ietf.org
Type       : A
TTL        : 300
DataLength : 4
Section    : Answer
IPAddress  : 104.16.44.99

Name       : ietf.org
Type       : A
TTL        : 300
DataLength : 4
Section    : Answer
IPAddress  : 104.16.45.99
```

**Зафіксовані значення:**

| Параметр | Перше виконання | Повторне виконання |
|---|---|---|
| Час виконання (год:хв) | 09:27 |09:34|
| IP-адреса | 104.16.44.99, 104.16.45.99, 2606:4700::6810:2c63, 2606:4700::6810:2d63 | 104.16.44.99, 104.16.45.99, 2606:4700::6810:2c63, 2606:4700::6810:2d63 |
| Значення TTL | 300 | 300 |

> Якщо друге значення TTL виявилося більшим за перше — це нормально: кеш резолвера встиг оновитися. Зафіксуйте як є.

---

### A.4. Контрольний ресурс

**Команда:**

```
curl.exe -v https://google.com
```

**Вивід:**

```
* Host google.com:443 was resolved.
* IPv6: 2a00:1450:4025:800::66, 2a00:1450:4025:800::71, 2a00:1450:4025:800::64, 2a00:1450:4025:800::8b
* IPv4: 142.250.130.100, 142.250.130.113, 142.250.130.102, 142.250.130.101, 142.250.130.138, 142.250.130.139
*   Trying [2a00:1450:4025:800::66]:443...
* schannel: disabled automatic use of client certificate
* ALPN: curl offers http/1.1
* ALPN: server accepted http/1.1
* Established connection to google.com (2a00:1450:4025:800::66 port 443) from [IPv6 приховано] port 55052
* using HTTP/1.x
> GET / HTTP/1.1
> Host: google.com
> User-Agent: curl/8.16.0
> Accept: */*
>
* Request completely sent off
* schannel: remote party requests renegotiation
* schannel: renegotiating SSL/TLS connection
* schannel: SSL/TLS connection renegotiated
< HTTP/1.1 301 Moved Permanently
< Location: https://www.google.com/
< Content-Type: text/html; charset=UTF-8
< Content-Security-Policy-Report-Only: object-src 'none';base-uri 'self';script-src 'nonce-Q1VYwnYmgAN3_C5Hlox1Og' 'strict-dynamic' 'report-sample' 'unsafe-eval' 'unsafe-inline' https: http:;report-uri https://csp.withgoogle.com/csp/gws/other-hp
< Date: Thu, 19 Nov 2026 08:46:56 GMT
< Expires: Sat, 19 Dec 2026 08:46:56 GMT
< Cache-Control: public, max-age=2592000
< Server: gws
< Content-Length: 220
< X-XSS-Protection: 0
< X-Frame-Options: SAMEORIGIN
< Alt-Svc: h3=":443"; ma=2592000,h3-29=":443"; ma=2592000
<
<HTML><HEAD><meta http-equiv="content-type" content="text/html;charset=utf-8">
<TITLE>301 Moved</TITLE></HEAD><BODY>
<H1>301 Moved</H1>
The document has moved
<A HREF="https://www.google.com/">here</A>.
</BODY></HTML>
* Connection #0 to host google.com:443 left intact
```

---

### A.5. Ресурси з некоректною конфігурацією сертифіката

**Випадок 1**

```
curl.exe -v https://expired.badssl.com
```

```
* Host expired.badssl.com:443 was resolved.
* IPv6: (none)
* IPv4: 104.154.89.105
*   Trying 104.154.89.105:443...
* schannel: disabled automatic use of client certificate
* ALPN: curl offers http/1.1
* schannel: next InitializeSecurityContext failed: SEC_E_CERT_EXPIRED (0x80090328) - The received certificate has expired.
* closing connection #0
curl: (35) schannel: next InitializeSecurityContext failed: SEC_E_CERT_EXPIRED (0x80090328) - The received certificate has expired.
```

**Випадок 2**

```
curl.exe -v https://wrong.host.badssl.com
```

```
* Host wrong.host.badssl.com:443 was resolved.
* IPv6: (none)
* IPv4: 104.154.89.105
*   Trying 104.154.89.105:443...
* schannel: disabled automatic use of client certificate
* ALPN: curl offers http/1.1
* schannel: SNI or certificate check failed: SEC_E_WRONG_PRINCIPAL (0x80090322) - The target principal name is incorrect.
* closing connection #0
curl: (60) schannel: SNI or certificate check failed: SEC_E_WRONG_PRINCIPAL (0x80090322) - The target principal name is incorrect.
More details here: https://curl.se/docs/sslcerts.html

curl failed to verify the legitimacy of the server and therefore could not
establish a secure connection to it. To learn more about this situation and
how to fix it, please visit the webpage mentioned above.
```

**Випадок 3**

```
curl.exe -v https://self-signed.badssl.com
```

```
* Host self-signed.badssl.com:443 was resolved.
* IPv6: (none)
* IPv4: 104.154.89.105
*   Trying 104.154.89.105:443...
* schannel: disabled automatic use of client certificate
* ALPN: curl offers http/1.1
* schannel: SEC_E_UNTRUSTED_ROOT (0x80090325) - The certificate chain was issued by an authority that is not trusted.
* closing connection #0
curl: (60) schannel: SEC_E_UNTRUSTED_ROOT (0x80090325) - The certificate chain was issued by an authority that is not trusted.
More details here: https://curl.se/docs/sslcerts.html

curl failed to verify the legitimacy of the server and therefore could not
establish a secure connection to it. To learn more about this situation and
how to fix it, please visit the webpage mentioned above.
```

> Якщо використано альтернативний спосіб із параметром `--resolve` — зазначити це та навести фактичну команду.

---

## Частина B. Власна модель рівнів

**Кількість виділених груп:** 5

| № | Назва групи (власне формулювання) | Рядки виводу, віднесені до групи | Обґрунтування |
|---|---|---|---|
| 1 | Отримання вмісту вебсторінки | `<html>`, `<head>`, `<body>`, `</html>` | Ці рядки містять HTML-розмітку вебсторінки, яку клієнт отримує від сервера. |
| 2 | Обмін HTTP-запитами та відповідями | `> GET / HTTP/1.1`, `> Host: ietf.org`, `< HTTP/1.1 301 Moved Permanently`, `< HTTP/1.1 200 OK` | Ці рядки показують, як клієнт надсилає запит до сервера, а сервер повертає відповідь із відповідним кодом стану. |
| 3 | Захист з'єднання та перевірка сертифікатів | `* schannel: SSL/TLS connection renegotiated`, `SEC_E_CERT_EXPIRED`, `SEC_E_WRONG_PRINCIPAL`, `SEC_E_UNTRUSTED_ROOT` | Ці повідомлення свідчать про узгодження захищеного з'єднання та перевірку терміну дії сертифіката, відповідності доменного імені й довіри до сертифіката. |
| 4 | Встановлення мережевого з'єднання | `*   Trying 104.16.44.99:443...`, `* Established connection to ietf.org (104.16.44.99 port 443) from 192.168.0.102 port 57586`, `* Connection #0 to host ietf.org:443 left intact` | Ці рядки показують спробу підключення до сервера за IP-адресою та портом, успішне встановлення з'єднання і залишення його відкритим після отримання відповіді. |
| 5 | Визначення IP-адреси за доменним іменем | `* Host ietf.org:443 was resolved.`, `* IPv4: 104.16.44.99, 104.16.45.99`, `Name : ietf.org`, `TTL : 300`, `IPAddress : 104.16.44.99` | Ці рядки показують визначення IP-адрес за доменним іменем за допомогою DNS, а також час життя DNS-записів у кеші. |

*Групи впорядковано від найближчої до користувача (№ 1) до найближчої до апаратного забезпечення. Зайві рядки вилучити, за потреби — додати.*

**Рядки, які не вдалося віднести до жодної групи:**
| Рядок виводу | Причина утруднення |
|---|---|
| `< CF-RAY: a5c6c3f9b8963bbd-WAW` | Не зрозуміло призначення цього службового ідентифікатора сервера. |
| `< alt-svc: h3=":443"; ma=86400` | Потребує додаткового вивчення, оскільки містить інформацію про альтернативний протокол з'єднання. |
| `* ALPN: server accepted http/1.1` | Складно однозначно віднести до однієї групи, оскільки рядок стосується як узгодження захищеного з'єднання, так і вибору протоколу HTTP. |

---

## Контрольні питання

**1. Скільки рядків діагностичного виводу передує отриманню даних сторінки (завдання A.1)?**

>  Отриманню даних вебсторінки передують 29 рядків діагностичного виводу, які містять інформацію про визначення IP-адреси, встановлення з'єднання, узгодження SSL/TLS, надсилання HTTP-запиту та отримання заголовків відповіді сервера.

**2. Які рядки наявні у виводі A.1 і відсутні у виводі A.2? Чим це зумовлено?**

> У виводі А.1 наявні такі рядки, які відсутні у виводі А.2:
>
> - `* schannel: disabled automatic use of client certificate`
> - `* ALPN: curl offers http/1.1`
> - `* ALPN: server accepted http/1.1`
> - `* schannel: remote party requests renegotiation`
> - `* schannel: renegotiating SSL/TLS connection`
> - `* schannel: SSL/TLS connection renegotiated`
>
> Це зумовлено тим, що у завданні А.1 використовується захищений протокол HTTPS, який передбачає шифрування даних за допомогою TLS, а у завданні А.2 використовується незахищений протокол HTTP, при якому дані передаються без TLS-шифрування.

**3. Звідки у виводі з'явилося значення `443`, якщо його не було вказано в адресі?**

>Значення 443 з'явилося автоматично, оскільки цей порт є стандартним для протоколу HTTPS. Якщо номер порту не зазначено в адресі ресурсу, програма curl використовує порт, установлений за замовчуванням для відповідного протоколу. 

**4. Як змінилося значення TTL між двома запитами (A.3)? Що означає це число?**

> Під час першого та повторного виконання DNS-запиту значення TTL становило 300 секунд, тобто не змінилося. Це може свідчити про оновлення записів у DNS-кеші. TTL (Time To Live) визначає час у секундах, протягом якого DNS-запис може зберігатися в кеші без необхідності повторного звернення до DNS-сервера. 

**5. Чим відрізняються між собою три причини помилок із завдання A.5? Сформулювати кожну однією фразою.**

| Випадок | Причина недовіри |
|---|---|
| `expired` |Закінчився термін дії сертифіката.|
| `wrong.host` | Доменне ім'я сайту не відповідає імені, зазначеному в сертифікаті.|
| `self-signed` |Самопідписаний сертифікат не має довіри з боку системи. |

**6. Три рядки з власних виводів, про які не йшлося на лекції 1:**

| № | Рядок виводу | Джерело (номер завдання) |
|---|---|---|
| 1 |`* ALPN: server accepted http/1.1` | А.1 | 
| 2 |`< CF-RAY: a5c6c3f9b8963bbd-WAW` | А.1 |
| 3 |`< Accept-Ranges: bytes` | А.2 |

*Пояснення до цих рядків не потрібне.*

---

## Висновки


**D.1. Що виявилося неочевидним або несподіваним**

*Назвати конкретно, з посиланням на рядок виводу.*

> Під час виконання практичної роботи для мене виявилося несподіваним те, що перед отриманням вмісту вебсторінки виконується значна кількість службових операцій. Зокрема, рядок `* Trying 104.16.44.99:443...` показав, що порт 443 визначається автоматично, хоча в команді він не зазначався. Також під час двох DNS-запитів значення `TTL : 300` залишилося незмінним. Цікавим виявилося й те, що система самостійно виявляє різні помилки сертифікатів та припиняє встановлення захищеного з'єднання.

**D.2. Чому саме така кількість груп у частині B**

*На якій підставі ухвалено рішення. Що змусило б його змінити.*

> На підставі отриманих експериментальних даних було виділено п'ять логічних груп. Кожна з них характеризує окремий аспект взаємодії клієнта із сервером: отримання вмісту вебсторінки, обмін HTTP-запитами та відповідями, захист з'єднання, встановлення мережевого з'єднання та визначення IP-адреси за доменним іменем. Саме така кількість груп дозволяє систематизувати отримані результати та пояснити більшість спостережуваних процесів. Кількість груп можна було б збільшити, якби отримані дані також містили інформацію про передавання мережевих пакетів, MAC-адреси та фізичне передавання сигналів.

**D.3. Питання, яке залишилося без відповіді**

> Після виконання практичної роботи залишилося питання щодо призначення службового заголовка `CF-RAY` та його ролі в обміні даними між клієнтом і сервером. Також хотілося б детальніше дослідити механізм оновлення DNS-кешу та з'ясувати, чому під час повторного запиту значення TTL залишилося незмінним.

---

## Використання штучного інтелекту

*Розділ обов'язковий. Заповнюється незалежно від того, чи використовувався ШІ. Детальні вимоги — у документі «Політика використання технологій штучного інтелекту».*

**Факт використання:** використано / 

**Установлений рівень для цієї роботи:** Р3 — ШІ як співвиконавець

**Фактичний рівень використання:** Р3

### Використані системи

| Система | Версія або модель | Період використання |
|---|---|---|
| ChatGPT | GPT-6 | 18.11.2026–19.11.2026 |

### Промпти

*Наводити дослівно, у тому вигляді, у якому запит було надано системі. Переказ не приймається.*

| № | Розділ роботи | Текст промпта |
|---|---|---|
| 1 | Підготовка до виконання роботи | Допоможи як її правильно зробити |
| 2 | Оформлення звіту | що внести в таблицю |
| 3 | Частина B | давай заповню всі групи і я надішлю скрін |
| 4 | Частина А | З якого рядка починати копіювати з блокнота? |

### Дії з отриманим результатом

| № промпта | Що перевірено | Що змінено | Що відхилено і чому |
|---|---|---|---|
| 1 | Відповідність методичним рекомендаціям | Уточнено порядок виконання роботи | — |
| 2 | Правильність заповнення таблиці | Внесено власні дані, номер групи та варіанта | — |
| 3 | Відповідність груп експериментальним даним | Видалено зайві рядки таблиці | — |
| 4 | Результати виконання команд у PowerShell | Виправлено форматування виводів | — |

ШІ також використовувався для формулювання відповідей на контрольні питання та висновків на основі отриманих експериментальних даних.

### Підтвердження

Підтверджую, що всі наведені в цьому звіті виводи команд отримано мною особисто внаслідок фактичного виконання відповідних дій, а відомості цього розділу є повними та достовірними.

> Виводи `curl`, `dig` та інші артефакти не можуть бути згенеровані. Це стосується будь-якого рівня використання ШІ.

---

## Примітки виконавця

*(необов'язковий розділ: що не спрацювало, які команди довелося змінити, які виникли труднощі)*

> Під час виконання практичної роботи виникли такі труднощі:
- У завданні А.2 під час першої спроби підключення виникла помилка curl (28) через перевищення часу очікування. Повторний запит виконано успішно.
- У завданні А.3 для повного відображення DNS-записів використано командлет `Format-List`.
- У середовищі Windows PowerShell замість команди curl використовувалася команда curl.exe.
- Під час оформлення звіту виникли незначні труднощі з форматуванням таблиць і блоків коду в Markdown, які було усунуто.
- У завданні А.4 власну IPv6-адресу приховано з міркувань конфіденційності. Решту діагностичного виводу залишено без змін.
