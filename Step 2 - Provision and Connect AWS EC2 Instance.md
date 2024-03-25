### __Provisioining EC2 Instance__
To provision an Ubuntu EC2 server of type t2.micro in AWS, steps:
1. Log in to the AWS Management Console: Go to the AWS homepage (https://aws.amazon.com/) and sign in to your AWS account.
2. Open the EC2 Dashboard: Navigate to the EC2 service by searching for "EC2" in the AWS services search bar and selecting "EC2" from the results.
3. Launch an Instance: Click on the "Launch Instance" button to start the instance creation process.
4. Choose an Ubuntu Image: In the instance launch wizard, select the desired Ubuntu version 20.04LTS (HVM) ### .
5. Choose an Instance Type: Select the *"t2.micro"* instance type, which falls under the free tier eligibility and offers 1 vCPU and 1 GB of RAM.
6. Configure Instance Details: Leave the default settings or configure the instance details according to your requirements. You can specify the number of instances, network settings, and other configurations.
7. Add Tags (Optional): You can add tags to your EC2 instance for better organization and identification. This step is optional but can be helpful in managing your resources.
8. Configure Security Group: Create or select a security group for your EC2 instance. Security groups control inbound and outbound traffic to your instance. Ensure that port 22 (SSH) is open to allow remote access to the Ubuntu server.
9. Create a Key Pair: Select an existing key pair or create a new one. This key pair will be used to securely connect to your Ubuntu server via SSH.
10. Review and Launch: Review your instance configuration and click on the "Launch" button to start the provisioning process.
11. Access your Ubuntu Server: Once the instance is launched, you can connect to your Ubuntu server using SSH. Use the private key associated with your selected key pair to establish a secure connection.

![EC2 - Instance Launch](https://github.com/AustinOzor/DevOps-Portfolio-Project-1/assets/99667583/b2312878-cc98-4527-8a52-018a4601af74)


### Connecting to the EC Instance Using Terminal

1. Open terminal
```
2.cd ~/Downloads
```
3. Change the permission of the private key to allow connection to the EC2 instance.
 ```
 ssh -i <mykey.pem> ubuntu@<public-ip address of ec2 instance>
 ```
 Example: **ssh -i key.pem ubuntu@53.105.24.204**
 
4. Press **Enter**

**Stop the EC2 instance when not in use to avoid being charged by AWS depending on the in type you are using**

👉 
👉
**Next** https://github.com/AustinOzor/DevOps-Portfolio-Project-1/blob/main/Step%203%3A%20Installing%20Apache%20Web%20Server.md

