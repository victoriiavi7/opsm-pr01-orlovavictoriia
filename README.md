# opsm-pr01-orlovavictoriia

# Практична робота № 1

**Дисципліна:** Основи побудови інформаційних систем та мереж

**Тема:** Спостереження за процесом звернення до вебресурсу. Побудова власної моделі рівнів взаємодії

|                          |                                      |
| ------------------------ | ------------------------------------ |
| **Прізвище, ім'я**       | Орлова Вікторія                      |
| **Група**                | F5 2.02                              |
| **Номер варіанта**       | 18                                   |
| **Домен варіанта**       | openwrt.org                          |
| **Середовище виконання** | macOS                                |
| **Версія curl**          | curl 8.7.1 (x86_64-apple-darwin25.0) |
| **Дата виконання**       | 12/09/2026                           |

---

## Частина A. Збір експериментальних даних

### A.1. Запит із діагностичним виводом

**Команда:**

```bash
curl -v openwrt.org
```

**Вивід:** [a1-curl-https.txt](raw/a1-curl-https.txt)

```text
* Host openwrt.org:80 was resolved.
* IPv6: (none)
* IPv4: 64.226.122.113
*   Trying 64.226.122.113:80...
* Connected to openwrt.org (64.226.122.113) port 80
> GET / HTTP/1.1
> Host: openwrt.org
> User-Agent: curl/8.7.1
> Accept: */*
>
* Request completely sent off
< HTTP/1.1 301 Moved Permanently
< Server: nginx
< Date: Sat, 12 Sep 2026 10:28:31 GMT
< Content-Type: text/html
< Content-Length: 162
< Connection: keep-alive
< Location: https://openwrt.org/
<
<html>
<head><title>301 Moved Permanently</title></head>
<body>
<center><h1>301 Moved Permanently</h1></center>
<hr><center>nginx</center>
</body>
</html>
* Connection #0 to host openwrt.org left intact
```

---

### A.2. Запит без захисту з'єднання

**Команда:**

```bash
curl -v "http://neverssl.com"
```

**Вивід:** [a2-curl-http.txt](raw/a2-curl-http.txt)

```text
* Host neverssl.com:80 was resolved.
* IPv6: (none)
* IPv4: 34.223.124.45
*   Trying 34.223.124.45:80...
* Connected to neverssl.com (34.223.124.45) port 80
* using HTTP/1.x
> GET / HTTP/1.1
> Host: neverssl.com
> User-Agent: curl/8.12.1
> Accept: */*
>
* Request completely sent off
< HTTP/1.1 200 OK
< Date: Sat, 12 Sep 2026 10:31:07 GMT
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
                                ⚠️ JavaScript appears to be disabled. NeverSSL'ss cache-busting works better if you enable JavaScript for <code>neverssl.com</code>.
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
                poorly-behaved wifi networks, it can be hard to get online. Secure
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
* Connection #0 to host neverssl.com left intact
```

> **Примітка:** у фактичному виводі A.2 зазначено `curl/8.12.1`, хоча у відомостях про середовище наведено `curl 8.7.1`. У звіті залишено фактичне значення з отриманого виводу.

---

### A.3. Запит до служби доменних імен

**Команда (перше виконання):**

```bash
dig openwrt.org
```

**Вивід:** [a3-dig.txt](raw/a3-dig.txt)

```text
; <<>> DiG 9.10.6 <<>> openwrt.org
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 29275
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;openwrt.org.                   IN      A

;; ANSWER SECTION:
openwrt.org.            3039    IN      A       64.226.122.113

;; Query time: 5 msec
;; SERVER: 192.168.88.1#53(192.168.88.1)
;; WHEN: Sat Sep 12 13:33:56 EEST 2026
;; MSG SIZE  rcvd: 45
```

**Команда (повторне виконання через 5–7 хвилин):**

```bash
dig openwrt.org
```

**Вивід:** [a3-dig.txt](raw/a3-dig.txt)

