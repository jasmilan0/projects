***** This project is being completed in Azure and RDP port will be exposed to the public to all of the VMs. <br />
***** If replicating this in real environment, make sure use of VPN or SASE is implemented.<br />
***** I will not be setting up the VPN access server to save time with the setup of this lab<br />

## Step 1: Create a new resource group(RG)
#### I am setting the regions of all resources in Central India to save cost.
![Screen Shot 2024-06-14 at 10 39 18 PM](https://github.com/jasmilan0/projects/assets/58121854/860186ef-39b2-4f7d-b349-481765efd36f)

## Step 2: Open the newly created RG and hit create 
![Screen Shot 2024-06-14 at 10 49 12 PM](https://github.com/jasmilan0/projects/assets/58121854/f2449303-b511-4953-bd04-c556b1a79197)

## Step 3: Search for "Virtual Network" by Microsoft
![Screen Shot 2024-06-14 at 10 51 32 PM](https://github.com/jasmilan0/projects/assets/58121854/4d93733d-1f6c-4477-9ea9-7629b20b907e)

## Step 4: Create the virtual network in the RG created
![Screen Shot 2024-06-14 at 10 52 55 PM](https://github.com/jasmilan0/projects/assets/58121854/92f36fd5-8031-44eb-831a-7e8f03ab5516)

***** I am skipping the security just because I will be removing this lab from Azure. AGAIN this is for testing *****

#### I created 4 subnets. For each subnet, I didn't configure "Private subnet, Security, Service Endpoints, Subnet Delegation or network policy for private endpoints". Skip tags and create the network
![Screen Shot 2024-06-14 at 10 58 14 PM](https://github.com/jasmilan0/projects/assets/58121854/25bbacb8-70e3-437e-ad99-94bcbfb78220)

## Step 5: In the RG, hit create > Search for virtual machine
![Screen Shot 2024-06-14 at 11 02 49 PM](https://github.com/jasmilan0/projects/assets/58121854/b9bf2502-3299-40c3-9c12-53ac835cce0e)

## Step 6: Configure the AD server as below
![Screen Shot 2024-06-14 at 11 05 16 PM](https://github.com/jasmilan0/projects/assets/58121854/8578a181-ccf2-4843-9e9b-e52341dec8fe)

#### Allow public inbound port and allow port 3389 for RDP

#### Disk Settings
![Screen Shot 2024-06-14 at 11 06 55 PM](https://github.com/jasmilan0/projects/assets/58121854/9fba3338-1b92-470c-8404-f174c730a9aa)

#### Network Settings
![Screen Shot 2024-06-14 at 11 07 46 PM](https://github.com/jasmilan0/projects/assets/58121854/fc1802af-db91-4e17-8352-b50a29be383f)

#### You can skip management, monitoring, advanced and tags

## Wait for everything to be deployed. This can take some time

## Step 7: Configure the NIC assigned to AD-Server
#### a) Select the NIC
![Screen Shot 2024-06-14 at 11 12 51 PM](https://github.com/jasmilan0/projects/assets/58121854/1602cfa8-f965-4c90-b91b-b940f0dc893c)

#### b) Select IP Configurations on the Nav Bar > Assign it a static IP
![Screen Shot 2024-06-14 at 11 13 34 PM](https://github.com/jasmilan0/projects/assets/58121854/09fba0b5-9f1c-4fc6-9f0a-fdfd7ff7a529)

## Step 8: Create a new NIC in the RG. This will be used for internal routing
![Screen Shot 2024-06-14 at 11 16 44 PM](https://github.com/jasmilan0/projects/assets/58121854/6bc6f245-fea7-497e-9d8c-9f3f735a8940)

#### Configure the following settings of the NIC, make sure the IPv4 address is static and set to 10.0.10.4
![Screen Shot 2024-06-14 at 11 48 40 PM](https://github.com/jasmilan0/projects/assets/58121854/54a67ddc-dae9-43e7-af20-bbc761276852)

## Step 9: Go into the Ad Server VM > Network Settings > And attach the NIC created. For this VM has to stopped and restarted later


***** Delete "Sales, HR and Tech Subnet". I forgot that we will be having DHCP server setup to assign to workstations *****

## Step 9: To access the AD Server VM, select the VM > Connect > Native RDP > Make sure prereqs are green > Download the RDP file
![Screen Shot 2024-06-14 at 11 39 42 PM](https://github.com/jasmilan0/projects/assets/58121854/7ebd2412-b064-4562-ac18-3395326ae119)


## CONFIGURATION OF AD SERVER

## Step 1: Open


