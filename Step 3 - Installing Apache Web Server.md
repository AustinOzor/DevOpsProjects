# Installing Apache Using the EC2 Ubuntu machine #
**Apache HTTP Server is the web server software that handles incoming HTTP requests and serves web pages to clients.
 It is a robust and feature-rich server that supports various modules and configurations.
Apache is known for its stability, scalability, and widespread use in the industry.**

*Web Server: Apache acts as a web server that listens for incoming HTTP requests from clients and serves the 
requested web pages and resources.*

*HTTP Protocol Handling: Apache handles the HTTP protocol, allowing clients to communicate with the server using standard 
HTTP methods such as GET, POST, PUT, DELETE, etc.*

*Virtual Hosting: Apache supports virtual hosting, which allows multiple websites to be hosted on a single server by associating
different domain names or IP addresses with different directories or configurations.*

## Steps in Installing Apache: ##
#Update package lists: Run the following command to update the package lists on your system:
```
sudo apt update
```
#Install Apache2: Once the package lists are updated, you can install Apache2 by running the following command:
#
```
sudo apt install apache2 -y
```
#
## Start Apache and Verify if it is Active ##
#Install Apache2: Once the package lists are updated, you can install Apache2 by running the following command:
```
sudo systemctl start apache2
sudo systemctl status apache2
```

![Apache2 verification](https://github.com/AustinOzor/DevOps-Portfolio-Project-1/assets/99667583/bd6e96ad-2163-47b2-904d-2c99e23db8b3)

## Connecting Apache2 on the web ##
By default apache runs on port 80. However, this is not configured by default on the E2C instance unlike the SSH port 22, 
so we need to open port 80 on the EC2 instance to allow connection to the apache.

**Note**: If you have any other web servers or services running on port 80, you may encounter conflicts. 
In such cases, you may need to stop or disable the conflicting services before starting Apache2.
___________________________________________________________________________________________________________________________________________

1. Locate the security group: In the "Description" tab of the instance details, find the security group name associated with the instance. 
 It will be listed under the "Security groups" section.

2. Go to the security group settings: Navigate to the "Security Groups" section in the EC2 console. You can find this under the 
"Network & Security" category in the sidebar.

3. Edit the security group: Select the security group associated with your instance and click on the "Inbound Rules" tab.

4. Add a new rule: Click on the "Edit inbound rules" button, and then click on the "Add Rule" button.

5. Configure the rule: Set the following parameters for the inbound rule:

6. Type: Select "HTTP" from the drop-down list and chose add port 80 under the port range.
Source: Choose either "Anywhere" to allow access from any IP address or specify a specific IP range or address for added security.
7. Save the rule: Click on the "Save rules" button to apply the changes to the security group.
___________________________________________________________________________________________________________________________________________

## Verify Apache in the web browser ##
To confirm that Apache2 is successfully installed and running, open a web browser and enter
```
http://localhost:80  
```
**OR**
http://ip-add of ec2 instance:port 80

```
http://184.72.206.123:80
```
If apache is work you should see the default page below
![Apache2 web interface](https://github.com/AustinOzor/DevOps-Portfolio-Project-1/assets/99667583/f2e20845-b50f-4331-8792-e283125c9522)

## Location of Apache main configuration file ##
#The main configuration file for Apache2 is located at 

```
/etc/apache2/apache2.conf
```

#Addition configuration is located at :

```
/etc/apache2/conf-available/
```


👉👉 **Next**
https://github.com/AustinOzor/DevOps-Portfolio-Project-1/blob/main/Step%204%3A%20Installing%20MySQL%20Database.md

