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


## Step 4: Configuring the access server

#### a) After the deployment is complete we are going to configure the access server. I have a Mac so I will be using terminal. 

#### b) Copy the Public IP address of the access server virtual machine.
<img width="1425" alt="Screen Shot 2022-09-12 at 7 11 16 PM" src="https://user-images.githubusercontent.com/58121854/189774003-d782deb3-e019-43ea-9f75-90094de519d8.png">

#### c)Run this command “ssh username@publicIPAddress”
<img width="558" alt="Screen Shot 2022-09-12 at 7 12 13 PM" src="https://user-images.githubusercontent.com/58121854/189774103-85a76169-ace6-45fb-8837-5f5e3bcbff56.png">

#### d) Type yes and enter your password you had set.
<img width="564" alt="Screen Shot 2022-09-12 at 7 13 19 PM" src="https://user-images.githubusercontent.com/58121854/189774211-6623366c-d387-45f6-8eeb-7ea4f4c2633c.png">

#### e) Agree to the agreement.

#### f) When configuring the initial settings leave everything default. 
<img width="855" alt="Press ENTER" src="https://user-images.githubusercontent.com/58121854/189774322-04350a51-b8d9-44f4-9d64-142733219fa2.png">

<img width="516" alt="Initial Configuration Complete!" src="https://user-images.githubusercontent.com/58121854/189774370-f03668a6-6acc-471a-b678-0c877672d058.png">

#### g) Change the password of the user we just created
<img width="402" alt="client1@openvpnas2-$ sudo passwd openvpn" src="https://user-images.githubusercontent.com/58121854/189774404-0cc645a5-1265-46b4-bcef-083fc9902189.png">

#### h) Once it Is set up, it will say to access OpenVPN via urls. These URLs will not work because they are local IP. To configure the rest of the settings, use the Public IP address. Another thing, Google Chrome will not let you access the public IP address because there is no valid certificate. However, Safari lets you.

#### i) Go to the search bar and enter your public IP address "https://public.ip.address"

#### j) Click “visit this website”. Download the OpenVPN Connect. After downloaded go the admin sign in page. The username would be “openvpn” and whatever password you set as. 
<img width="956" alt="This Connection Is Not Private" src="https://user-images.githubusercontent.com/58121854/189774696-d8a8269e-34e4-4d61-9e4a-5601ac00b5e4.png">

#### k) Under configuration and network settings, change the host name from the local ip to the Public IP address Azure assigned to the openvpn access server virtual machine. 
<img width="1250" alt="Server Network Settings" src="https://user-images.githubusercontent.com/58121854/189775141-c40ecd71-335f-41d3-b4bf-94048e813336.png">

#### l) As you scroll down to the client web server, make the changes as it appears on the image.
<img width="1165" alt="Screen Shot 2022-09-12 at 7 24 07 PM" src="https://user-images.githubusercontent.com/58121854/189775233-0a365dfd-a681-46fe-804e-b1d9bcd0b242.png">

#### m) Save the changes and on the top it will say update running server. Make sure to select that option otherwise if logged out it will not update and you would have to start all over. 

#### n) Under Configuration and VPN settings, specify which subnets computers able to have. Since we created the accountant subnet, we are going to specify the accountant subnet.
<img width="1014" alt="Screen Shot 2022-09-03 at 10 02 20 AM" src="https://user-images.githubusercontent.com/58121854/189775815-533949a1-de97-480c-9cd8-421254d8a4d9.png">

#### o) Save the changes and update the server


## Step 5: Adding a virtual machine to the accountant subnet

#### a) Create a new virtual machine. Make sure the right resource group is selected
<img width="579" alt="Screen Shot 2022-09-12 at 7 44 54 PM" src="https://user-images.githubusercontent.com/58121854/189777043-e3934e7b-d28b-4c5c-8019-17ddd98089f6.png">

#### b) For storage, I would recommend Premium SDD however, if cost is a issue you can select Standard HDD. 
<img width="687" alt="Screen Shot 2022-09-12 at 7 48 33 PM" src="https://user-images.githubusercontent.com/58121854/189777364-206b12d6-fe50-4ce1-a9fa-00ec6d5c18ba.png">

