# draft scappfwk

## Description

This template deploys Steelscript Application Framework on a fresh linux VM for development purpose. The deployment has been tested on Centos and Ubuntu linux VM.

Link to the Steelscript Application Framework reference for developpers: https://support.riverbed.com/apis/steelscript/appfwk/toc.html

## Quick deploy

<a href="https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fgwenblum%2Ftempwb%2Fmaster%2Fazuredeploy.json" target="_blank">
    <img src="http://azuredeploy.net/deploybutton.png"/>
</a>
<a href="http://armviz.io/#/?load=https%3A%2F%2Fraw.githubusercontent.com%2F%2Fgwenblum%2Ftempwb%2Fmaster%2Fazuredeploy.json" target="_blank">
    <img src="http://armviz.io/visualizebutton.png"/>
</a>

1. Click the "Deploy to Azure" button, fill parameters and launch the deployment
    Set your ssh public key to connect to the VM
    Select the VM size
    Choose the linux distribution

2. When deployment is done, 
    The deployment takes less than 25min.
    Connection strings the deployment outputs show get connection strings in the deployment outputs
    * ssh command
    * URL

## Usage

*(when deployment is done)

### Launch your browser and connect to the URL

    You can get URL in the Deployment outputs
    Ex. http://scappfwkdev-bcncuqdggmvjc.koreacentral.cloudapp.azure.com:8000

### Connect to the VM using ssh

    You can get the command in the Deployment outputs
    Ex. ssh scappfwkdev-admin@scappfwkdev-bcncuqdggmvjc.koreacentral.cloudapp.azure.com

### Manually start the web server 

    After the deployment, the server is running, thus it will not automatically start if your restart the VM.
    You can connect to the VM using ssh and start the web server:    
    $ cd /appfwk_project ; sudo python runserver 0.0.0.0:8000 
    
## Troubleshooting

### Check installation log in the VM
$ sudo cat /var/log/azure/custom-script/handler.log
$ sudo cat /var/log/azure/custom-script/handler.log

### Identify appfwk webserver processes running in background
$ ps -eo pid,command | grep "appfwk_project/manage.py" | grep -v grep
45530 sudo python /appfwk_project/manage.py runserver 0.0.0.0:8000
45533 python /appfwk_project/manage.py runserver 0.0.0.0:8000
45540 /bin/python /appfwk_project/manage.py runserver 0.0.0.0:8000

### Stop appfwk webserver running in background (kill processes)
$ sudo kill $(ps -eo pid,command | grep "appfwk_project/manage.py" | grep -v grep | awk '{ print $1 }')
