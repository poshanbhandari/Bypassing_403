# Bypassing_403

## If you stumbled upon a "403 Forbidden" page .Here are some things 

### Remove the host header

By removing the Host header from the request, some servers may return a redirect Location header.

This location could be the actual address of the application behind the firewall which (when accessed directly) let's you bypass the 403

![image](https://github.com/user-attachments/assets/56517017-4d29-4504-9db0-b1ae8dfef2bc)


### Change the letter case

/admin -> 403 Forbidden
/AdMiN -> 200 OK

### Use the alternate HTTP Versions

HTTP/0.9
HTTP/1.1
HTTP/3

### Use HTTP Method Fuzzing 𝐇𝐓𝐓𝐏 𝐌𝐞𝐭𝐡𝐨𝐝 𝐅𝐮𝐳𝐳𝐢𝐧𝐠

GET /admin HTTP/1.1 -> 403 Forbidden
POST /admin HTTP/1.1 -> 403 Forbidden
PUT /admin HTTP/1.1 -> 403 Forbidden
PATCH /admin HTTP/1.1 -> 200 OK

### User- Agent Fuzzing 

GET /admin HTTP/1.1
Host: target
User-Agent: <INTRUDER_INJECTION>

### Do Path Fuzzing

Trick the URL parser into thinking you are trying to access another page (one that should not be protected

target[.]com/admin/?
target[.]com//admin//
target[.]com///admin///

### HTTP Header Fuzzing

Lastly but not least. It involves adding headers such as HTTP-X-FORWARDED-FOR-IP to the request. 

Based on how the application/server is configured, it might interpret the request as coming from localhost and disable some of the security measures as it implies this is a safe place
