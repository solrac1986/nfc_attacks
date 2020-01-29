# Location

In modern browsers, the location collection via Javascript requires users' interaction with a location-notification message. For these cases, a much simpler approach can be used by the attacker. The attacker knows the location of the NFC tags, therefore, the physical location (latitude and longitude) can be inserted as parameters in the URL. 


```
http://localhost:8888?lat=1&long=3
```

```php
<?php
$value = 'something from somewhere a cookie 3';
setcookie("TestCookie", $value);
$parts = parse_url($url);
echo $_GET["lat"];
echo $_GET["long"];
?>
<html>
 <head>
  <title>PHP Test</title>
 </head>
 <body>
   <?php echo '<p>Hello World</p>'; ?>
   <?php echo $_COOKIE["TestCookie"]; ?>
 </body>
</html>
```
