Congratulations on completing Newb Relic! It was so great to have all of you in class :-)  

Now that Newb Relic is over, you should turn off the Synthetics monitors you created. Here are the steps:  
1. Log into newrelic.com  
2. Change to the account associated with your kata  
3. Open the Synthetics page  
4. Find your monitor in the list (you may have only one item in the list if you have not created other monitors)  
5. Hover over the gear icon on the right side of the page  
6. Click "Disable"    

If you want to get rid of you kata application on heroku, use the following commands:   
*heroku apps*  -- this will list your apps. Note the one that you use for the kata (You may have only one application listed).    
*heroku apps:destroy <application name>* -- substitute heroku's name of your kata for <application name>. For instance, *heroku apps:destroy gentle-hollow-1234* 
