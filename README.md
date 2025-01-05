# AWS-VPC-Perring-and-EC2-Instance-Connectivity
# Creating VPC and Subnet

Login to the AWS console and navigate to the VPC section.<br>
Click on "Create VPC"<br><br>

![Screenshot_20230704_174920](https://github.com/Diplahane/AWS-VPC-Perring-and-EC2-Instance-Connectivity/assets/129828021/9f58964c-2628-486d-80d6-c4320d618990)

![Screenshot_20230704_175034](https://github.com/Diplahane/AWS-VPC-Perring-and-EC2-Instance-Connectivity/assets/129828021/d764f716-e77d-4551-ba86-de67180dafc8)


provide a name tag for your VPC (e.g., "vpc-A").<br>
Define the CIDR range for your VPC (e.g., "10.0.0.0/16").<br>
Leave the other settings as default and click on "Create VPC".<br>

![Screenshot_20230704_175147](https://github.com/Diplahane/AWS-VPC-Perring-and-EC2-Instance-Connectivity/assets/129828021/e4c06405-3d73-4cb6-8650-db2c4c77c55d)


On the left side of the VPC dashboard, select "Subnets."<br>
Click on "Create Subnet."<br>

![Screenshot_20230704_175214](https://github.com/Diplahane/AWS-VPC-Perring-and-EC2-Instance-Connectivity/assets/129828021/dd485994-79bc-4939-aaa4-3f10102df339)
Select the VPC you just created.<br>
Set the CIDR range for the subnet, e.g., "10.0.1.0/24."<br>
Create the subnet.<br>

![Screenshot_20230704_175226](https://github.com/Diplahane/AWS-VPC-Perring-and-EC2-Instance-Connectivity/assets/129828021/818d1932-87a8-4482-ab29-90aef167dcd4)

![Screenshot_20230704_175302](https://github.com/Diplahane/AWS-VPC-Perring-and-EC2-Instance-Connectivity/assets/129828021/0ee7f405-88b1-4c25-8c3e-289d7f0be26a)

# Configuring Internet Gateway

Go back to the dashboard and select "Internet Gateway".<br>
Create an internet gateway using the VPC you just created.<br>

![Screenshot_20230704_175327](https://github.com/Diplahane/AWS-VPC-Perring-and-EC2-Instance-Connectivity/assets/129828021/b1d2be7a-91a3-4e11-aee5-f826b126fcaf)

![Screenshot_20230704_175346](https://github.com/Diplahane/AWS-VPC-Perring-and-EC2-Instance-Connectivity/assets/129828021/02f532f7-1acc-4658-ba40-9882941bcf82)
After creating the internet gateway, click on "Actions" at the top right side and select "Attach to VPC".<br>

![Screenshot_20230704_175400](https://github.com/Diplahane/AWS-VPC-Perring-and-EC2-Instance-Connectivity/assets/129828021/64b41723-afb2-4ed1-8e3a-5a5947c6820d)

![Screenshot_20230704_175418](https://github.com/Diplahane/AWS-VPC-Perring-and-EC2-Instance-Connectivity/assets/129828021/6dafbf55-5b8b-40aa-9673-fcfea7705035)

# Setting Up Route Table

Navigate to the "Route Table" in the dashboard.<br>
To make it easier to understand, rename the already created route table in your VPC.<br>

![Screenshot_20230704_175448](https://github.com/Diplahane/AWS-VPC-Perring-and-EC2-Instance-Connectivity/assets/129828021/8280eace-5e7a-4c83-916e-d23397525e33)

![Screenshot_20230704_175511](https://github.com/Diplahane/AWS-VPC-Perring-and-EC2-Instance-Connectivity/assets/129828021/dbac6e72-90e8-410b-b05a-12e48da12f9d)

In the route table, click on "Edit routes".<br>
To allow your subnet to access the internet, add a new route to the subnet route table with the following settings:<br>

Destination: 0.0.0.0/0<br>
Target: The internet gateway that you just created<br><br>

![Screenshot_20230704_175536](https://github.com/Diplahane/AWS-VPC-Perring-and-EC2-Instance-Connectivity/assets/129828021/a6e2df44-b53b-4484-b111-584566b341bd)

Go to the "Subnet associations" tab in the route table.<br>

![Screenshot_20230704_175601](https://github.com/Diplahane/AWS-VPC-Perring-and-EC2-Instance-Connectivity/assets/129828021/9d1a9612-52cd-4c7f-8795-5d2617ee97ba)
Click on "Edit subnet association" and select the subnet you created.<br>
Save the associations.<br>

![Screenshot_20230704_175613](https://github.com/Diplahane/AWS-VPC-Perring-and-EC2-Instance-Connectivity/assets/129828021/ea2d8495-57f3-4127-8f06-1a997678b150)

# Creating Security Group

Scroll down on the dashboard and navigate to "Security Groups".<br>
Click on "Create security group" and provide a name for the security group.<br>

![Screenshot_20230704_175642](https://github.com/Diplahane/AWS-VPC-Perring-and-EC2-Instance-Connectivity/assets/129828021/50e8cbe0-d55b-475f-bc93-611fd71025e8)

Select your VPC.

![Screenshot_20230704_175701](https://github.com/Diplahane/AWS-VPC-Perring-and-EC2-Instance-Connectivity/assets/129828021/e9456c5b-e8f7-4d18-b974-779303dbc569)

Click on "Edit inbound rules" and add a rule for "All ICMP IPv4" with the source set to "Anywhere - IPv4".<br>
Save the rules.<br>

![Screenshot_20230704_175752](https://github.com/Diplahane/AWS-VPC-Perring-and-EC2-Instance-Connectivity/assets/129828021/28e7f072-3810-4c96-ab79-f3cdb1937ae0)

# Launching EC2 Instance

![Screenshot_20230704_175842](https://github.com/Diplahane/AWS-VPC-Perring-and-EC2-Instance-Connectivity/assets/129828021/2af477c3-2174-4558-9a8c-c22490e91566)

![Screenshot_20230704_175857](https://github.com/Diplahane/AWS-VPC-Perring-and-EC2-Instance-Connectivity/assets/129828021/8566edf4-c869-4a0e-8e23-21788daf7a3a)

Go to the EC2 section.<br>
Click on "Launch instance" and select a name tag for your instance.<br>

![Screenshot_20230704_175957](https://github.com/Diplahane/AWS-VPC-Perring-and-EC2-Instance-Connectivity/assets/129828021/ad8a7ab9-7caf-4b63-940b-874c5040ad2d)

Select an Amazon Machine Image (AMI) and Instance Type

![Screenshot_20230704_180007](https://github.com/Diplahane/AWS-VPC-Perring-and-EC2-Instance-Connectivity/assets/129828021/cd5b8e13-0875-4f7c-8143-3f9f38827f07)

Create a new key pair (e.g., "peering-A") or use an existing one.

![Screenshot_20230704_180035](https://github.com/Diplahane/AWS-VPC-Perring-and-EC2-Instance-Connectivity/assets/129828021/d7fc2433-ebb0-4041-a364-f446072ab7bb)

Scroll down and edit the "Network Setting".<br>
Select your VPC and enable auto-assign public IP.<br>
Select the existing security group you created.<br>
Click on "Launch instance" and connect to the instance.<br>

![Screenshot_20230704_180216](https://github.com/Diplahane/AWS-VPC-Perring-and-EC2-Instance-Connectivity/assets/129828021/d315c39e-57c4-4ba8-a4a2-242ca76c1d69)

# Creating Second VPC and Subnet

Repeat the above steps to create another VPC called "vpc-B".<br>
Use CIDR range 172.16.0.0/16 for the VPC and 172.16.1.0/24 for the subnet.<br>

![Screenshot_20230704_181654](https://github.com/Diplahane/AWS-VPC-Perring-and-EC2-Instance-Connectivity/assets/129828021/7962dbcb-51e0-449a-9113-29d5602126f2)

Launch an EC2 instance named "linux-B" in vpc-B.

![Screenshot_20230704_182046](https://github.com/Diplahane/AWS-VPC-Perring-and-EC2-Instance-Connectivity/assets/129828021/1d5b3914-92ac-4323-b4e1-731a45717da8)

# Setting Up VPC Peering

Go to the VPC dashboard and navigate to "VPC Peering".<br>
Select "Create VPC Peering"<br>

![Screenshot_20230704_183749](https://github.com/Diplahane/AWS-VPC-Perring-and-EC2-Instance-Connectivity/assets/129828021/856add25-2ddc-4a19-b54e-6189430407ab)

Give it a name (e.g., "peering-AB").<br>
Set "VPC-A" as the requester, "my account" as the accepter, and "VPC-B" as the select another VPC.<br>
Click on "Create Peering Connection".<br>

![Screenshot_20230704_183930](https://github.com/Diplahane/AWS-VPC-Perring-and-EC2-Instance-Connectivity/assets/129828021/05ba822d-3a60-43b1-afc5-f458ae9c9c04)

In the "Actions" menu at the top right side, select "Accept Request" to accept the peering connection.

![Screenshot_20230704_184003](https://github.com/Diplahane/AWS-VPC-Perring-and-EC2-Instance-Connectivity/assets/129828021/887c42f8-fe32-44d2-be68-a0dbe39166d5)

# Configuring Route Tables for VPC Peering

Go to the VPC dashboard and navigate to the route tables.<br>

![Screenshot_20230704_184053](https://github.com/Diplahane/AWS-VPC-Perring-and-EC2-Instance-Connectivity/assets/129828021/5be6e8e0-13db-4635-81f3-06eb1b85bc74)

Click on "Edit routes" for the route table of "vpc-A".<br>
Add a new route with the destination as the IP of "vpc-B" and the target as "VPC Peering".<br>

![Screenshot_20230704_184137](https://github.com/Diplahane/AWS-VPC-Perring-and-EC2-Instance-Connectivity/assets/129828021/4b67dcfd-b57f-4e43-91f7-0a60df4726e1)
Repeat the above step for the route table of "vpc-B", adding a rule with the destination as the IP of "vpc-A" and the target as "VPC Peering".

![33](https://github.com/harshartz/AWS-VPC-Peering-and-EC2-Instance-Connectivity/assets/130890384/482506fb-a053-4d48-8de4-e770f6c06afe)


# Connecting to EC2 Instance

![Screenshot_20230704_184419](https://github.com/Diplahane/AWS-VPC-Perring-and-EC2-Instance-Connectivity/assets/129828021/1d0ad6d0-b017-4e78-8dde-0ee5f3747abd)

![Screenshot_20230704_184440](https://github.com/Diplahane/AWS-VPC-Perring-and-EC2-Instance-Connectivity/assets/129828021/fa01f6a7-3b46-4b03-b417-bd83663ebc65)

To establish a connection between the EC2 instances, follow these steps:<br>

Connect to one of the EC2 instance<br>

Switch to the root user:<br>

Run the command: <br>
```diff
-sudo -i
```

![Screenshot_20230704_184515](https://github.com/Diplahane/AWS-VPC-Perring-and-EC2-Instance-Connectivity/assets/129828021/531ddc31-7bcf-46b0-b1fc-b7d12f365a81)

Create an empty file with a name of target Ec2's key pair file (e.g., "peering-B"):<br>

Run the command: <br>
```diff
-touch peering-B
```

Edit the file and paste the private key of the EC2 instance that you want to connect to:<br>

Run the command: <br>
```diff
-vi peering-B
```

![Screenshot_20230704_184544](https://github.com/Diplahane/AWS-VPC-Perring-and-EC2-Instance-Connectivity/assets/129828021/a80f7b01-f3ad-494c-80a2-268af5222c25)

![Screenshot_20230704_184702](https://github.com/Diplahane/AWS-VPC-Perring-and-EC2-Instance-Connectivity/assets/129828021/a60c3d23-70d2-4c25-91cf-2b9cdb96dbc7)

Modify the permissions of the file:<br>

Run the command: <br>
```diff
-chmod 400 peering-B
```

Use the SSH command to establish the connection to the other EC2 instance:<br>

Run the command: <br>
```diff
-ssh -i <<key-pair-file-name>> ec2-user@<<Target Linux EC2's Private IP>>
```
![Screenshot_20230704_184713](https://github.com/Diplahane/AWS-VPC-Perring-and-EC2-Instance-Connectivity/assets/129828021/e581d8ae-2d85-47d5-8e98-05df485a9bc8)

Select "yes" to confirm the connection

![Screenshot_20230704_184721](https://github.com/Diplahane/AWS-VPC-Perring-and-EC2-Instance-Connectivity/assets/129828021/4bcc313a-6353-4a7b-aae7-52a4fc4d197f)

# You have successfully established a connection between the two EC2 instances.
