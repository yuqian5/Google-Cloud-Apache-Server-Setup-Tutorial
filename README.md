# GoogleCloudWebServerSetup
A Complete Tutorial on setting up a web server on Google Cloud Computing Instance.

## Menu

- [1. Obtain Domain Name](##getDomain)
- [2. Create Google Cloud VM Instance](##createVM)
- [3. Configure DNS](##setDNS)


## <a name="getDomain"></a> Obtain Domain Name

Go to https://domains.google.com/m/registrar/search 

Search for your desired domain name

Purchase domain name 

## <a name="createVM"></a> Create Google Cloud VM Instance

Go to page VM Instances (Navigation Menu > Compute Engine > VM Instances)

Click Create Instance (You may have to wait a few minutes if this is your first time using Google Cloud VM)

Configure your instance

![alt text](https://github.com/yuqian5/GoogleCloudWebServerSetup/raw/master/markdownMedia/createInstance.png "Instance Hardware Config")

Select your boot disk, in this tutorial we will be using the provided Ubuntu 18.04 LTS Minimal

<img src="https://github.com/yuqian5/GoogleCloudWebServerSetup/raw/master/markdownMedia/diskSelect.png" alt="alt text" width="469" height="274">

Allow http and https traffic in the firewall setting

<img src="https://github.com/yuqian5/GoogleCloudWebServerSetup/raw/master/markdownMedia/firewallSetting.png" alt="alt text" width="340" height="80">

Under the firewall setting, you should see a expandable section named "Management, security, disks, networking, sole tenancy"

Expand section and navigate to networking tab

In the Network Interface section, you should see a Default Setting, click on it to reveal more information

![alt text](https://github.com/yuqian5/GoogleCloudWebServerSetup/raw/master/markdownMedia/reserveStaticExternalIP.gif "Instance Hardware Config")

Now you can create the instance, it might take a few minutes



## <a name="setDNS"></a> Configure DNS

Go to page Cloud DNS (Navigation Menu > Network Services > Cloud DNS)

Create Zone

    Zone Type: Public
    Zone Name: myzone
    DNS Name: <your domain name>
    DNSSEC: ON
    
    Create
    
You should now see a page like this:

<img src="https://github.com/yuqian5/GoogleCloudWebServerSetup/raw/master/markdownMedia/initZone.png" alt="alt text" width="1000" height="370">









