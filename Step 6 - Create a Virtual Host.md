# CREATING A VIRTUAL HOST FOR USING APACHE #
#### What is a Virtual host? ####
A virtual host is a feature of the Apache web server that allows multiple websites to be hosted on 
the same server. It allows the server to differentiate between requests for different websites,
and to serve the appropriate content for each website. 

Virtual hosting allows you to run multiple websites with different domain names or subdomains 
on the same server, utilizing the server's resources efficiently. It enables websites to share
the server's processing power, memory, and network connectivity while keeping their content and
configurations isolated from one another.
_______________________________________________________________________________________________________________________________________________________________________
#### How Virtual Host Works ####
When a user requests a webpage from a virtual host, the web server uses the requested domain name or IP address 
to determine which website's content to serve. The server matches the domain name in the HTTP request header
with the configured virtual hosts and delivers the appropriate content to the user.
___________________________________________________________________________________________________________________________________________________________________
#### How to Configure Virtual Host on Apache ####
1. Create directory in */var/www/devopsproject* for the project to store the configuration 
```
sudo mkdir /var/www/devopsporject
```
2. Assign ownship of the directory to the current user: 
```
sudo chown -R $USER:$USER /var/www/devopsproject
```
3. Identify the Apache configuration directory: The configuration files for Apache are typically located in 
**/etc/apache2/sites-available/**
4. Create a new configuration file in: /etc/apache2/sites-available/devopsproject,  create a new file with a .conf extension. 
```
sudo vi /etc/apache2/sites-available/devopsproject.conf
```
5. The devopsproject.conf file we create is empty. Now define the virtual host. Inside the configuration file, add the following lines
  to define the virtual host:
 
```
<VirtualHost *:80>
    ServerName devopsproject.com
    ServerAlias www.devopsproject.com
    ServeAdmin webmaster@localhost
    DocumentRoot /var/www/devopsproject.com/public_html
    ErrorLog  ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>

```
**Save the file and exit**
```
Press **esc** then **:** followed by **wq!** then press enter
```
6. Enable the virtual host configuration file.
```
sudo a2ensite devopsproject   # For Ubuntu/Debian
```
a2ensite is a script that enables the specified site (which contains a <VirtualHost> block)
within the apache2 configuration. It does this by creating symlinks within /etc/apache2/sites-enabled.
Likewise, a2dissite disables a site by removing those symlinks. It is not an error to enable a site which is
already enabled, or to disable one which is already disabled.
Apache treats the very first virtual host enabled specially as every request not matching any actual directive 
is being redirected there. Thus it should be called 000-default in order to sort before the remaining hosts to be loaded first.
 https://manpages.debian.org/jessie/apache2/a2ensite.8.en.html
  
7. Before reloading your server, disable the default site defined in 000-default.conf by using the a2dissite command:
```
sudo a2dissite 000-default
```

8. Verify the configuration file to check any error which might affect the configuration
```
9. sudo apache2ctl configtest
```
If there is no error the output should be 
```
...
syntax ok
```
10. Restart Apache: To apply the changes, restart the Apache web server using the command:
 ```
 sudo systemctl restart apache2   
```

 The website is now active but the as the is not content or file which will be displayed.
  /var/www/devopsject is empty.

  
  Next we will enable PHP on the week site.


  👉 👉 **Next**
  https://github.com/AustinOzor/DevOps-Portfolio-Project-1/blob/main/Step%207%3A%20Enable%20PHP%20on%20the%20Website.md
  


  
 
 
 
