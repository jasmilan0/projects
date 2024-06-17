## Step 1: Open the virtual network in the RG
#### Create a new subnet for client workstations
<img width="843" alt="Screen Shot 2024-06-16 at 6 50 44 PM" src="https://github.com/jasmilan0/projects/assets/58121854/e733c258-1f04-423e-a49e-3b85b4033257">

#### Enable private endpoint. This is so we can route outbound traffic through one public ip

## Step 2: Assign the route to the DNS server in azure to the AD Server VM

<img width="1435" alt="Screen Shot 2024-06-16 at 6 57 26 PM" src="https://github.com/jasmilan0/projects/assets/58121854/50b70bd2-06f2-41db-af22-1d644f7e3e3d">

## Step 2: Create a Windows 11 VM in the RG
<img width="1029" alt="Screen Shot 2024-06-16 at 7 02 17 PM" src="https://github.com/jasmilan0/projects/assets/58121854/dada0ce9-ebaa-445d-bd81-2c4947b791a6">

<img width="870" alt="Screen Shot 2024-06-16 at 7 02 53 PM" src="https://github.com/jasmilan0/projects/assets/58121854/582db243-6127-4b89-94d5-9f568fadfc4c">

<img width="903" alt="Screen Shot 2024-06-16 at 7 03 05 PM" src="https://github.com/jasmilan0/projects/assets/58121854/590b8bbd-1e99-4bc2-a53e-602383126dd6">

<img width="871" alt="Screen Shot 2024-06-16 at 7 03 30 PM" src="https://github.com/jasmilan0/projects/assets/58121854/38271f5e-e34a-4b03-8256-6e489d0d4095">

<img width="832" alt="Screen Shot 2024-06-16 at 7 04 53 PM" src="https://github.com/jasmilan0/projects/assets/58121854/c0766eac-252d-42c4-9626-aaf8f6c0d44a">

<img width="883" alt="Screen Shot 2024-06-16 at 7 05 06 PM" src="https://github.com/jasmilan0/projects/assets/58121854/f9d8292c-7fd0-4c03-a2f7-d959b5e114c4">

<img width="875" alt="Screen Shot 2024-06-16 at 7 05 46 PM" src="https://github.com/jasmilan0/projects/assets/58121854/bcd4e54a-7cfa-472b-8030-3f4deff3e3af">

#### Skip Management, Monitoring, advanced, and tags and then hit create

## Step 3: Restart both the AD Server VM and Client Workstation 1 to make sure both are able to communicate with each other
#### Select virtual machines under home
<img width="1175" alt="Screen Shot 2024-06-16 at 7 26 55 PM" src="https://github.com/jasmilan0/projects/assets/58121854/1f3867f3-0669-48a8-9bb8-09b826695533">

#### Select both VMs and hit restart on top 
<img width="1427" alt="Screen Shot 2024-06-16 at 7 27 31 PM" src="https://github.com/jasmilan0/projects/assets/58121854/b7926ee6-bd09-497e-b76c-7c9a0518cd51">

## Step 4: Connect to both machines and ping each other

#### Since there is no public IP to the Client VM, you will have to connect via Bastion
#### When configuring bastion, it will create a virtual subnet automatically and can take around 30-45 minutes, sometimes even longer

#### If you try to ping the VMs, most likely you would be able to ping the AD Server VM from the Client VM. But you would be unsuccessful the other way around. <br />
#### You would have to create a rule in the Client VM firewall to allow ICMP traffic <br />
#### If everything is configured correctly, you should be able to ping each other

## Step 5: 