```text
; <<>> DiG 9.10.6 <<>> openwrt.org
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 25878
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;openwrt.org.                   IN      A

;; ANSWER SECTION:
openwrt.org.            2719    IN      A       64.226.122.113

;; Query time: 3 msec
;; SERVER: 192.168.88.1#53(192.168.88.1)
;; WHEN: Sat Sep 12 13:39:16 EEST 2026
;; MSG SIZE  rcvd: 45
```

**Зафіксовані значення:**

| Параметр               | Перше виконання | Повторне виконання |
| ---------------------- | --------------: | -----------------: |
| Час виконання (год:хв) |           13:33 |              13:39 |
| IP-адреса              |  64.226.122.113 |     64.226.122.113 |
| Значення TTL           |            3039 |               2719 |

---

### A.4. Контрольний ресурс

**Команда:**

```bash
curl -v "https://google.com"
```

**Вивід:** [a4-google.txt](raw/a4-google.txt)

```text
* Host google.com:443 was resolved.
* IPv6: (none)
* IPv4: 172.217.17.78
*   Trying 172.217.17.78:443...
* Connected to google.com (172.217.17.78) port 443
* ALPN: curl offers h2,http/1.1
* (304) (OUT), TLS handshake, Client hello (1):
*  CAfile: /etc/ssl/cert.pem
*  CApath: none
* (304) (IN), TLS handshake, Server hello (2):
* (304) (IN), TLS handshake, Unknown (8):
* (304) (IN), TLS handshake, Certificate (11):
* (304) (IN), TLS handshake, CERT verify (15):
* (304) (IN), TLS handshake, Finished (20):
* (304) (OUT), TLS handshake, Finished (20):
* SSL connection using TLSv1.3 / AEAD-CHACHA20-POLY1305-SHA256 / [blank] / UNDEF
* ALPN: server accepted h2
* Server certificate:
*  subject: CN=*.google.com
*  start date: Aug 10 08:37:35 2026 GMT
*  expire date: Nov 2 08:37:34 2026 GMT
*  subjectAltName: host "google.com" matched cert's "google.com"
*  issuer: C=US; O=Google Trust Services; CN=WR2
*  SSL certificate verify ok.
* using HTTP/2
* [HTTP/2] [1] OPENED stream for https://google.com/
* [HTTP/2] [1] [:method: GET]
* [HTTP/2] [1] [:scheme: https]
* [HTTP/2] [1] [:authority: google.com]
* [HTTP/2] [1] [:path: /]
* [HTTP/2] [1] [user-agent: curl/8.7.1]
* [HTTP/2] [1] [accept: */*]
> GET / HTTP/2
> Host: google.com
> User-Agent: curl/8.7.1
> Accept: */*
>
* Request completely sent off
< HTTP/2 301
< location: https://www.google.com/
< content-type: text/html; charset=UTF-8
< content-security-policy-report-only: object-src 'none';base-uri 'self';script-src 'nonce-AfSQ9TBzG5Z6qx4Kqd1bcw' 'strict-dynamic' 'report-sample' 'unsafe-eval' 'unsafe-inline' https: http:;report-uri https://csp.withgoogle.com/csp/gws/other-hp
< date: Sat, 12 Sep 2026 10:34:40 GMT
< expires: Mon, 12 Oct 2026 10:34:40 GMT
< cache-control: public, max-age=2592000
< server: gws
< content-length: 220
< x-xss-protection: 0
< x-frame-options: SAMEORIGIN
< alt-svc: h3=":443"; ma=2592000,h3-29=":443"
<
<HTML><HEAD><meta http-equiv="content-type" content="text/html;charset=utf-8">
<TITLE>301 Moved</TITLE></HEAD><BODY>
<H1>301 Moved</H1>
The document has moved
<A HREF="https://www.google.com/">here</A>.
</BODY></HTML>
* Connection #0 to host google.com left intact
```

---

### A.5. Ресурси з некоректною конфігурацією сертифіката

#### Випадок 1

**Команда:**

```bash
curl -v "https://expired.badssl.com"
```

**Вивід:** [a5-tls-errors.txt](raw/a5-tls-errors.txt)

