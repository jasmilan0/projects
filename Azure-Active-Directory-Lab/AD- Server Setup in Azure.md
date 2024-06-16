***** This project is being completed in Azure and RDP port may be exposed to the public  <br />
***** If replicating this in real environment, make sure use of VPN/Bastion/SASE is implemented.<br />
***** I will not be setting up the VPN access server to save time with the setup of this lab<br />
***** I will not be setting up DHCP server since entire setup is done in the cloud

## Step 1: Create a resource group(RG)
<img width="894" alt="Screen Shot 2024-06-16 at 4 33 49 PM" src="https://github.com/jasmilan0/projects/assets/58121854/aaa657f5-a3eb-4694-8f95-02820d7fe724">

## Step 2: Create a virtual network in that RG
<img width="886" alt="Screen Shot 2024-06-16 at 4 39 16 PM" src="https://github.com/jasmilan0/projects/assets/58121854/ccdacd41-4815-49f4-9ce7-86497931c721">

<img width="897" alt="Screen Shot 2024-06-16 at 4 43 07 PM" src="https://github.com/jasmilan0/projects/assets/58121854/b627aa27-9111-4a18-b987-db209ab5e7c5">

## Step 3: Create a virtual machine for the AD Server
<img width="899" alt="Screen Shot 2024-06-16 at 4 49 41 PM" src="https://github.com/jasmilan0/projects/assets/58121854/82df34b5-dd90-4e43-a70b-356e4ed4b3c0">

<img width="895" alt="Screen Shot 2024-06-16 at 4 50 00 PM" src="https://github.com/jasmilan0/projects/assets/58121854/89ade3a4-47e1-4d8e-b4e3-ac0441a71df6">

<img width="844" alt="Screen Shot 2024-06-16 at 4 50 19 PM" src="https://github.com/jasmilan0/projects/assets/58121854/4470b76c-dcfa-4031-b264-0bf424c1f1b6">

<img width="870" alt="Screen Shot 2024-06-16 at 4 50 58 PM" src="https://github.com/jasmilan0/projects/assets/58121854/ffb216a0-34be-4a4e-a74e-581a26b22b81">

<img width="852" alt="Screen Shot 2024-06-16 at 4 52 42 PM" src="https://github.com/jasmilan0/projects/assets/58121854/07162a11-6bbf-47b0-ad32-e14d5e41c97b">

<img width="824" alt="Screen Shot 2024-06-16 at 4 52 58 PM" src="https://github.com/jasmilan0/projects/assets/58121854/7218a30f-18bc-45fe-94a7-ae95a0bbf6af">

#### I skipped the monitoring and management tab and left it default for this AD-Server-VM

## Step 4: Connect to the VM using Bastion or native RDP if you allowed public inbound access to port 389
#### I am using Bastion because it is convenient to use via the browser.

## Step 5: Add ADDS and DNS Server via Server Manager which opens by default
#### Select Add roles and features
<img width="408" alt="Screen Shot 2024-06-16 at 5 52 40 PM" src="https://github.com/jasmilan0/projects/assets/58121854/76f65271-4296-4556-953a-d6ccd03c149a">

<img width="789" alt="Screen Shot 2024-06-16 at 5 53 34 PM" src="https://github.com/jasmilan0/projects/assets/58121854/b086c460-f44f-4f26-a8a8-8ebba86d31d4">

<img width="785" alt="Screen Shot 2024-06-16 at 5 54 56 PM" src="https://github.com/jasmilan0/projects/assets/58121854/4d0ebaa6-74a6-44c3-9e87-37552e1316d8">

<img width="783" alt="Screen Shot 2024-06-16 at 5 55 44 PM" src="https://github.com/jasmilan0/projects/assets/58121854/ca498703-6649-470d-81ef-fc4dee1f3981">

#### Hit next on "Features", "AD DS", "DNS Server", and then hit Install

#### Once installed, you have to promote the server to Domain Controller

<img width="464" alt="Screen Shot 2024-06-16 at 6 00 41 PM" src="https://github.com/jasmilan0/projects/assets/58121854/01bb51e8-4e22-4ce4-b915-7606bd529af4">

<img width="763" alt="Screen Shot 2024-06-16 at 6 01 14 PM" src="https://github.com/jasmilan0/projects/assets/58121854/bdf21153-647b-4403-bbc2-d82f575d346d">

<img width="762" alt="Screen Shot 2024-06-16 at 6 01 38 PM" src="https://github.com/jasmilan0/projects/assets/58121854/6d83f25b-053b-43b4-bd1a-56bccc63ef3d">

#### Skip DNS delegation
#### I used the default NETBIOS NAME and file path and then install 
#### VM will restart

## Step 6: Make sure the IP for AD Server NIC is static
#### This has to be configured via Azure and will require to restart the AD-Server VM

#### Go into the RG > select the AD server NIC
<img width="1431" alt="Screen Shot 2024-06-16 at 6 11 27 PM" src="https://github.com/jasmilan0/projects/assets/58121854/f26fdbd8-641a-453a-94d4-d63be1ca9457">

#### Restart the AD-Server VM

## ----------------------------------------------------------- ##

#### Now we will create a subnet for client workstations
#### This will be in a different page
