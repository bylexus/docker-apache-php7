apache-php7
===================================

A Docker image based on Ubuntu, serving PHP 7 running as Apache Module. Useful for Web developers in need for a fixed PHP version. In addition, the `error_reporting` setting in php.ini is configurable per container via environment variable.

Tags
-----

* latest: Ubuntu 16.04 (LTS), Apache 2.4, PHP 7.0.x with support for setting `error_reporting`

Usage
------

```
$ docker run -d -P bylexus/apache-php7
```

With all the options:

```bash
$ docker run -d -p 8080:80 \
    -v /home/user/webroot:/var/www \
    -e PHP_ERROR_REPORTING='E_ALL & ~E_STRICT' \
    bylexus/apache-php7
```

* `-v [local path]:/var/www` maps the container's webroot to a local path
* `-p [local port]:80` maps a local port to the container's HTTP port 80
* `-e PHP_ERROR_REPORTING=[php error_reporting settings]` sets the value of `error_reporting` in the php.ini files.

### Access apache logs

Apache is configured to log both access and error log to STDOUT. So you can simply use `docker logs` to get the log output:

`docker logs -f container-id`


Installed packages
-------------------
* Ubuntu Server 16.10, based on ubuntu docker image
* apache2
* php
* php-cli
* libapache2-mod-php
* php-apcu
* php-apcu-bc
* php-gd
* php-json
* php-ldap
* php-mbstring
* php-mysql
* php-opcache
* php-pgsql
* php-sqlite3
* php-xml
* php-xsl
* php-zip
* php-soap
* php-xdebug
* composer (php package manager)

Default Configurations
----------------------

* Apache: .htaccess-Enabled in webroot (mod_rewrite with AllowOverride all)
* php.ini:
  * display_errors = On
  * error_reporting = E_ALL (default, overridable per env variable)

