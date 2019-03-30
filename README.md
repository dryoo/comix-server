comix-server-php
================

Comix-server is a PHP-based AirComix Server acting just as the Windows
version. Originally it was written to run on the Synology NAS. However,
it can run on any platforms where HTTP/PHP Server runs, such as
Ubuntu Linux or OS X.

Comix-server is only compatible with **iOS AirComix** app.


## How to install

- put index.php to your web directory (you should use web document root)
- make subdirectory named as 'manga' and put all things in.


## Nginx configuration 

    rewrite ^/(.*) /index.php;



## How to use

- Copy your comic collection to the manga directory.
- Start the AirComix app on your iOS devices and add comix-server as an AirComix Server.
  Select the **AirComix Server URL** menu to fill in your comix-server information.
  use 80 port.
- Enjoy!



## FAQ


Q) Which file formats are supported?  
A) Comix-server supports archive formats such as ZIP and CBZ.
   Also it supports most image formats such as JPG, GIF, PNG, and TIFF.

Q) Does comix-server support RAR or CBR format?  
A) Depends. Your system needs PHP extension for RAR. On Linux, you can easily install it (see <http://www.php.net/manual/en/rar.installation.php> for more details), but on Synology DSM, it seems very hard to install it. Please let me know if you find a way!

Q) Do I need to uncompress ZIP or CBZ files?  
A) No. Like Windows version, just put them in your manga directory.
   However, comix-server does not handle double-zipped files.

Q) Can I have multiple directories under my manga directory?  
A) Yes. You can make any directory structure. 
   One restriction is that image files can be only in a leaf directory, 
   which does not have any child directory.

Q) How can I change the port number?  
A) configure your nginx.

Q) How can I change the manga directory?  
A) See comments index.php, $parent_path = "manga";

Q) Does comix-server support password protection?  
A) Yes, using Apache's basic authentication mechanism. Refer to 
   <http://www.cs.duke.edu/csl/faqs/web/basic-auth> to know how to
   configure it. Note that the user name must be AirComix (case
   sensitve) and .htaccess file should be in /var/services/web/comix where
   handler.php exists. If there is no htpasswd util in your system, 
   you can create the password file on other machines and copy it to
   your system.
   
Q) I cannot see some files under the manga directory. What is the problem?   
A) If you have a directory which contains image files as well as ZIP files, 
   move image files (or ZIP files) to another directory. 
   A single directory can have multiple image files or multiple ZIP files, 
   but not both.  


## License

Comix-server is free software licensed under [GNU GPLv3](http://www.gnu.org/licenses/gpl.txt). 
Everyone is permitted to copy, modify, and redistribute it.
