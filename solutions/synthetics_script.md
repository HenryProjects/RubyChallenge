```

/**
 * Feel free to explore, or check out the full documentation
 * https://docs.newrelic.com/docs/synthetics/new-relic-synthetics/scripting-monitors/writing-scripted-browsers
 * for details.
 */

var assert = require('assert');
//CHANGE THE LINE BELOW TO MATCH THE IP ADDRESS OF YOUR AMAZON INSTANCE
var ip_address = '54.69.116.25';


visit('loop', 'The Loop');  
visit('big_list', 'The Big List');  
visit('tweets', 'The Tweets');  
visit('caching', 'The Cache');  
visit('async', 'The Async');  
visit('many_assets', 'The Many Assets');  
visit('errors', 'The Errors');  

function visit(page, header) {  
  $browser.get('http://' + ip_address + ':3000/'+ page).then(function(){  
  // Check the H1 title matches "Example Domain"  
   $browser.findElement($driver.By.css('h1')).then(function(element){  
     element.getText().then(function(text){    
      assert.equal(header, text, 'Page H1 title did not match. Expected "' + header +'". Got: ' + text);  
     });  
   });  
 });  
}  
```
