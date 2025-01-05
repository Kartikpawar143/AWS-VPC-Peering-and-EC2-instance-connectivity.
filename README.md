# AWS-VPC-Perring-and-EC2-Instance-Connectivity
# Creating VPC and Subnet

Login to the AWS console and navigate to the VPC section.<br>
Click on "Create VPC"<br><br>

![Screenshot 2025-01-04 111317](https://github.com/user-attachments/assets/2b1b058d-fd48-4e39-850c-018cb21da771)

![Screenshot 2025-01-04 111417](https://github.com/user-attachments/assets/c9f5d83a-61f1-47cd-bb60-21fb063a6360)

provide a name tag for your VPC (e.g., "vpc-A").<br>
Define the CIDR range for your VPC (e.g., "10.0.0.0/16").<br>
Leave the other settings as default and click on "Create VPC".<br>

![Screenshot 2025-01-04 111618](https://github.com/user-attachments/assets/7e5685aa-3386-456c-ba4c-d70c09021ce6)

On the left side of the VPC dashboard, select "Subnets."<br>
Click on "Create Subnet."<br>

![Screenshot 2025-01-04 111709](https://github.com/user-attachments/assets/e9245bb8-136c-4888-a20b-5f99c21ef226)
Select the VPC you just created.<br>
Set the CIDR range for the subnet, e.g., "10.0.1.0/24."<br>
Create the subnet.<br>

![Screenshot 2025-01-04 112942](https://github.com/user-attachments/assets/05ffd680-4537-4e8b-a1a8-8a8d992eb061)

![Screenshot 2025-01-04 113125](https://github.com/user-attachments/assets/0ba5d7a2-8337-40ca-afa9-290fadad9c56)
# Configuring Internet Gateway

Go back to the dashboard and select "Internet Gateway".<br>
Create an internet gateway using the VPC you just created.<br>

![Screenshot 2025-01-04 113639](https://github.com/user-attachments/assets/58baa63f-8eaf-46e5-9ee6-607eb13950d2)

![Screenshot 2025-01-04 113722](https://github.com/user-attachments/assets/5fa11536-0cdf-44bd-952d-7d2c650a901b)
After creating the internet gateway, click on "Actions" at the top right side and select "Attach to VPC".<br>

![Screenshot 2025-01-04 113736](https://github.com/user-attachments/assets/acd83da0-d13a-43d1-a308-1e87a32af4fb)
![Screenshot 2025-01-04 113804](https://github.com/user-attachments/assets/c8d266a8-93eb-4649-a8fa-f1e8e3269d08)
# Setting Up Route Table

Navigate to the "Route Table" in the dashboard.<br>
To make it easier to understand, rename the already created route table in your VPC.<br>

![Screenshot 2025-01-04 113851](https://github.com/user-attachments/assets/177f3da4-a3b9-4a95-af17-57e036ceda86)

![Screenshot 2025-01-04 113932](https://github.com/user-attachments/assets/25653da7-1150-48e2-9c8e-61621ab65470)

In the route table, click on "Edit routes".<br>
To allow your subnet to access the internet, add a new route to the subnet route table with the following settings:<br>

Destination: 0.0.0.0/0<br>
Target: The internet gateway that you just created<br><br>

![Screenshot 2025-01-04 113957](https://github.com/user-attachments/assets/43dffd79-ecd7-4499-b11f-547624d9eb34)
Go to the "Subnet associations" tab in the route table.<br>
Click on "Edit subnet association" and select the subnet you created.<br>
Save the associations.<br>

![Screenshot 2025-01-04 114215](https://github.com/user-attachments/assets/c0280b67-b383-494a-87f7-c0b277cdf2e1)

# Creating Security Group

Scroll down on the dashboard and navigate to "Security Groups".<br>
Click on "Create security group" and provide a name for the security group.<br>

![Screenshot 2025-01-04 114327](https://github.com/user-attachments/assets/25d09b4e-e587-45cd-a8f9-beb7ce643634)
Select your VPC.

![Screenshot 2025-01-04 114636](https://github.com/user-attachments/assets/869bc3a6-d2e0-4a8a-8187-9033e02ecea2)
Click on "Edit inbound rules" and add a rule for "All ICMP IPv4" with the source set to "Anywhere - IPv4".<br>
Save the rules.<br>

![Screenshot 2025-01-04 114527](https://github.com/user-attachments/assets/64093cad-90e9-4560-8e57-911e60ee8e7f)

# Launching EC2 Instance

![Screenshot 2025-01-04 114709](https://github.com/user-attachments/assets/feb02f5d-d239-4cfb-a252-2d8b53c7b2e9)
![Screenshot 2025-01-04 114841](https://github.com/user-attachments/assets/f5700034-8df3-43c5-ae3a-496074e25616)

Go to the EC2 section.<br>
Click on "Launch instance" and select a name tag for your instance.<br>

![Screenshot 2025-01-04 115037](https://github.com/user-attachments/assets/e4bf796d-593f-4811-9a82-403dfc1acd8c)
Select an Amazon Machine Image (AMI) and Instance Type

![Screenshot 2025-01-04 115141](https://github.com/user-attachments/assets/684647d6-f962-44f7-9b27-cb7924921e26)

Create a new key pair (e.g., "peering-A") or use an existing one.

![Screenshot 2025-01-04 115304](https://github.com/user-attachments/assets/f7200e0d-11ed-49c8-a616-6aae95187d66)
Scroll down and edit the "Network Setting".<br>
Select your VPC and enable auto-assign public IP.<br>
Select the existing security group you created.<br>
Click on "Launch instance" and connect to the instance.<br>

![Screenshot 2025-01-04 115419](https://github.com/user-attachments/assets/798e8a1f-0456-46dd-9b5a-d8c691a10fdc)
# Creating Second VPC and Subnet

Repeat the above steps to create another VPC called "vpc-B".<br>
Use CIDR range 172.16.0.0/16 for the VPC and 172.16.1.0/24 for the subnet.<br>

![Screenshot 2025-01-04 121206](https://github.com/user-attachments/assets/0abcc109-0f69-40e8-8516-533b8a83e9a6)
Launch an EC2 instance named "linux-B" in vpc-B.

![Screenshot 2025-01-04 121250](https://github.com/user-attachments/assets/24fd9bea-cbcb-4f24-aec8-c20fbe578d99)
# Setting Up VPC Peering

Go to the VPC dashboard and navigate to "VPC Peering".<br>
Select "Create VPC Peering"<br>

![Screenshot 2025-01-04 121345](https://github.com/user-attachments/assets/2aa945a8-c47b-4bbd-b28b-aa90e641ba17)
Give it a name (e.g., "peering-AB").<br>
Set "VPC-A" as the requester, "my account" as the accepter, and "VPC-B" as the select another VPC.<br>
Click on "Create Peering Connection".<br>

![Screenshot 2025-01-04 121540](https://github.com/user-attachments/assets/d2e48ff7-9892-46e8-b511-15ed5e2c2328)
In the "Actions" menu at the top right side, select "Accept Request" to accept the peering connection.

![Screenshot 2025-01-04 121602](https://github.com/user-attachments/assets/3e45a8a7-1d9b-4531-afdd-c7c84ea55617)
# Configuring Route Tables for VPC Peering

Go to the VPC dashboard and navigate to the route tables.<br>

![Screenshot 2025-01-04 122605](https://github.com/user-attachments/assets/05a4fe84-b43a-402a-9d34-98147a587c92)
Click on "Edit routes" for the route table of "vpc-A".<br>
Add a new route with the destination as the IP of "vpc-B" and the target as "VPC Peering".<br>

![Screenshot 2025-01-05 115350](https://github.com/user-attachments/assets/787107c8-978f-4ca7-a1d0-c275103199e6)
Repeat the above step for the route table of "vpc-B", adding a rule with the destination as the IP of "vpc-A" and the target as "VPC Peering".

![Screenshot 2025-01-05 115444](https://github.com/user-attachments/assets/a812c820-b92c-44d5-a6e6-5ee494693357).

# Connecting to EC2 Instance

![Screenshot 2025-01-05 123153](https://github.com/user-attachments/assets/56ec5b39-5171-40eb-b751-1c321734ea7d)
![Screenshot 2025-01-05 123249](https://github.com/user-attachments/assets/073a3600-075b-4a04-a1bb-0fb66d932396)
To establish a connection between the EC2 instances, follow these steps:<br>

Connect to one of the EC2 instance<br>

Switch to the root user:<br>

Run the command: <br>
```diff
-sudo -i
```

![Screenshot 2025-01-05 121532](https://github.com/user-attachments/assets/9c8bf58a-9895-4889-82fd-31e70333a5b8)
Create an empty file with a name of target Ec2's key pair file (e.g., "peering-B.pem"):<br>

Run the command: <br>
```diff
-touch peering-B.pem
```

Edit the file and paste the private key of the EC2 instance that you want to connect to:<br>

Run the command: <br>
```diff
-vi peering-B.pem
```

![Screenshot 2025-01-05 121532](https://github.com/user-attachments/assets/9c8bf58a-9895-4889-82fd-31e70333a5b8)
![Screenshot 2025-01-05 121645](https://github.com/user-attachments/assets/ca2e05f2-1a89-45d8-be93-737a74ce6a3c)
Modify the permissions of the file:<br>

Run the command: <br>
```diff
-chmod 400 peering-B.pem
```

Use the SSH command to establish the connection to the other EC2 instance:<br>

Run the command: <br>
```diff
-ssh -i <<key-pair-file-name>> ubuntu@<<Target Linux EC2's Private IP>>
```
![Screenshot 2025-01-05 121756](https://github.com/user-attachments/assets/6ebd2f17-8eb0-4ff6-910e-cad3c0d16fa0)
Select "yes" to confirm the connection

![Screenshot 2025-01-05 121811](https://github.com/user-attachments/assets/233a2832-2344-4a23-a960-ffd4cd82a07c)

# You have successfully established a connection between the two EC2 instances.