#### c) For networkng, make sure the subnet for this machine is accountant or which ever one you want it to be.
<img width="753" alt="Screen Shot 2022-09-12 at 7 50 17 PM" src="https://user-images.githubusercontent.com/58121854/189778086-5b322f54-e0fa-4905-9280-c0c7c8cf2dd9.png">

#### d) After this, you can review and create. Again you can have auto shutdown configured which can allow you to save money. Tags are also very useful but for the purpose of this demonstration, we will skip over them.


## Step 6: Configuring the NSG

#### a) Select the Windows 10 VM and go to Networking
<img width="1436" alt="Screen Shot 2022-09-14 at 9 22 55 AM" src="https://user-images.githubusercontent.com/58121854/190165740-eee902ac-c2c8-4170-9d32-c792a79cc941.png">

#### b) Since the client wants to be able to have to secure access and internet connection we are going to just change the RDP rules. This rule will allow a RDP session only if connected to the VPN and only communication with other local VMs under the accountant subnet. 
<img width="466" alt="Screen Shot 2022-09-14 at 9 24 43 AM" src="https://user-images.githubusercontent.com/58121854/190166326-9bad9571-eb28-4f51-b5dd-8ddb86712fb8.png">


## Step 7: Testing

#### a) Download the RDP Session file from azure. This is under the "Connect" option. For the first testing option, we are going to download with the public ip address and test whether or not our NSG rule is working or not. Make sure to not connect to the VPN yet. 
<img width="1436" alt="Screen Shot 2022-09-14 at 9 31 30 AM" src="https://user-images.githubusercontent.com/58121854/190167678-7670cd1b-026b-4bc7-9c21-d2c1901b833e.png">

#### b) In order to run the file, you must have a remote desktop application. After running the file you will get a error. This shows that the rule is working.
<img width="565" alt="Screen Shot 2022-09-14 at 9 33 02 AM" src="https://user-images.githubusercontent.com/58121854/190168216-ef63f79f-9b25-4c79-9834-6288763f996b.png">

#### c) Now let's try to connect to the VPN and using the same RDP session. To connect to the VPN, enter the public IP of the OpenVPN Access Server we created. Hit Next
<img width="416" alt="Screen Shot 2022-09-14 at 9 39 22 AM" src="https://user-images.githubusercontent.com/58121854/190169683-3a76532e-65d3-4100-b082-34430fc30c63.png">

#### d) Since we never added a certificate, which is recommeneded, we are going to accept the self signed certificate.
<img width="254" alt="Screen Shot 2022-09-14 at 9 40 22 AM" src="https://user-images.githubusercontent.com/58121854/190169997-eca430dc-0b3c-49d3-a127-4d90400988f5.png">

#### e) If you followed the exact steps, the username should be openvpn and whatever password you set. Accept the certificate again. I had enabled the auto login. Do not select that. I had received an error because my login was not configured that way
<img width="397" alt="Screen Shot 2022-09-14 at 9 41 34 AM" src="https://user-images.githubusercontent.com/58121854/190170283-e2ee4547-db38-4a43-8f14-957da1ae142b.png">

#### f) We are connected. Now try running the RDP session with the public IP.
<img width="376" alt="Screen Shot 2022-09-14 at 9 42 58 AM" src="https://user-images.githubusercontent.com/58121854/190170627-a26f1f60-ca7f-4f4c-b93f-86ab1cb581ff.png">

#### g) It still failed. So far it's working as attended. Now go back to Azure and download the Windows 10 RDP Session File with the Private IP.
<img width="563" alt="Screen Shot 2022-09-14 at 9 44 17 AM" src="https://user-images.githubusercontent.com/58121854/190170912-3efba412-fc99-49bb-8137-156810f2fdbc.png">

#### h) It is asking for credentials. Everything is working. Hit Continue when it comes to the certificate.
<img width="527" alt="Screen Shot 2022-09-14 at 9 46 12 AM" src="https://user-images.githubusercontent.com/58121854/190171782-8c820abd-42ee-4c46-bc02-cc1b37189f98.png">

#### i) Now see if the VM has internet access.
<img width="1440" alt="Screen Shot 2022-09-14 at 9 50 06 AM" src="https://user-images.githubusercontent.com/58121854/190172360-8852a71c-79ab-4212-881f-806d8d90a858.png">
