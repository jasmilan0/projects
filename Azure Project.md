## Step 1: Create a Resource Group

#### Make sure the region same with other resources that are going to be created.
<img width="1440" alt="Create a resource group" src="https://user-images.githubusercontent.com/58121854/189464303-e31c832f-c170-4140-acad-1b5dfc23fba6.png">


## Step 2: Create a Virtual Network

#### a) In the search bar, search for virtual network, make sure it is not virtual network gateway. Link it to the correct resource group and make sure the region is same throughout.
<img width="1440" alt="Create virtual network" src="https://user-images.githubusercontent.com/58121854/189766907-46a8a908-7aba-40ea-bdc0-a0e3cf547240.png">

#### b) For the IPv4 address, you can leave it default. For the subnets, click the default name and name it accordingly. In this scenario, I named it accountants. I changed the default subnet address range from 10.0.0.0/24 to 10.0.1.0/24. You can leave it default but I prefer it this way. 
<img width="1440" alt="Create virtual network" src="https://user-images.githubusercontent.com/58121854/189767007-d5b7e821-adf9-462e-824b-2da774e3403d.png">

#### c)You can leave security as it is. These are paid services that are very beneficial and are recommended. However, because cost can be a factor for some businesses have it disabled. For tags, you can skip it, after that review your configurations and create it. 
<img width="1440" alt="Create virtual network" src="https://user-images.githubusercontent.com/58121854/189767228-901c6def-6e72-4d4a-b8c1-9a574308d41f.png">

#### d) I forgot to create another subnet for the VPN, so what we are going to do is after the deployment is created, open the resource group, select the virtual network, go under subnets, and click add. Name it VPN, give it either the default subnet range, or in my example, give it 10.0.2.0/24. After that, save it.
<img width="1440" alt="Add subnet" src="https://user-images.githubusercontent.com/58121854/189767290-938f2b7c-5371-4b3e-b29a-60d43ea4ad48.png">


## Step 3: Downloading and Configuring OpenVPN access server

#### a) Go to the search bar and download OpenVPN access server. Make sure it is by OpenVPN and not by other parties providing the access. 
<img width="1440" alt="Screen Shot 2022-08-27 at 10 40 40 AM" src="https://user-images.githubusercontent.com/58121854/189767440-627b6797-c5e3-44ff-9603-fa58be24f5bf.png">

 #### b) Again make sure the resource group is properly selected. For the admin account, you can create the SSH public key but I prefer the password. 
 <img width="498" alt="Screen Shot 2022-08-27 at 10 44 02 AM" src="https://user-images.githubusercontent.com/58121854/189771708-b9ebf6e3-2e7c-4da5-89a0-e0f482c26a43.png">

#### c) For disks, I am going to use a Standard HDD because of costs. Preferably, premium sdd is recommended
<img width="1440" alt="Screen Shot 2022-08-27 at 10 45 41 AM" src="https://user-images.githubusercontent.com/58121854/189771762-7b7230f1-0768-4092-a9b3-f5a44320d986.png">

#### d) Configure the network. Make sure you select the subnet as the VPN we configured.
<img width="1440" alt="Create a virtual machine" src="https://user-images.githubusercontent.com/58121854/189772019-796eeec1-4901-4370-a535-607a8707beb7.png">

#### e) Under management, you can configure it for auto-shutdown. This will save costs. For this demonstration, I will leave it off. I am also going to skip advanced and tags.

#### f) After that hit create. 


