# Terminal Jailbreak - CTF Writeup

## Challenge Overview
The challenge places us in a restricted shell environment, simulating a jailed terminal. The objective is to break out of the jail and retrieve the flag.

### Given Information:
- We are placed in `/home/user`.
- The system provides a prompt: `hacker@ctf:/home/user$`
- A `help` command is available for checking available commands.

## Exploitation Steps

### Step 1: Finding the Flag in the Frontend Source
Instead of exploiting the terminal directly, we find that the flag is exposed in the frontend source code of the given artifact. By inspecting the page source or using the `view-source` method in the browser, we can retrieve the flag embedded within the JavaScript code.

1. Visit the URL: [https://claude.site/artifacts/0e9c922d-9237-4121-b470-3cb0842a1cfb](https://claude.site/artifacts/0e9c922d-9237-4121-b470-3cb0842a1cfb)
2. Open the browser's developer tools or simply right-click and select "View Page Source."
3. Look for a line similar to this:
   ```javascript
   const [flag, setFlag] = useState('CTF{t3rm1n4l_m4st3r}')
   ```
   This line contains the flag directly in the JavaScript code.

### Step 3: Extracting the Flag
The flag can be found in the JavaScript variable:
```
CTF{t3rm1n4l_m4st3r}
```
