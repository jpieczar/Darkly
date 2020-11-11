**http://10.0.12/?page=media**

This is another example of XSS.
Here the javascript code is injected into the source of a image tag.
This was achieved by encoding the following into base64:
_<script>alert(1)</script>_
This method is used to disguise the payload and avoid the present XSS filters.

_http://10.0.0.12/?page=media&src=data:text/html;base64,PHNjcmlwdD5hbGVydCgxKTwvc2NyaXB0Pg==_

After doing this, a flag will be returned.

https://owasp.org/www-community/xss-filter-evasion-cheatsheet

**FLAG:
928d819fc19405ae09921a2b71227bd9aba106f9d2d37ac412e9e5a750f1506d**
