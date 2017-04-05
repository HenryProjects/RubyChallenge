# Removing AWS Instances After Newb Relic Completes

Amazon charges New Relic for every minute the Amazon EC2 instances run, so it is important to disable the instances after Newb Relic is finished. To prevent visual clutter from unused instances, you may as well delete the instances at the same time you turn them off. AWS uses the "Terminate" state to mark an instance that will be deleted. These instructions walk you through removing AWS EC2 instances created for Newb Relic.

## Turning Off the Instructor Image
You probably want to keep the image you made for yourself so that you do not have to re-create it the next time you teach Newb Relic. Instructions in this section tell you how to turn off an instance without marking it for deletion.  

1. Go to aws.amazon.com
1. Sign in to the Console
1. Click the "EC2" icon in the "Compute" section  
1. Clck the link that says "X Running Instances", where "X" is the number of instances. For example, "14 Running Instances"  
1. Select your instance  
1. From the "Actions" drop down button at the top, select Instance State > Stop    
The icon will change to a spinning circle. After a few seconds, the state will change to "Stopped"  

## Removing Students' Images
The instructions in this section tell you how to remove the EC2 instances that were created for students in Newb Relic.

1. Notify the students that the instances are being removed and that they must shut down Synthetics monitors. An example email is in the [Email Template](#email) section.
1. Go to aws.amazon.com
1. Sign in to the Console
1. Click the "EC2" icon in the "Compute" section
1. Clck the link that says "X Running Instances", where "X" is the number of instances. For example, "14 Running Instances"
1. Select ONLY the instances that belong to students in Newb Relic. **Make sure you do not select your instructor instance.**
1. Fom the "Actions" drop down button at the top, select Instance State > Terminate.  
The icon will change to a spinning circle. After a few seconds, the state will change to "Terminated". Eventually, Amazon will remove the terminated resources and they will no longer show up in the list.

## <a name="email"> Email Template

```

Thanks to everyone for a great Newb Relic session! It is wonderful to see New Relic grow as a company by hiring such stellar people with great ideas!

I will be turning off the virtual servers you used this week. This means any Synthetics monitors hitting the applications will fail.

***If you created a Synthetics monitor, you should disable it.****

Here are the steps: 
1. Navigate to the Synthetics application (synthetics.newrelic.com)
2. Click the gear icon to the right of your monitor
3. Click Disable

```
