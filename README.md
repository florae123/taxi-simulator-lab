# Bluemix Hands-on Lab for IoT Creating a Taxi-Simulartor

In this Lab you will create a **Taxi-Simulartor** for IoT. This Taxi-Simulator will create sample data for a Data Analytics part, in one of the following Hands-on Labs.

The objective is you will get a basic understanding of the IBM IoT and
customize your own flow in Node-RED, using the give given IoT Data to display in your Node-RED Dashboard.

**Functionality of the existing Node-RED flow**

1. The simulator will create different Taxi devices inside the Watson IoT Platform.
2. You can choose the count of the taxis you want create.
3. A created taxi will simulate speed and geolocation and the created data will be stored in a database.

**This Hands-on Lab Contains the following steps**

*a) Setup:*
* A simulator for Taxis, which do sending their speed and location information.
* Setup the IBM Watson IoT

*b) Create your own Node-RED flow*
* Use Watson IoT as input in your flow
* Use the Node-RED for implementing some logic and UI

**In the Hands-on Lab  you will use in IBM Bluemix:**

* The **Node-RED Starter** _Boiler Template_ with contains a **Cloudant DB** and a **Node.JS Server**.
* You will add additional nodes into the Node-RED instance [Node-RED Dashboard Node](https://flows.nodered.org/node/node-red-dashboard), [Node-RED Virtual IoT Device Node](https://www.npmjs.com/package/node-red-contrib-iot-virtual-device), [Node-RED Objectstore](http://flows.nodered.org/node/node-red-contrib-objectstore) and [Node-RED MessageHub](https://flows.nodered.org/node/node-red-contrib-messagehub)
* The [Watson IoT Service](https://console.bluemix.net/catalog/services/internet-of-things-platform?env_id=ibm%3Ayp%3Aus-south)
* The [Object Store Database](https://console.bluemix.net/catalog/services/Object-Storage?env_id=ibm%3Ayp%3Aus-south)
* The [Message Hub](https://console.bluemix.net/catalog/?context=services&app=bdd3e76c-09b7-47a6-8515-50c7e6b477e9&env_id=ibm%3Ayp%3Aeu-gb&search=Message%20Hub)

# 1 Setup the needed Application and services

In the part of the Lab you will setup and configure the environment, we will use for you Taxi-Simulartor.

### 1.1 Setup and configure Node-RED

1. Logon to your Bluemix Account and search in catalog for Node-RED. You will find the **Node-RED Boiler Template** and click on the icon.
![Node-RED Boiler Template](images/01_Node-RED_Starter.jpg)

2. Now you can see the which application and services will be create. Give the application and route a name like **taxi-simulartor-[YOUR-UNIQUE-NAME]**. Here you can find the **Cloudant DB** and the **Node.JS Server** and press **create**.
![Node-RED Boiler Template Configuration](images/02_Node-RED_Starter_Setup.jpg)

3. After this step select the **Visit App URL** to get to the Running Node-RED instance on the Node.JS Server.
![Node-RED Boiler Template Visit URL](images/03_Node-RED_Starter-visit-URL.jpg)

4. Now just **follow the steps in the wizard** to do the basic configuration of the Node-RED instance.
![Node-RED Boiler Template Follow the steps in the wizard](images/04_Node-RED_Follow_the_Steps_in_the_wizard.jpg)

5. Now inspect the landing page and press **Go to your Node-RED flow editor**.
![Node-RED Boiler Template Inspect the landing page and press go to node red_ ditor](images/05_Node-RED_Inspect_the_landing_page_and_press_go_to_node_red_editor.jpg)

6. Inside Node-RED we had to add the additional _Nodes_ we will use in our future flow. The [Node-RED Dashboard Package](https://flows.nodered.org/node/node-red-dashboard) and the [Node-RED Virtual IoT Device Package](https://www.npmjs.com/package/node-red-contrib-iot-virtual-device) . First select **manage palatte** from the menu on right upper side of the page.
![Node-RED_Select_Manage-Palette](images/06_Node-RED_Select_Manage-Palette.jpg)

7. Now choose the Tab **install** and search for each of these four nodes **node-red-dashboard**, **node-red-contrib-iot-virtual-device**, **node-red-contrib-objectstore**, **node-red-contrib-messagehub** and press install.
![Node-RED_Select_Manage-Palette](images/07_Node-RED_Install_nodes.jpg)

8. After the installation verify that following sections for the installed nodes will appear on the left hand side.
![Node-RED_Select_Manage-Palette](images/08_Node-RED_List_of_installed_nodes.jpg)

### 1.2 Create and bind the remaining needed Bluemix services

**Watson IoT and MessageHub**

1. Go back to your bluemix application and select on the left hand side **connections** and press **connect new**.
![Bluemix-services_add](images/01_Bluemix_services_add.jpg)

2. Search for the Watson IoT Service by insert in the catalog search **Internet of Things Platform** and press on the service.
![Bluemix-services_search](images/02_Bluemix_services_search.jpg)

3. For the service name insert following name **taxi-simulartor-InternetOfThingsPlatform** and press **create**. Do **NOT** select restage for now.
![Bluemix-services_add_iot](images/02_Bluemix_services_add_iot.jpg)

4. Repeat the steps 1 to 3 for the Service **MessageHub**

**Cloud object storage**

1. Now open the Bluemix catalog directly.
![Bluemix-services_catalog](images/04_Bluemix_services_catalog.jpg)

2. Search for the **Cloud Object Storage** directly in the catalog and select in this infrastructure component the **Bluemix Storage Swift**.
![Bluemix-services_cloud_object_storage](images/05_Bluemix_services_cloud_object_storage.jpg)

3. Name the service like this **taxi-simulator-ObjectStorage** and press create. _NOTE:_ You can only use **ONE** instance per **ORAGNIZATION** of **Cloud Object Storage**.                       
![Bluemix-services_create_object_storage](images/06_Bluemix_services_create_object_storage.jpg)

4. Open your Bluemix Application in the Bluemix Dashboard and select **connections**.

5. Then select **connect existing** and search for your just created **Cloud Object Storage for Bluemix** service. If you are now ask to restage the application press **OK**.

6. Alter this steps have connected services look like in the following picture. In my case I have a different name for the **cloud object storage** service.                               
![Bluemix-services_connected_services](images/07_Bluemix_services_connected_services.jpg)

# 2 Configure the needed services and apply changes to the Node-RED flow

## 2.1 Import existing Node-RED flow

**Copy the prepared Node-RED flow into the your Node-RED instance**

1. Open the file **Lab_start_20170928.json** in GitHub and all select the the content into the clipboard

2. Inside Node-RED select **Menu->Import->Clipboard**
![Node-RED_Import_node_red_flow_01](images/15_Node-RED_Import_node_red_flow_01.jpg)

3. Take look into the three tabs
![Node-RED_Import_node_red_flow_02](images/16_Node-RED_Import_node_red_flow_02.jpg)

## 2.3 Configure the Watson IoT inside the Node-RED Taxi-Simulation Tab

Create a app API-Key inside the Watson IoT Service and insert the information inside the existing Node-RED flow.

1. Open the existing Watson IoT Service and press launch
![Watson_IoT_open](images/01_Watson_IoT_open.jpg)

2. Create a new application API-Key inside Watson IoT by pressing **Generate API Key**
![Watson_IoT_app_key_01](images/02_Watson_IoT_app_key_01.jpg)

3. Change API Role to **Backend Trusted Application** and insert as comment **Taxi-Simulation**.
**NOTE: DON'T CLOSE THIS WINDOW!!!**
![Watson_IoT_app_key_03](images/03_Watson_IoT_app_key_03.jpg)

4. Now copy and paste API Key and Authentication Token into  the Node-RED flow in Tab **Configure-TaxiSimulation**, by open the function node **set predefined config for Watson IoT** and replace the existing **API Key** and **API Token** with your value. Use **API Key** for **Username** and **API Token** for **Password**.
```
/* Watson IoT:
   ============
   Organization: XXXX
   API Key  :    a-XXXX-twkonxv5oo
   API Token:    XX+0xANGIYdQG&SdXI
*/

flow.set("orgid", "XXXX");
flow.set("instances","2");
flow.set("username", "a-XXXX-twkonxv5oo");
flow.set("password", "XX+0xANGIYdQG&SdXI");
return msg
```

5. The Organization ID you can find in the right upper corner of the Watson IoT WebPage.
![Watson_IoT_app_key_04](images/04_Watson_IoT_app_key_04.jpg)


2. Insert the application token into the IoT node inside the Node-RED flow

# 3 Use Watson IoT input to Node-RED

0. You will start with this flow                                           
![Node-RED start with own flow](12_Node-RED_Start_own_flow.jpg)

1. Create IoT input node

2. Configure IoT input node.                                             
![Node-RED configure iot input node](images/11_Node-RED_Configure_iot_input_node.jpg)

4. Add debug node and make a connection to the IoT input node

5. Add a switch node

6. Insert in the switch node into property the string **payload.d.velocity** and add a rules for > 50 and <50.              
![Node-RED configure switch node](images/10_Node-RED_Configure_switch_node.jpg)

7. Create a new debug node and connect each output of the switch node.              
![Node-RED configure connect switch to debug](images/12_Node-RED_Connect_debug_to_switch.jpg)

8. Create a new function node to build a text message in case of danger.        
![Node-RED Function node danger](images/13_Node-RED_Function_node_danger.jpg)
```
  // Danger
  msg.payload = "The velocity of " + msg.payload.d.velocity + " of the Taxi is to high!";
  return msg;
```

9. Create a two additional function nodes; one to build a text message in case of safe status and one for forward all data and insert following code.          
![Node-RED All function nodes](images/14_Node-RED_All_function_nodes.jpg)
```
  // Safe
  msg.payload = "The velocity is " + msg.payload.d.velocity + ".";
  return msg;
```
```
  // All
  msg.payload = msg.payload.d.velocity;
  return msg;
```


# 4 Basic Git Command line instructions

## 4.1 Git global setup

```
git config --global user.name "Thomas Südbröcker"
git config --global user.email "thomas.suedbroecker.2@de.ibm.com"
```
## 4.2 Create a new repository

```
git clone git@git.ng.bluemix.net:thomas.suedbroecker.2/Bluemix-Hands-on-Workshop-IoT.git
cd Bluemix-Hands-on-Workshop-IoT
touch README.md
git add README.md
git commit -m "add README"
git push -u origin master
```

## 4.3 Existing folder

```
cd existing_folder
git init
git remote add origin git@git.ng.bluemix.net:thomas.suedbroecker.2/Bluemix-Hands-on-Workshop-IoT.git
git add .
git commit -m "Initial commit"
git push -u origin master
```

## Existing Git repository

```
cd existing_repo
git remote add origin git@git.ng.bluemix.net:thomas.suedbroecker.2/Bluemix-Hands-on-Workshop-IoT.git
git push -u origin --all
git push -u origin --tags
```
