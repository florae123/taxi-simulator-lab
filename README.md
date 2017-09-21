# Bluemix Hands-on Lab for IoT


This Lab Contains the steps to setup:

* A sample for Taxis which do sending their speed and location information.
* Setup the IBM Watson IoT

In the Lab you will use in IBM Bluemix:
* The **Node-RED Starter** _Boiler Template_ with contains a **Cloudant DB** and a **Node.JS Server**.
* We will add additional Nodes into the Node-RED instance [Node-RED Dashboard Node](https://flows.nodered.org/node/node-red-dashboard) and [Node-RED Virtual IoT Device Node](https://www.npmjs.com/package/node-red-contrib-iot-virtual-device)
* The **Watson IoT Service**
* A **Object Store Database**


## 1 Setup the needed Application and services

### 1.1 Setup and configure Node-RED

1. Logon to your Bluemix Account and seach in catalog for Node-RED. You will find the **Node-RED Boiler Template** and click on the icon.
![Node-RED Boiler Template](images/01_Node-RED_Starter.jpg)

2. Now you can see the which application and services will be create. Give the application and route a name like taxi-simulartor-[YOUR-UNIQUE-NAME]. Here you can find the **Cloudant DB** and the **Node.JS Server** and **press create**.
![Node-RED Boiler Template Configuration](images/02_Node-RED_Starter_Setup.jpg)

3. After this step select the **Visit App URL** to get to the Running Node-RED instance on the Node.JS Server.
![Node-RED Boiler Template Visit URL](images/02_Node-RED_Starter-visit-URL.jpg)

4. Now just **follow the steps in the wizard** to do the basic configuration of the Node-RED instance.
![Node-RED Boiler Template Follow the steps in the wizard](images/04_Node-RED_Follow_the_Steps_in_the_wizard.jpg)

5. Now inspect the landing page and press **Go to your Node-RED flow**.
![Node-RED Boiler Template Inspect the landing page and press go to node red_ ditor](images/05_Node-RED_Inspect_the_landing_page_and_press_go_to_node_red_editor.jpg)

6. Inside Node-RED we had to add the additional _Nodes_ we will use in our future flow. The [Node-RED Dashboard Package](https://flows.nodered.org/node/node-red-dashboard) and the [Node-RED Virtual IoT Device Package](https://www.npmjs.com/package/node-red-contrib-iot-virtual-device) . First select **manage palatte** from the menu on right upper side of the page.
![Node-RED_Select_Manage-Palette](images/06_Node-RED_Select_Manage-Palette.jpg)

7. Now choose the Tab **install** and search for the two Packages **node-red-dashboard** and **node-red-contrib-iot-virtual-device** and press install.
![Node-RED_Select_Manage-Palette](images/07_Node-RED_Install_nodes.jpg)

8. After the installation verify that following sections for the installed nodes will appear on the left hand side.
and press install.
![Node-RED_Select_Manage-Palette](images/08_Node-RED_List_of_installed_nodes.jpg)

### 1.2 Create and bind the remaining needed services



# Basic Git Command line instructions

## Git global setup

```
git config --global user.name "Thomas Südbröcker"
git config --global user.email "thomas.suedbroecker.2@de.ibm.com"
```
## Create a new repository

```
git clone git@git.ng.bluemix.net:thomas.suedbroecker.2/Bluemix-Hands-on-Workshop-IoT.git
cd Bluemix-Hands-on-Workshop-IoT
touch README.md
git add README.md
git commit -m "add README"
git push -u origin master
```

## Existing folder

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
