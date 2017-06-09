# draft

# Deploy

<a href="https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fgwenblum%2Ftempwb%2Fmaster%2Fazuredeploy.json" target="_blank">
    <img src="http://azuredeploy.net/deploybutton.png"/>
</a>
<a href="http://armviz.io/#/?load=https%3A%2F%2Fraw.githubusercontent.com%2F%2Fgwenblum%2Ftempwb%2Fmaster%2Fazuredeploy.json" target="_blank">
    <img src="http://armviz.io/visualizebutton.png"/>
</a>

This template deploys scappfwk on a fresh linux VM. Tested woth Centos and Ubuntu.

1. Prepare your ssh public key to set in parameters

2. Click the "Deploy to Azure" button. 

3. Fill parameters 

Choose the linux distribution

4. Launch deployment

5. When deployment is done, check outputs
* ssh command
* URL

# Usage

(when deployment is done)

1. Connect with ssh (see outputs)

Ex. ssh scappfwkdev-admin@scappfwkdev-bcncuqdggmvjc.koreacentral.cloudapp.azure.com

2. Run the web server 

cd /appfwk_project ; sudo python runserver 0.0.0.0:8000

3. Launch your browser and connect to the URL (see outputs)

Ex. http://scappfwkdev-bcncuqdggmvjc.koreacentral.cloudapp.azure.com:8000
