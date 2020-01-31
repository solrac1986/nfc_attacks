The attacker uses javascript embedded in the website to gather location information. There are several third-party services that provides IP location information such as [ipinfo](https://ipinfo.io/), [freegeoip](http://freegeoip.net/).

```javascript
<script type="application/javascript">
  var ip_address = 0;
  $.getJSON("http://jsonip.com?callback=?", function (data) {
    alert("Your ip: " + data.ip);
    ip_address = data.ip;
  });

</script>
<script>
  jQuery(document).ready(function(){
      jQuery.get("http://ipinfo.io/ip_address", function (response)
                 {
                     var lats = response.loc.split(',')[0]; 
                     var lngs = response.loc.split(',')[1];
                     map = new GMaps({
                         el: '#map',
                         lat: lats, //latitude
                         lng: lngs //longitude
                     });

                 }, "jsonp");
  });
</script>
```
