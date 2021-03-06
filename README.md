# CS499 Team 2 SQS Training Site README



Code in this repository represents efforts of Connor Kunstek @ConnorKunstek, Nick Sladic @Nickademius, Luke Andrews, and Stephen Richie 



https://github.com/ConnorKunstek/SeniorDesignProject




## Directory Structure



>Training_site/



Contains index.php, assets, and all other display code. Code is written as PHP files with HTML and CSS markup and styling. Some JavaScript code is used to augment functionality, and both JQuery and Bootstrap libraries are dependencies, and are included in this repository.



The root directory contains SQL connector files used for accesing the MySQL database as well as DDL files for all necessary SQL tables. Both pure schema and dumps with placeholder data are included in corresponding folders.



A file named 'config.ini' not tracked in this repository will need to be placed in the root directory containing credentials for accessing the MySQL database. Further instructions follow under 'Installation Instructions'.



## Dependencies



This site is built to run on a traditional LAMP (Linux/Apache/MySQL/PHP) stack. It was developed on Linux machines running MySQL/MariaDB, PHP, and Apache, but should run on other webserver technologies, provided the other requirements are met, and all other settings and paths are correct.



Given this, the dependencies are as follows:



- A Unix based webserver running Apache (or an equivalent webserver such as NGINX *ALHTOUGH THIS IS UNTESTED AND NOT OFFICIALLY SUPPORTED*)

- PHP version 7 or above

- PHP-Apache version 7 or above (or the equivalent package/dependency for your distribution/platform)

- MySQL server version 10 or above (or an equivalent for your distribution/platform such as MariaDB)



JQuery and Bootstrap are not listed as dependencies as the necessary files are included within assets/css/ assets/js/. Should you wish to update either, simply replace the files within those directories with more recent versions.



## Installation Instructions - TODO



### LAMP Stack - NEEDS EDITING



- Install and configure Apache according to the guidelines of your distribution.

- Install and configure MySQL or MariaDB through the appropriate package as per your distribution.

- Install and configure PHP through the appropriate package as per your distribution.



These three steps are detailed more fully [here](https://www.digitalocean.com/community/tutorials/how-to-install-linux-apache-mysql-php-lamp-stack-on-ubuntu-16-04), in a tutorial for Ubuntu systems. It also may be useful to install and configure a management program such as [PHP My Admin](https://www.digitalocean.com/community/tutorials/how-to-install-and-secure-phpmyadmin-on-ubuntu-16-04) to make it easier to add to and edit the SQL database.



### Project Specific Instructions - NEEDS EDITING



- Create a table named 'cs499' (without quotes) in the MySQL database.

- Individually run all the .sql files located in either 'schemas' or 'DDL_with_data'. check to see that all eleven tables have been created. Start with 'user_schema.sql' so as to avoid foreign key constraint conflicts.

- Prepare the installation location. This is



>/var/www/html/



on most distributions, but could be locations such as '/srv/http/' on ArchLinux/Slackware distributions, or other locations. Check where Apache serves files from on your system.



- if your system does not use '/var/www/' to serve files, create a symlink from your serve location to '/var/www/html'. It is important to leave off the trailing '/' in this path. A sample symlink command would look like this:



> sudo ln -s /srv/http/ /var/www/html



where /srv/http/ is the location your Apache installation serves files from. Create the /var/www/ directory before running this command, if need be.



- Download the sqsg6 repository to your installation location. On systems with Git installed simply run this command:



> git clone https://github.com/Robert8944/sqsg6



or alternatively



> wget https://github.com/Robert8944/sqsg6/archive/master.zip



and



> unzip master.zip



- Test that your installation was successful by navigating to the 'Training_site/' directory in your browser, usually [http://localhost/sqsg6/Training_site/](http://localhost/sqsg6/Training_site/) if you are running the LAMP stack on your local machine. This URL should load 'index.php' automatically.



- Create a file in the root /sqsg6/ directory named 'config.ini' (without quotes).



- In 'config.ini' write one line with the format



> password = "Demo Password"



Where "Demo Password" is the root password to your MySQL database. Keep the quotes in the config.ini file. If you wish to use a different user, edit the 'sql_connector.php' file to use a differnt string other than 'root' on the line containing 'DB_USER'.



- Test the connection to the SQL database by running



> php sql_connector.php



from the command line. The file should execute without error.





## Continued Development - NEEDS EDITING



All code changes made over the course of the 2017 Spring Semester development have an associated pull request and refrenced issue on the GitHub page. To trace a code alteration find the file changed, view its history through the GitHub interface, and find the associated commit and pull request name.





## Fall 2017 Updates - NEEDS UPDATING



Instead of using the traditional LAMP stack, we decided to go with XAMPP due to group members having different operating systems and previous experience with XAMP over LAMP.

All dependencies and directory structure should be the same as listed above.



Installation has not changed. Using XAMPP and phpMyAdmin allowed us to comment out the use of the config file when connecting to the database.

Thus, the only difference between our code and previous semesters code is the file paths used and excluding the use of the config file.



Only files with altered file paths are as follows...



sql_connector.php				--> Lines 4 & 6

feature_connector.php			--> Lines 8, 11, & 14

features_loader.php				--> Line 10



Required to alter for features to load properly.



groupdisplay_0_profile_d.php	--> Lines 3 & 5

groupdisplay_1_profile_d.php	--> Lines 7 & 9

phonedisplay_0_profile_d.php	--> Lines 3 & 5

phonedisplay_1_profile_d.php	--> Lines 3 & 5

addressdisplay_0_profile_d.php	--> Lines 3 & 5



All files have comments indicating what the file path was from previous semester for ease of installation in the future.



All new files added contain comments for ease of continuted development.

Added files...



user_register.php	--> Not new code but split and altered into multiple files.

user register2.php	--> Used some code from original user_register.php, added some new code.

user_register3.php	--> All New code, based off previous user_register.php design.

user_register4.php	--> All New code, based off previous user_register.php design.

skillsinfo.php		--> All New code. Used to update information in database from user profile.

header.php			--> Added code for new features.



If using XAMPP on Windows. Simply install XAMPP. Place the sqsg6 folder into the htdocs folder in XAMPP.



XAMPP/htdocs/[Folder Here]



Run the XAMPP Control Panel, Start Apache and MySQL, click on Admin in the MySQL row, click on the databases tab and create a new database called cs499,

navigate to the import tab, and import either sql files from schemas or ddl_with_data folder to get the initial database set up and you're ready.



Then simply connect to the webpage by using the URL



localhost/sqsg6/Training_site/



Features added...

	Registration Progress Bar		--> Indicates progress through new registration process.

	Element ID Tags					--> For automation team to automate the site.

	Skills Bank Idea				--> Pages 3 & 4 of registration process and skills displayed on user profile page.

	Individual User Progress Bar	--> Indicates how complete a users profile is.

		 Individual user progress shows the percentage of profile completed by user, the code embeded in Header.php in config folder but the feature still need some work and passing the testing procedure, currently we get error when we login and doesn't show user prograss for user Admin. also in order to show the prograss pie graph the server requrired to access to internet since we used feature google drawchart api. 