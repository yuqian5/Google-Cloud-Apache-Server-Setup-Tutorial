# Google Cloud Apache Server Setup
A Complete Tutorial on setting up a web server on Google Cloud Computing Instance.

## Menu

- [1. Obtain Domain Name](#getDomain)
- [2. Create Google Cloud VM Instance](#createVM)
- [3. Configure DNS](#setDNS)
- [4. Install LAMP Stack on VM Instance](#lamp)
- [5. Verify](#veri)


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

Follow the gif below to reserve a static external IP address

<img src="https://github.com/yuqian5/GoogleCloudWebServerSetup/raw/master/markdownMedia/reserveStaticExternalIP.gif" alt="alt text" width="460" height="340">

Save that external ip address somewhere, we will need to use it later when we configure the DNS settings

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

Click add record set

Leave everything as default except the ipv4 address, where we will fill it with the static external ip address that we got from the previous steps

Now you should see a screen like this 

<img src="https://github.com/yuqian5/GoogleCloudWebServerSetup/raw/master/markdownMedia/addedRecord.png" alt="alt text" width="1000" height="370">

Your DNS zone is now complete

Go to https://domains.google.com/m/registrar/yourDomainName
    
Go to the page DNS (from left menu bar)

In the name server section, select Use custom name servers

Add name server, as shwon in your zone

<img src="https://github.com/yuqian5/GoogleCloudWebServerSetup/raw/master/markdownMedia/dns1.png" alt="alt text" width="1000" height="370">

It should take anywhere from 2 - 24 hr for the DNS change to propagate

## <a name="lamp"></a> Install LAMP Stack on VM Instance

Run the following command:

    // install apache 2
    sudo apt update
    sudo apt install apache2
    
    // install mySQL
    sudo apt install mysql-server
    
    // install 
    sudo apt-get install php libapache2-mod-php php-mysql 
    
    // restart apache
    sudo systemctl restart apache2
    
## <a name="veri"></a> Verify

Now to verify that you have done everything correctly, go to your brower and type in your domain name

You should see the following page:

![alt text](https://github.com/yuqian5/GoogleCloudWebServerSetup/raw/master/markdownMedia/apacheDefault.jpg "Instance Hardware Config")





