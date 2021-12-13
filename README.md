# linuxtech

De volgende commando’s worden gebruikt bij het testen van de Ubuntu server.
•	ip address show
•	lsb_release -d
•	whoami
•	date
•	IP-adres
hieronder zie je de ip configuratie, geïnstalleerde versie , de gebruiker en de datum van vandaag.
 




Hieronder zie je de IP-adres van de Ubuntu server. De IP-adres van de Ubuntu server is 10.0.2.15
 













De volgende commando’s worden gebruikt bij het werkstation.
•	Ipconfig /all
•	Whoami
•	Date
•	IP-adres
Hieronder zie je de IP configuraties en het IP-adres.
 


Hieronder zie je de gebruiker en datum van het werkstation.
 


Hieronder zie je dat het werkstation aan het pingen is met de Ubuntu server. De verbinding is gelukt en ze kunnen communiceren met elkaar.
 


Je gaat je Ubuntu server update en upgrade. Hieronder zie je dat gebeuren.
Update 
 
Upgrade 
 

Hieronder zie je dat poorten 22, 80 en 443 open worden gemaakt en dat firewall wordt geactiveerd.
De volgend commando’s worden gebruikt:
•	Sudo ufw allow ssh
•	Sudo ufw allow 80
•	Sudo ufw allow 443
•	Sudo ufw enable

 
Het configureren van Firewall en SSH.

SSH wordt met de volgende commando’s geïnstalleerd.
•	Sudo apt-get install ubuntu-desktop
•	sudo ufw enable
•	sudo ufw allow 22/tcp
•	Sudo systemctl status ssh

Hieronder zie je de installatie van desktop.
 
Hieronder zie je dat firewall geactiveerd is en er zijn regels toegevoegd.
 

Hieronder zie je dat SSH aan het runnen is in het systeem
 
Het installeren van Apache

Apache wordt met de volgende commando geinstalleerd: sudo apt install apache2
Hieronder zie je dat Apache aan het installeren is.
 
Hieronder zie je dat Apache2 aan het runnen is in het systeem en actief is.
 

Hieronder zie je dat het IP-adres van de Ubuntu server op de webbrowser wordt gebruikt bij de werkstation. Je typt http://10.0.2.15/ en vervolgens verschijnt er een website.
 


PHP installeren op Ubuntu server



Hieronder zie je dat het systeem aan het update is
 

Hieronder zie je dat PHP aan het installeren is met de volgende commando sudo apt install php libapache2-mod-php
ss 

Hieronder zie je de versie van PHP
 
Vervolgens is de volgende commando gebruikt: sudo systemctl restart apache2
Hieronder staat de commando die is gebruikt om een test-page te maken
echo '<?php phpinfo(); ?>' | sudo tee -a /var/www/html/phpinfo.php > /dev/null
hieronder zie je de webpagina van PHP
- Het installe 

Je installeert MariaDB met de volgende commando: sudo apt install mariadb-server mariadb-client

Hieronder zie je dat MariaDB aan het installeren is.
 

Met de volgende commando : sudo systemctl status mariadb zie je dat MariaDB actief is in het systeem.
 




Hieronder zie je dat er beveiligingsvragen worden gesteld. De commando is hiervoor gebruikt: sudo mysql_secure_installation


sudo apt-get install apache2 mysql-server -y
When that completes, install the second group of dependencies with the command:

sudo apt-get install php zip libapache2-mod-php php-gd php-json php-mysql php-curl php-mbstring php-intl php-imagick php-xml php-zip php-mysql php-bcmath php-gmp -y
How to secure the MySQL database
With the dependencies out of the way, the next thing to be taken care of is securing the database server. Back at the terminal window, issue the command:

sudo mysql_secure_installation
Give MySQL a new admin password and answer the remaining questions with y (for yes).

How to create the database

Need-to-know tips and support sites for Linux users

The open source operating system has plenty of available support—you just need to know where to look.

Research provided by TechRepublic Premium
Now we'll create the Nextcloud database and a database user. Log in to the MySQL console with the command:

sudo mysql -u root -p
Create the new database with the command:

CREATE DATABASE nextcloud;
Create a new user with the command:

CREATE USER 'nextcloud'@'localhost' IDENTIFIED BY 'PASSWORD';
Where PASSWORD is a unique and strong password.

Give the new user the necessary permissions with the command:

GRANT ALL PRIVILEGES ON nextcloud.* TO 'nextcloud'@'localhost';
Flush the privileges and exit the console with the commands:

FLUSH PRIVILEGES;
exit
How to download and unpack the Nextcloud file
In order to install Nextcloud, we have to first download the necessary zipped file. To do that, issue the command:

wget https://download.nextcloud.com/server/releases/nextcloud-20.0.0.zip
Unpack that file with the command:

unzip nextcloud-20.0.0.zip
Move the newly-created nextcloud file to the Apache document root with the command:

sudo mv nextcloud /var/www/html/
Next, we'll give the Nextcloud folder the necessary ownership with the command:

sudo chown -R www-data:www-data /var/www/html/nextcloud
How to configure the web server
With the Nextcloud directory in place, we now have to make Apache aware of it. For that, we have to create a .conf file with the command:

sudo nano /etc/apache2/sites-available/nextcloud.conf
In that file, paste the following:

Alias /nextcloud "/var/www/html/nextcloud/"
<Directory /var/www/html/nextcloud/>
    Options +FollowSymlinks
    AllowOverride All
      <IfModule mod_dav.c>
        Dav off
      </IfModule>     

     SetEnv HOME /var/www/html/nextcloud
    SetEnv HTTP_HOME /var/www/html/nextcloud
</Directory>
Save and close the file. 

Enable the new site with the command:

sudo a2ensite nextcloud
We'll now enable the necessary Apache modules by issuing the command:

sudo a2enmod rewrite headers env dir mime
Finally, we'll change the PHP memory limit with the command:

sudo sed -i '/^memory_limit =/s/=.*/= 512M/' /etc/php/7.4/apache2/php.ini
Restart Apache with the command:

sudo systemctl restart apache2
How to finish the installation
Your venture into the command line is complete. Now you can open a browser and point it to http://SERVER_IP/nextcloud (where SERVER_IP is the IP address of the hosting server). You'll first be greeted by the web-based installer (Figure A).

Figure 




sudo apt update
sudo apt upgrade 

 
Forward look up zone 
Zone maak je aan
Xprotex.com new host genaamd lamp en de ubuntu server 10.0.2.15
Je gaat naar de file (ubuntu server)
Cd var/www/html/nextcloud/config
Cd /var
Cd www
Cd html
Cd nextcloud
Cd config/
Sudo nano config.php
De ip-adres en de naam type
10.0.2.15 en lamp
Webbrowser http:/lamp/nextcloud
Dan zie je nextcloud



