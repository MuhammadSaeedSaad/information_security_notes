# XSS cross-site scripting
## definition
Cross-site scripting (also known as XSS) is a web security vulnerability that allows an attacker to compromise the interactions that users have with a vulnerable application. It allows an attacker to circumvent the same origin policy, which is designed to segregate different websites from each other.

## How to find it
usering _alert()_ or _print()_.

## important notes when trying to exploit or find XSS
1. 
```html
don't give up when <script>alert(11)</script> doesn't work .. sometimes it doesn't work and <img src=() onerror="alert(11);"> works 
```

## Types of XSS
-   [Reflected XSS](https://portswigger.net/web-security/cross-site-scripting#reflected-cross-site-scripting), where the malicious script comes from the current HTTP request.
-   [Stored XSS](https://portswigger.net/web-security/cross-site-scripting#stored-cross-site-scripting), where the malicious script comes from the website's database.
-   [DOM-based XSS](https://portswigger.net/web-security/cross-site-scripting#dom-based-cross-site-scripting), where the vulnerability exists in client-side code rather than server-side code.

## recourse
1. [Cross Site Scripting Prevention Cheat Sheet by OWASP](https://cheatsheetseries.owasp.org/cheatsheets/Cross_Site_Scripting_Prevention_Cheat_Sheet.html).
2. [Excess XSS](https://excess-xss.com/).
