#Nginx for Linux

* php5-fpm
* php5-mysql
* php5-cli
* php5-mcrypt
* php5-curl
* php5-gd
* mariadb (MySql)

##Install nginx

	apt-get install nginx

##Install php5

	apt-get install php5-fpm php5-mysql php5-cli php5-mcrypt php5-curl php5-gd
	
###Modifity php.ini & nginx.conf

etc/php5/fpm/php.ini

	fix_pathinfo = 0
	
etc/nginx/nginx.conf

	client_max_body_size = 128M
	
##Install MySql
[See mariadb] (https://blog.mariadb.org/installing-mariadb-galera-cluster-on-debian-ubuntu/)

	apt-get install married-server-5.5
	
*note : remember account, password*

Test Mysql

	mysql -u root -h 127.0.0.1 -p

###Modifity my.conf

	default-time-zone = '+8:00'

##Install imagemagic libaray

	apt-get install imagemagickss

##Install phpmyadmin
[See phpmyadmin] (https://www.phpmyadmin.net/downloads/)

* Download to /user/share/nginx/html/phpMyAdmin
* Set /etc/nginx/site-enabled/default

		index index.html index.htm index.php;
		...
		location ~ \.php$ {
		fastcgi_split_info ^(.+\.php)(/.+)$;
		# # NOTE: You should have "cgi.fix_pathinfo = 0;" in php.ini
		#
		# # With php5-cgi alone:
		# fastcgi_pass 127.0.0.1:9000;
		# # With php5-fpm:
		fastcgi_pass unix:/var/run/php5-fpm.sock;
		fastcgi_index index.php;
		include fastcgi_params;
		try_files $uri =404;
		}
		...

##Q&A
Q. See nginx log  
A. /var/log/nginx/error.log  
Q. Permission denied  
A. Progject set permission 775  


