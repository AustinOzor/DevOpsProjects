# ENABLE PHP ON WEBSITE #
 Apache needs to be configured to recognize and process PHP files
 
With the default DirectoryIndex settings on Apache, a file named index.html will always take precedence over an index.php file.
This is useful for setting up maintenance pages in PHP applications, by creating a temporary index.html file containing an 
informative message to visitors. Because this page will take precedence over the index.php page, it will then become the landing 
page for the application. Once maintenance is over, the index.html is renamed or removed from the document root, bringing back the 
regular application page.

In case you want to change this behavior, you’ll need to edit the /etc/apache2/mods-enabled/dir.conf file and modify the order 
in which the index.php file is listed within the DirectoryIndex directive:
source: https://www.digitalocean.com/community/tutorials/how-to-install-linux-apache-mysql-php-lamp-stack-on-ubuntu-22-04

Locate the Apache configuration file for your virtual host or the global configuration file,then use the command below
```
sudo vi /etc/apache2/mods-enabled/dir.conf
``` 
Locate the section that handles the DirectoryIndex directive. Add index.php to the list of default files;
change the order of the files and make sure **index.ph** comes before the other files.

```
<IfModule mod_dir.c>
        DirectoryIndex index.php index.html index.cgi index.pl index.xhtml index.htm
</IfModule> 
```
Save the file using these steps
  i. Press ecape on the keyboard. 
  ii. Press sime-colon 
  iii. Type **wq!** and press enter to save and exit
  
To apply the changes, restart the Apache web server using the appropriate command.
```
sudo systemctl restart apache2  
```

### Testing the PHP on the Websever ###
Create a PHP test file to verify that PHP is working correctly. Create a new file named info.php in your web server's document root directory /var/www/.

```
vi /var/www/devopsproject/index.php
```

Inside info.php, add the following code:

```
<?php
phpinfo();
?>
```

Save the file and access it through a web browser by visiting http://your_server_ip/info.php. If PHP is enabled and working, you should see the PHP information page.

If everything is successfule you will see the page below.

![LampStack-2204-php-landing](https://github.com/AustinOzor/DevOps-Portfolio-Project-1/assets/99667583/0ad34200-71e2-4f72-afad-dd0645f7bd48)

The PHP file you created contain sensitve information which for security reasons shouldd be keep a secrete. 
To do that we need to remove the php file that we created using *sudo rm /var/www/your_domain/info.php*

```
sudo rm /var/www/devopsproject/info.php
```

We are all set and done.

👏 😄