```text
* Host expired.badssl.com:443 was resolved.
* IPv6: (none)
* IPv4: 104.154.89.105
*   Trying 104.154.89.105:443...
* Connected to expired.badssl.com (104.154.89.105) port 443
* ALPN: curl offers h2,http/1.1
* (304) (OUT), TLS handshake, Client hello (1):
*  CAfile: /etc/ssl/cert.pem
*  CApath: none
* (304) (IN), TLS handshake, Server hello (2):
* TLSv1.2 (IN), TLS handshake, Certificate (11):
* TLSv1.2 (OUT), TLS alert, certificate expired (557):
* SSL certificate problem: certificate has expired
* Closing connection
* TLSv1.2 (IN), TLS handshake, Certificate (11):
* TLSv1.2 (OUT), TLS alert, certificate expired (557):
curl: (60) SSL certificate problem: certificate has expired

More details here: https://curl.se/docs/sslcerts.html

curl failed to verify the legitimacy of the server and therefore could not
establish a secure connection to it. To learn more about this situation and
how to fix it, please visit the web page mentioned above.
```

#### Випадок 2

**Команда:**

```bash
curl -v "https://wrong.host.badssl.com"
```

**Вивід:** [a5-tls-errors.txt](raw/a5-tls-errors.txt)

```text
* Host wrong.host.badssl.com:443 was resolved.
* IPv6: (none)
* IPv4: 104.154.89.105
*   Trying 104.154.89.105:443...
* Connected to wrong.host.badssl.com (104.154.89.105) port 443
* ALPN: curl offers h2,http/1.1
* (304) (OUT), TLS handshake, Client hello (1):
*  CAfile: /etc/ssl/cert.pem
*  CApath: none
* (304) (IN), TLS handshake, Server hello (2):
* TLSv1.2 (IN), TLS handshake, Certificate (11):
* TLSv1.2 (OUT), TLS handshake, Server key exchange (12):
* TLSv1.2 (IN), TLS handshake, Server finished (14):
* TLSv1.2 (OUT), TLS handshake, Client key exchange (16):
* TLSv1.2 (OUT), TLS change cipher, Change cipher spec (1):
* TLSv1.2 (OUT), TLS handshake, Finished (20):
* TLSv1.2 (IN), TLS change cipher, Change cipher spec (1):
* TLSv1.2 (IN), TLS handshake, Finished (14):
* SSL connection using TLSv1.2 / ECDHE-RSA-AES128-GCM-SHA256 / [blank] / UNDEF
* ALPN: server accepted http/1.1
* Server certificate:
*  subject: CN=*.badssl.com
*  start date: Jul 28 20:03:02 2026 GMT
*  expire date: Oct 26 20:03:01 2026 GMT
*  subjectAltName does not match host name wrong.host.badssl.com
* SSL: no alternative certificate subject name matches target host name 'wrong.host.badssl.com'
* Closing connection
* TLSv1.2 (OUT), TLS alert, close notify (256):
curl: (60) SSL: no alternative certificate subject name matches target host name 'wrong.host.badssl.com'

More details here: https://curl.se/docs/sslcerts.html

curl failed to verify the legitimacy of the server and therefore could not
establish a secure connection to it. To learn more about this situation and
how to fix it, please visit the web page mentioned above.
```

#### Випадок 3

**Команда:**

```bash
curl -v "https://self-signed.badssl.com"
```

**Вивід:** [a5-tls-errors.txt](raw/a5-tls-errors.txt)

```text
* Host self-signed.badssl.com:443 was resolved.
* IPv6: (none)
* IPv4: 104.154.89.105
*   Trying 104.154.89.105:443...
* Connected to self-signed.badssl.com (104.154.89.105) port 443
* ALPN: curl offers h2,http/1.1
* (304) (OUT), TLS handshake, Client hello (1):
*  CAfile: /etc/ssl/cert.pem
*  CApath: none
* (304) (IN), TLS handshake, Server hello (2):
* TLSv1.2 (IN), Certificate (11):
* TLSv1.2 (OUT), TLS alert, unknown CA (560):
* SSL certificate problem: self signed certificate
* Closing connection
* TLSv1.2 (IN), TLS handshake, Certificate (11):
* TLSv1.2 (OUT), TLS alert, unknown CA (560):
curl: (60) SSL certificate problem: self signed certificate

More details here: https://curl.se/docs/sslcerts.html

curl failed to verify the legitimacy of the server and therefore could not
establish a secure connection to it. To learn more about this situation and
how to fix it, please visit the web page mentioned above.
```

