#AWS

## set server time zone date

> dpkg-reconfigure tzdata		
> asia		
> taipei

## add user

> adduser leo_wang		

## install webserver of nginx

> apt-get install nginx

## Install php fpm, php mysql, php-cli, php5-mcrypt, php5-curl, php5-imagick, php-gd

> apt-get install php5-fpm php5-mysql php5-cli php5-mcrypt php5-curl php5-imagick php5-gd			
> apt-get install php5-memcached memcached		
> php5enmod mcrypt

## Add or Modifiy /etc/nginx/nginx.conf

> client_max_body_size 128M;    
> worker_processes 2; (if instance core is 2 機器核心數量)

## Add or Modifiy /etc/php5/fpm/php.ini 
> cgi.fix_pathinfo = 0
> mbstring.internal_encoding = UTF-8 (unucomment)
> max_input_vars = 5000

## Modify /etc/php5/fpm/pool.d/www.conf

for web: 
> pm.max_children = 50		
> pm.start_servers = 10		
> pm.min_spare_servers = 5		
> pm.max_spare_servers = 15

for fps: 
> pm.max_children = 100		
> pm.start_servers = 40		
> pm.min_spare_servers = 20		
> pm.max_spare_servers = 60

## Add a EBS to this instance which position at /storage/mysql (only on Dev)

> mount /dev/svdf /storage/mysql

## Install MySQL and set /etc/mysql/my.cnf (only on Dev)

> apt-get install mariadb-server		
> set datadir = /storage/mysql/data		
> set default-time-zone = ‘+8:00’

## Install graph handler imagemagic libaray

> apt-get install imagemagick

* convert for anyone and it’s orginal path is /etc/alternatives/convert (黑名單機制，選配)

## SSH use password login

> sudo vi /etc/ssh/sshd_config

### modifity 
PasswordAuthentication yes    
PubkeyAuthentication no

## Install phpMyAdmin

* test mysql
```shell
$ service mysql start
```

* install wget
```shell
$ apt-get install wget
```

* install phpMyAdmin, go to [official site](https://www.phpmyadmin.net/downloads/) and get the download link   
```shell
$ cd /tmp
$ wget https://files.phpmyadmin.net/phpMyAdmin/4.5.5/phpMyAdmin-4.5.5-all-languages.tar.gz
$ tar -xzf phpMyAdmin-4.5.5-all-languages.tar.gz
```
* mv phpmyadmin folder to nginx's default site folder   
```shell
$ mv phpMyAdmin-4.5.5-all-languages phpmyadmin
$ mv ./phpmyadmin /usr/share/nginx/html
```
* modify nginx's default host
```shell
$ vi /etc/nginx/sites-available/default
```
as...
```
server {
        listen 80 default_server;
        listen [::]:80 default_server ipv6only=on;

        root /usr/share/nginx/html;
        index index.html index.htm index.php;

        # Make site accessible from http://localhost/
        server_name localhost;

        location / {
                # First attempt to serve request as file, then
                # as directory, then fall back to displaying a 404.
                try_files $uri $uri/ =404;
                # Uncomment to enable naxsi on this location
                # include /etc/nginx/naxsi.rules
        }
        
        # pass the PHP scripts to FastCGI server listening on 127.0.0.1:9000
        #
        location ~ \.php$ {
                fastcgi_split_path_info ^(.+\.php)(/.+)$;
        #       # NOTE: You should have "cgi.fix_pathinfo = 0;" in php.ini
        #
        #       # With php5-cgi alone:
        #       fastcgi_pass 127.0.0.1:9000;
        #       # With php5-fpm:
                fastcgi_pass unix:/var/run/php5-fpm.sock;
                fastcgi_index index.php;
                include fastcgi_params;
        }
}
```
* test link of phpmyadmin
