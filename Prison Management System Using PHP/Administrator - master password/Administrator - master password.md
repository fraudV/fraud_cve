# Prison Management System Using PHP - Administrator - master password

The login logic in Admin/login.php doesn't perform any filtering. The SQL query is: "SELECT \* FROM users WHERE username='".\$username."' and password = '".\$password."'"

![](image/image_SfTHUnmuTI.png)

Entering ' or '1'='1 at the password field allows logging in.

![](image/image_JJOG_-8m-g.png)

![](image/image_4oQmtlmY6V.png)
