# Web-Security

## Part 1 defenses against SQL injection
### 1.0 No defenses
Target: https://comp427.rice.edu/proj2/sqlinject0/
Submission: sql_0.txt
### 1.1 Simple escaping
The server escapes single quotes (') in the inputs by replacing them with two single quotes.
Target: https://comp427.rice.edu/proj2/sqlinject1/
Submission: sql_1.txt
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

## Part 2 defenses against XSS (Cross Site Scripting)

## Part 3 defenses against CSRF (Cross Site Request Forgery)
