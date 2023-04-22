# Popular Web-Security Exploration Testing

## Part 1 defenses against SQL injection
### 1.0 No defenses
Target: https://comp427.rice.edu/proj2/sqlinject0/

### 1.1 Simple escaping
The server escapes single quotes (') in the inputs by replacing them with two single quotes.
Target: https://comp427.rice.edu/proj2/sqlinject1/

### 1.2 Escaping and Hashing
The server uses the following PHP code, which escapes the username and applies the MD5
hash function to the password.
```
if (isset($_POST['username']) and isset($_POST['password'])) {
$username = mysql_real_escape_string($_POST['username']);
$password = md5($_POST['password'], true);
$sql_s = "SELECT * FROM users WHERE username='$username' and pw='$password'";
$rs = mysql_query($sql_s);
if (mysql_num_rows($rs) > 0) {
echo "Login successful!";
} else {
echo "Incorrect username or password";
}
}
```
https://comp427.rice.edu/proj2/sqlinject2/checklogin.php

## Part 2 defenses against XSS (Cross Site Scripting)
### 2.0 No defenses
Target: https://comp427.rice.edu/proj2/search?xssdefense=0

### 2.1 Remove “script”
```
filtered = re.sub(r"(?i)script", "", input) 
```
Target: https://comp427.rice.edu/proj2/search?xssdefense=1

### 2.2 Remove several tags
```
filtered = re.sub(r"(?i)script|<img|<body|<style|<meta|<embed|<object",
"", input)
```
Target: https://comp427.rice.edu/proj2/search?xssdefense=2

### 2.3 Remove some punctuation
```
filtered = re.sub(r"[;'\"]", "", input)
```
Target: https://comp427.rice.edu/proj2/search?xssdefense=3

## Part 3 defenses against CSRF (Cross Site Request Forgery)
### 3.0 No defenses
Target: https://comp427.rice.edu/proj2/login?csrfdefense=0&xssdefense=4
### 3.1 Token validation
The server sets a cookie named csrf_token to a random 16-byte value and also includes
this value as a hidden field in the login form. When the form is submitted, the server verifies
that the client’s cookie matches the value in the form. You are allowed to exploit the XSS
vulnerability from Part 2 to accomplish your goal.

Target: https://comp427.rice.edu/proj2/login?csrfdefense=1&xssdefense=0

## Disclaimer:
If you're currently enrolled in Intro to Computer Security at Rice University or plan to take it in the future.

**Please do not access my solutions till the conclusion of your term. 
Let's all strive to uphold academic integrity and follow our university's policies. Thank you for understanding!**
