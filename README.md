# Bluemix Hands-on Lab for IoT


This Lab Contains the steps to setup:

* A sample for Taxis which do sending their speed and location information.
* Setup the IBM Watson IoT

In the Lab you will use in IBM Bluemix:
* The *Node-RED Starter* _Boiler Template_ with contains a *Cloudant DB* and a *Node.JS Server*.
* [Node-RED Dashboard Package](https://github.com/node-red/node-red-dashboard)
* [Node-RED Virtual IoT Device Package](https://www.npmjs.com/package/node-red-contrib-iot-virtual-device)
* The *Watson IoT Service*
* A *Object Store Database*


## Setup the needed Application and services


1. Logon to your Bluemix Account and seach in catalog for Node-RED. You will find the *Node-RED Boiler Template* and click on the icon.

![Node-RED Boiler Template](images/01_Node-RED_Starter.jpg)

2. Now you can see the which application and services will be create. Give the application and route a name like taxi-simulartor-[YOUR-UNIQUE-NAME]. Here you can find the *Cloudant DB* and the *Node.JS Server* and *press create*.

![Node-RED Boiler Template Configuration](images/02_Node-RED_Starter-Setup.jpg)

3. After this step select the *Visit App URL* to get to the Running Node-RED instance on the Node.JS Server.

![Node-RED Boiler Template Visit URL](images/02_Node-RED_Starter-Visit-URL.jpg)

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
