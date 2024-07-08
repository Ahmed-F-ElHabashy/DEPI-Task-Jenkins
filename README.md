# Depi-Jenkins
Jenkins Test
##Difference between Webhook and Poll SCM:

###Webhook: 
  A server initiates webhook requests when an event occurs. It's automatic and immediate.
###Poll SCM:
  A client initiates polling requests at set intervals, regardless of new events.
  
##When to Use Poll SCM:
  Polling is suitable when you don't need real-time updates because frequent updates can overwhelm your system, especially with rapidly changing data.

For instance, if your startup gains 100 new users per second and you want to display the total number of users on a big screen in your office, polling every 5 to 10 minutes for updates would be more manageable than updating with every single new user.