---

# Частина B. Власна модель рівнів

**Кількість виділених груп:** 7

| № | Назва групи (власне формулювання)          | Рядки виводу, віднесені до групи                                                                           | Обґрунтування                                                                                  |
| - | ------------------------------------------ | ---------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| 1 | **Вміст вебсторінки**                      | `<html>`, `<head>`, `<body>`, HTML-теги, текст сторінки                                                    | Це безпосередньо дані, які отримує користувач від вебресурсу.                                  |
| 2 | **HTTP-запит і відповідь**                 | `> GET / HTTP/1.1`, `> Host:`, `> User-Agent:`, `< HTTP/1.1 301`, `< Content-Type:`, `< Location:`         | Ці рядки описують обмін HTTP-повідомленнями між клієнтом і сервером.                           |
| 3 | **Захищене з'єднання**                     | `TLS handshake`, `SSL connection using TLSv1.3`, `Server certificate`, `SSL certificate verify ok`         | Рядки характеризують встановлення та перевірку захищеного TLS-з'єднання.                       |
| 4 | **Встановлення мережевого з'єднання**      | `Trying 64.226.122.113:80`, `Connected to openwrt.org ... port 80`, `Connected to google.com ... port 443` | Показують спробу та результат встановлення TCP-з'єднання з визначеною IP-адресою та портом.    |
| 5 | **Визначення IP-адреси**                   | `Host openwrt.org:80 was resolved`, `IPv4: 64.226.122.113`, `Host google.com:443 was resolved`             | На цьому етапі доменне ім'я пов'язується з IP-адресою.                                         |
| 6 | **DNS-інформація**                         | `QUESTION SECTION`, `ANSWER SECTION`, `IN A`, `SERVER`, `TTL`                                              | Містить безпосередні результати роботи служби DNS та параметри відповіді.                      |
| 7 | **Локальне/мережеве середовище виконання** | `SERVER: 192.168.88.1#53`, `CAfile: /etc/ssl/cert.pem`, `CApath: none`                                     | Ці рядки характеризують локальні ресурси та параметри середовища, через які виконується запит. |

### Рядки, які не вдалося однозначно віднести до жодної групи

| Рядок виводу                                      | Причина утруднення                                                                                    |
| ------------------------------------------------- | ----------------------------------------------------------------------------------------------------- |
| `* (304) (IN), TLS handshake, Unknown (8)`        | Позначення внутрішнього типу TLS-повідомлення, яке складно однозначно віднести до окремого рівня.     |
| `* Connection #0 to host openwrt.org left intact` | Службова інформація curl про стан з'єднання після завершення обміну.                                  |
| `* Request completely sent off`                   | Службовий статус curl, який описує завершення передачі запиту, але не є окремим мережевим протоколом. |

---

# Контрольні питання

### 1. Скільки рядків діагностичного виводу передує отриманню даних сторінки (завдання A.1)?

> Перед отриманням HTML-даних сторінки у виводі A.1 є **19 рядків**, якщо рахувати всі службові, мережеві та HTTP-рядки від `* Host openwrt.org:80 was resolved.` до порожнього рядка після `Location: https://openwrt.org/`.

### 2. Які рядки наявні у виводі A.1 і відсутні у виводі A.2? Чим це зумовлено?

> У A.1 наявні рядки, пов'язані з перенаправленням `HTTP/1.1 301 Moved Permanently`, зокрема `Location: https://openwrt.org/`. У A.2 сервер одразу повернув `HTTP/1.1 200 OK`. Також A.1 і A.2 відрізняються службовими рядками curl та параметрами HTTP-з'єднання. Це зумовлено різною конфігурацією серверів і тим, що openwrt.org перенаправляє HTTP-запит на HTTPS, а neverssl.com повертає сторінку безпосередньо через HTTP.

### 3. Звідки у виводі з'явилося значення `443`, якщо його не було вказано в адресі?

