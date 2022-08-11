# IE-Cloud-Connector - Azure
Establish a connetion with Azure Cloud and send data to it using IE Cloud Connector

# Requirements

- Onboarded IED with the following apps:
  - IE Databus
  - IE Cloud Connector
  - IE Flow Creator
  - S7/OPC UA Connector (already configured)
- Working TIA Project to send the data
- Azure account
- Some coffee

# Getting started

The first thing we want to do is setup our Databus, for which we need to add a user and topic.

We will be using admin as user and password for this example as well as the topic ie/#.

![Add user](https://github.com/JustCapo/IE-Cloud-Connector.-Azure/blob/main/Images/IE_Databus.png)

Now we open the IE Cloud Connector, and in the Bus Adaptor area, select "Edit configuration". 
