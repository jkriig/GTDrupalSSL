# GTDrupalSSL
-------------
[Presentation given at GT DUG 1/15/16](http://oie2.gatech.edu/gtdrupalssl)

## Notes:
-------------

### Offical Drupal HTTPS Infomation
[Link](https://www.drupal.org/https-information)

### HSTS Information
[Drupal Mod](https://www.drupal.org/project/hsts)

[Wikipedia](https://en.wikipedia.org/wiki/HTTP_Strict_Transport_Security)

## How-to:
-------------


### GT Theme required changes
[Link](https://github.gatech.edu/ICWebTeam/gt-7.x/issues/3)

### .htaccess edits (different than slides)

~~~~
RewriteEngine On
RewriteCond %{HTTPS} !=on
RewriteRule ^ https://%{HTTP_HOST}%{REQUEST_URI} [L,R=301]
~~~~

### Drupal Base URL in Settings.php
Set $base_url to SSL in settings.php.
~~~
$base_url = "https://www.example.com";
~~~


### Creating Symbolic links in httpsdocs

Create a Symlink:
`ln -s /path/to/file /path/to/symlink`

Run the Following:
~~~~
cd httpsdocs/
ln -s ../httpdocs/.htaccess ../httpsdocs/.htaccess
ln -s ../httpdocs/archive/  archive
ln -s ../httpdocs/authorize.php authorize.php
ln -s ../httpdocs/common.css common.css      
ln -s ../httpdocs/cron.php cron.php    
ln -s ../httpdocs/css/ css         
ln -s ../httpdocs/inc/ inc
ln -s ../httpdocs/includes/ includes
ln -s ../httpdocs/index.php index.php
ln -s ../httpdocs/install.php install.php
ln -s ../httpdocs/misc/ misc  
ln -s ../httpdocs/modules/ modules
ln -s ../httpdocs/profiles/ profiles 
ln -s ../httpdocs/scripts/ scripts  
ln -s ../httpdocs/sites/ sites    
ln -s ../httpdocs/themes/ themes
ln -s ../httpdocs/update.php update.php 
ln -s ../httpdocs/xmlrpc.php xmlrpc.php 
~~~

**Important** you must include `../httpdocs/` in your symlink creation to have vaild links!  

List of links and locations that need to be created.
~~~~
bash-4.1$ cd httpsdocs/
bash-4.1$ ls -la
total 16
drwxr-x---.  4 oie2 psaserv 4096 Oct 16 12:16 .
drwx--x---. 21 oie2 psaserv 4096 Jan 14 21:04 ..
lrwxrwxrwx.  1 oie2 psacln    21 Jan 27  2015 .htaccess -> ../httpdocs/.htaccess
lrwxrwxrwx.  1 oie2 psacln    20 Jan 27  2015 archive -> ../httpdocs/archive/
lrwxrwxrwx.  1 oie2 psacln    25 Oct 16 12:16 authorize.php -> ../httpdocs/authorize.php
lrwxrwxrwx.  1 oie2 psacln    22 Jan 27  2015 common.css -> ../httpdocs/common.css
lrwxrwxrwx.  1 oie2 psacln    20 Jan 27  2015 cron.php -> ../httpdocs/cron.php
lrwxrwxrwx.  1 oie2 psacln    15 Jan 27  2015 css -> ../httpdocs/css
lrwxrwxrwx.  1 oie2 psacln    23 Jan 27  2015 favicon.ico -> ../httpdocs/favicon.ico
lrwxrwxrwx.  1 oie2 psacln    15 Jan 27  2015 inc -> ../httpdocs/inc
lrwxrwxrwx.  1 oie2 psacln    21 Jan 27  2015 includes -> ../httpdocs/includes/
lrwxrwxrwx.  1 oie2 psacln    21 Jan 27  2015 index.php -> ../httpdocs/index.php
lrwxrwxrwx.  1 oie2 psacln    23 Jan 27  2015 install.php -> ../httpdocs/install.php
lrwxrwxrwx.  1 oie2 psacln    17 Jan 27  2015 misc -> ../httpdocs/misc/
lrwxrwxrwx.  1 oie2 psacln    17 Jan 27  2015 misc -> ../httpdocs/misc/
lrwxrwxrwx.  1 oie2 psacln    20 Jan 27  2015 modules -> ../httpdocs/modules/
lrwxrwxrwx.  1 oie2 psacln    21 Jan 27  2015 profiles -> ../httpdocs/profiles/
lrwxrwxrwx.  1 oie2 psacln    20 Jan 27  2015 scripts -> ../httpdocs/scripts/
lrwxrwxrwx.  1 oie2 psacln    18 Jan 27  2015 sites -> ../httpdocs/sites/
lrwxrwxrwx.  1 oie2 psacln    19 Jan 27  2015 themes -> ../httpdocs/themes/
lrwxrwxrwx.  1 oie2 psacln    22 Jan 27  2015 update.php -> ../httpdocs/update.php
lrwxrwxrwx.  1 oie2 psacln    22 Jan 27  2015 xmlrpc.php -> ../httpdocs/xmlrpc.php
bash-4.1$
~~~~ 