> Значення `443` - це стандартний порт HTTPS. Curl автоматично використовує його, коли в адресі вказано протокол `https://`, навіть якщо номер порту явно не записаний.

### 4. Як змінилося значення TTL між двома запитами (A.3)? Що означає це число?

> TTL зменшився з **3039** до **2719**. Різниця становить **320 секунд**. TTL показує час, протягом якого DNS-запис може залишатися актуальним у кеші DNS-резолвера.

### 5. Чим відрізняються між собою три причини помилок із завдання A.5? Сформулювати кожну однією фразою.

| Випадок       | Причина недовіри                                                         |
| ------------- | ------------------------------------------------------------------------ |
| `expired`     | Сертифікат має прострочений термін дії.                                  |
| `wrong.host`  | Ім'я хоста не відповідає іменам, зазначеним у сертифікаті.               |
| `self-signed` | Сертифікат самопідписаний і не довірений системним центром сертифікації. |

### 6. Три рядки з власних виводів, про які не йшлося на лекції 1:

| № | Рядок виводу                                             | Джерело (номер завдання) |
| - | -------------------------------------------------------- | ------------------------ |
| 1 | `* ALPN: server accepted h2`                             | A.4                      |
| 2 | `< content-security-policy-report-only: ...`             | A.4                      |
| 3 | `* TLSv1.2 (OUT), TLS alert, certificate expired (557):` | A.5, випадок 1           |

---

# Висновки

## D.1. Що виявилося неочевидним або несподіваним

> Під час виконання роботи неочевидним виявилося те, що звернення до сайту за HTTP не обов'язково одразу приводить до отримання його сторінки. У виводі A.1 сервер `openwrt.org` повернув `HTTP/1.1 301 Moved Permanently` та рядок `Location: https://openwrt.org/`, тобто перенаправив запит на захищений протокол HTTPS. На відміну від цього, `neverssl.com` у A.2 повернув `HTTP/1.1 200 OK` і передав HTML без встановлення TLS-з'єднання. Також цікавим було спостерігати за процесом TLS у A.4: у виводі послідовно з'являються `Client hello`, `Server hello`, `Certificate`, `CERT verify` та `Finished`, після чого curl повідомляє `SSL certificate verify ok`. У A.5 було видно, що сама наявність TLS не гарантує успішного з'єднання: у трьох випадках проблема виникала на етапі перевірки сертифіката, але причини були різними. Окремо зафіксовано зміну TTL DNS-запису з 3039 до 2719 секунд при незмінній IP-адресі `64.226.122.113`.

## D.2. Чому саме така кількість груп у частині B

> Було виділено 7 груп, оскільки під час аналізу виводів вдалося розділити спостережувані рядки за їхньою функцією: дані сторінки, HTTP-обмін, TLS, мережеве з'єднання, визначення IP, DNS та параметри середовища. Такий поділ дозволяє простежити шлях від отриманих користувачем даних до нижчих етапів мережевої взаємодії. Кількість груп могла б змінитися, якби аналізувалися додаткові протоколи або детальніші дані мережевого рівня.

## D.3. Питання, яке залишилося без відповіді

> Залишилося питання, чому для `openwrt.org` та `google.com` curl у моєму середовищі показує відсутність IPv6 (`IPv6: (none)`), хоча сучасні вебресурси можуть підтримувати IPv6.

---

## Використання ШІ

**Інструмент:** ChatGPT
**Модель:** GPT-5.6 Luna
**Дата використання:** 12.09.2026

### Використані промпти

**Промпт 1:**

> сделай красивый высновок, оформление файла мд и вставь туда ссылки на файлы

**Результат використання ШІ:**
ШІ використовувався для допомоги в оформленні протоколу практичної роботи, додавання посилань на файли з результатами виконання команд, а також для формулювання та редагування висновків за результатами виконаної роботи.

### Підтвердження

Підтверджую, що всі наведені в цьому звіті виводи команд отримано мною особисто внаслідок фактичного виконання відповідних дій, а відомості цього розділу є повними та достовірними.

> Виводи `curl`, `dig` та інші артефакти не можуть бути згенеровані. Це стосується будь-якого рівня використання ШІ.

---
