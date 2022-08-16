# IE-Cloud-Connector - Azure

This is an example tailored to establish a connetion with Azure Cloud and send data to it using IE Cloud Connector.

# Requirements

- Onboarded IED with the following apps:
  - IE Databus.
  - IE Cloud Connector.
  - IE Flow Creator.
  - S7/OPC UA Connector (already configured and working).
- Working TIA Project to send the data.
- Azure account.
- Coffee and good music.

# Getting started

## Creating client in Azure

If you already have your Azure Hub/ Storage/ Client, you can [skip to the IED setup](#setting-up-our-ied). Otherwise, go to https://portal.azure.com/. 

### Create Azure HUB

If there is an already available HUB, we should use it instead of creating a new one, you can check on the Azure homepage for the IoT HUB option (you can also type it in the search bar), otherwise select the ***+ Create a resource*** button. From the Categories menu, select Internet of Things then IoT Hub. On the *Basics* tab, complete the fields as follows:

- Subscription: Select the subscription to use for your hub.

- Resource group: Select a resource group or create a new one. To create a new one, select Create new and fill in the name you want to use. It would be best to select an already existing one.

- Region: Select the region in which you want your hub to be located. Select the location closest to you.

- IoT hub name: Enter a name for your hub. This name must be globally unique, with a length between 3 and 50 alphanumeric characters. The name can also include the dash ('-') character.

We can stay with the rest of the settings as they are for this example. Proceed to *Review + Create*.

### Register new device

To register a new device, go to the Hub, and under *Device management* select *devices*. Click on *+Add device*. Give it a name and leave the settings as they are (symmetric key/ auto generate keys checked/ enable).

## Setting up our IED

### IE Databus

The first thing we want to do is setup our Databus, which will work as our MQTT server, for which we need to add a user and topic.

We will be using admin as user and password for this example as well as the topic ie/#.

![Add user](https://github.com/JustCapo/IE-Cloud-Connector.-Azure/blob/main/Images/IE_Databus.png)

### IE Cloud Connector

Now we open the IE Cloud Connector, and in the Bus Adaptor section, select *Edit configuration*.
The fields to fill are as follows:
- Client ID: Unique identifier of the cloud connector MQTT client which connects to an MQTT Server.
- Host: Hostname of the MQTT server, which the cloudd client connects to. Default is ie-databus.
- Port number: Port number of the MQTT server, which the cloud client connects to. Default is 1883.
- Topic for subscription: Topic name to receive data from the MQTT server.
- QOS for subscription: The Quality of Service (QoS) level is an agreement between the sender of a message and the receiver of a message that defines the guarantee of delivery for a specific message. We can leave it an 1 for this example.
- Username/Password: These are the username and password of the subscription topic in the MQTT server, so they will be the same admin/admin we used for the Databus.

![](https://github.com/JustCapo/IE-Cloud-Connector.-Azure/blob/main/Images/IE_CC_Databus.png)

Next we head up for the Cloud Client. Here we will click on *Add client* and type in a unique name for our client. Then choose type Azure because it would be quite strange choosing AWS/ for an Azure guide now, wouldn't it?

![](https://github.com/JustCapo/IE-Cloud-Connector.-Azure/blob/main/Images/IE_CC_Client.png)

After this, let's edit the client's configuration, by clicking on the edit symbol right next to it.

EXPLAIN HERE WHAT'S LEFT. SAS TOKEN

![](https://github.com/JustCapo/IE-Cloud-Connector.-Azure/blob/main/Images/IE_CC_ClientConfig.png)

Following that, we now click on "Add Route" in the *Connecting Routes* section. We give it a unique name, and save.

![](https://github.com/JustCapo/IE-Cloud-Connector.-Azure/blob/main/Images/IE_CC_AddRoute.png)

Click on top of the newly created route's name, and select the previously created topic and client. Click *Save Route*.

![](https://github.com/JustCapo/IE-Cloud-Connector.-Azure/blob/main/Images/IE_CC_SaveRoute.png)

### Azure IoT Explorer

https://github.com/Azure/azure-iot-explorer

### Device Explorer

https://github.com/Azure/azure-iot-sdk-csharp/releases/tag/2018-3-13

