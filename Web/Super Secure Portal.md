# CTF Writeup: JavaScript Obfuscation Challenge

## Challenge Overview
We were presented with an obfuscated JavaScript code snippet and a login page that required a password. The goal was to analyze the JavaScript, extract the password, and log in to retrieve the flag.

## Deobfuscating the Code
The given JavaScript was obfuscated using an array-based substitution method. After deobfuscation, we identified a function `CheckPassword` that verifies the user input by comparing it against values stored in `localStorage`.
```javascript
var _0x575c = ["2-4", "substring", "4-7", "getItem", "deleteItem", "12-14", "0-2", "setItem", "9-12", "^7M", "updateItem", "bb=", "7-9", "14-16", "localStorage"];
(function (_0x4f0aae, _0x575cf8) {
  var _0x51eea2 = function (_0x180eeb) {
    while (--_0x180eeb) {
      _0x4f0aae.push(_0x4f0aae.shift());
    }
  };
  _0x51eea2(++_0x575cf8);
})(_0x575c, 0x78);
var _0x51ee = function (_0x4f0aae, _0x575cf8) {
  _0x4f0aae = _0x4f0aae - 0x0;
  var _0x51eea2 = _0x575c[_0x4f0aae];
  return _0x51eea2;
};
function CheckPassword(_0x47df21) {
  var _0x4bbdc3 = [_0x51ee('0xe'), _0x51ee('0x3'), _0x51ee('0x7'), _0x51ee('0x4'), _0x51ee('0xa')];
  window[_0x4bbdc3[0x0]][_0x4bbdc3[0x2]]('9-12', 'BE*');
  window[_0x4bbdc3[0x0]][_0x4bbdc3[0x2]](_0x51ee('0x2'), _0x51ee('0xb'));
  window[_0x4bbdc3[0x0]][_0x4bbdc3[0x2]](_0x51ee('0x6'), '5W');
  window[_0x4bbdc3[0x0]][_0x4bbdc3[0x2]]('16', _0x51ee('0x9'));
  window[_0x4bbdc3[0x0]][_0x4bbdc3[0x2]](_0x51ee('0x5'), 'pg');
  window[_0x4bbdc3[0x0]][_0x4bbdc3[0x2]]('7-9', '+n');
  window[_0x4bbdc3[0x0]][_0x4bbdc3[0x2]](_0x51ee('0xd'), '4t');
  window[_0x4bbdc3[0x0]][_0x4bbdc3[0x2]](_0x51ee('0x0'), '$F');
  if (window[_0x4bbdc3[0x0]][_0x4bbdc3[0x1]](_0x51ee('0x8')) === _0x47df21[_0x51ee('0x1')](0x9, 0xc)) {
    if (window[_0x4bbdc3[0x0]][_0x4bbdc3[0x1]](_0x51ee('0x2')) === _0x47df21.substring(0x4, 0x7)) {
      if (window[_0x4bbdc3[0x0]][_0x4bbdc3[0x1]](_0x51ee('0x6')) === _0x47df21[_0x51ee('0x1')](0x0, 0x2)) {
        if (window[_0x4bbdc3[0x0]][_0x4bbdc3[0x1]]('16') === _0x47df21[_0x51ee('0x1')](0x10)) {
          if (window[_0x4bbdc3[0x0]][_0x4bbdc3[0x1]](_0x51ee('0x5')) === _0x47df21[_0x51ee('0x1')](0xc, 0xe)) {
            if (window[_0x4bbdc3[0x0]][_0x4bbdc3[0x1]](_0x51ee('0xc')) === _0x47df21[_0x51ee('0x1')](0x7, 0x9)) {
              if (window[_0x4bbdc3[0x0]][_0x4bbdc3[0x1]](_0x51ee('0xd')) === _0x47df21[_0x51ee('0x1')](0xe, 0x10)) {
                if (window[_0x4bbdc3[0x0]][_0x4bbdc3[0x1]](_0x51ee('0x0')) === _0x47df21[_0x51ee('0x1')](0x2, 0x4)) {
                  return true;
                }
              }
            }
          }
        }
      }
    }
  }
  return false;
}
```
### Identifying Password Storage
The `localStorage` was set with different segments of the password:

```javascript
localStorage.setItem('0-2', '5W');
localStorage.setItem('2-4', '$F');
localStorage.setItem('4-7', 'bb=');
localStorage.setItem('7-9', '+n');
localStorage.setItem('9-12', 'BE*');
localStorage.setItem('12-14', 'pg');
localStorage.setItem('14-16', '4t');
localStorage.setItem('16', '^7M');
```

The password was split into segments, and each segment was stored with a specific key in `localStorage`.

## Reconstructing the Password
By concatenating the stored values in order, we obtained the password:

```
5W$Fbb=+nBE*pg4t^7M
```

## Logging In
Entering the reconstructed password into the login page granted access and revealed the flag.

## Flag
```
ctf7{let_me_c0nfus3_you}
```

