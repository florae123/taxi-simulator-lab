# Bluemix Hands-on Lab for IoT

# Basic Git Command line instructions

This Lab Contains the steps to setup:

* A sample for Taxis which do sending their speed and location information.
* Setup the IBM Watson IoT

In the Lab you will use in IBM Bluemix:
* The Node-RED Boiler Template
* Node-RED Dashboard Package (https://github.com/node-red/node-red-dashboard)
* Node-RED Virtual IoT Device Package (https://www.npmjs.com/package/node-red-contrib-iot-virtual-device)
* The Watson IoT Service
* A Object Store Database


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
