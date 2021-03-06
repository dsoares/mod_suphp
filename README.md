mod_suphp
=========

Spec and patch files to build mod_suphp-0.7.1 RPMs for el7.

In order to activate mod_suphp support, `/etc/httpd/conf.d/mod_suphp.conf`
has to be edited.

Please note that **by default the module is loaded but not activated**.
After a restart of the httpd, php scripts will still be handled by the default mod_php.
**suPHP activation will be done on a virtual host or directory basis**.

To activate mod_suphp support for a certain virtual host or directory,
you can selectively enable mod_suphp:
```
  <Directory "/var/www/html">
    AddHandler x-httpd-php .php .php3 .php4 .php5 .phtml
    php_admin_flag engine off
    suPHP_Engine on
    suPHP_AddHandler x-httpd-php
    suPHP_RemoveHandler .php
    suPHP_UserGroup ##YOUR_USER##  ##USERGROUP##
  </Directory>
```

Should you require mod_userdir support, in order to enable ~user URLs, you should set 
`check_vhost_docroot=false` in the `/etc/suphp.conf` file, as currently suphp would fail
with an incorrect vhost.

`old` is just a folder to keep old patches (found in fedora repository). Not used.
