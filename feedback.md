**http://10.0.0.12/?page=feedback**

This page is vulnerable to a XSS attack.

For some reason, the page does not accept:
\<script\>alert(1)\</script\>
The following input into the name field will be accepted and autocompletes.
\<script\>al

**FLAG:
0fbb54bbf7d099713ca4be297e1bc7da0173d8b3c21c1811b916a3a86652724e**

https://owasp.org/www-community/attacks/xss/
