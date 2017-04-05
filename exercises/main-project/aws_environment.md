# Your Newb Relic Server
Before you start this exercise, the instructor will provide you with an instance of a virtual machine that has all of the code you need. This page will help you understand how to use the VM.

## Identifying your instance
The virtual machine is a Amazon Web Services (AWS) Elastic Computing Capabilities (EC2). There are three pieces of information about the machine you will need to note; your instructor will send you an email with these pieces of information: 
  * *newb-relic-master-key-pair.pem* -- This file has the certificate information needed to connect to your instance. Save it to a directory on your laptop. You will use it every time you connect to the instance.  
  * *Public DNS* -- This is the "address" you will use to connect to your instance.  
  * *Public IP address* -- This is the address you will use when you are testing your kata in your browser.

## How does this work
From your laptop, you will use ssh (**S**ecure **SH**ell) protocol to connect to the virtual server. You can then run commands on the virtual server to edit files and run a web server. The experience is very similar to using a Terminal window on your laptop. 

When you are testing the Ruby application (aka the "kata"), the application code will be running on the web server inside the virtual server. You will connect to it from a web browser on your laptop.  


![Diagram of Laptop and Virtual Server](images/AWS_Explain.png)

## Connecting to your instance
  You will use ssh to access the instance. The ssh command uses the information in the newb_relic_instance_key.pem file as login credentials.
  1. Open a terminal window on your laptop.
  1. Change to the directory where your newb_relic_instance_key.pem file is stored.
  1. Run this command to set the proper permissions on the .pem file:  
    ```chmod 400 newb-relic-master-key-pair.pem```
  1. Run this command, replacing "AMAZON INSTANCE PUBLIC DNS" with the Public DNS the instructor supplied: 
    ```ssh -i newb-relic-master-key-pair.pem ec2-user@AMAZON INSTANCE PUBLIC DNS```
  1. Type **yes** if you are warned that the authenticity of the host cannot be established.

## Test it

Now that you have your container setup, it's time to make sure that everything is working appropriately. You'll need to get the rails server started and then view the website from your browser.

1. Change to the directory for the kata:
```cd /home/ec2-user/newrelic-ruby-kata-newb-relic-master/```
1. Note that this is a Ruby On Rails application, with the standard layout of source files.
1. Start the rails server from the newrelic-ruby-kata-newb-relic-master directory:  
   ```rails server -b 0.0.0.0```
1. In your web browser, open the Ruby kata, using the IP address supplied for your virtual server. For instance: ```http://[PUT YOUR IP ADDRESS HERE]:3000```  

If you can get the New Relic Ruby Kata up and running, then congrats you win! 

  Once you have connected, you are ready to [continue with the exercise](readme.md)
  
