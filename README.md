# larastore
Larastore with Laravel 4

Config Nginx Server 

server {
        listen       80;
        server_name  your_website_name.com;
        root /var/www/larastore/public;
        index index.php index.html index.htm index.nginx-debian.html;
        location / {
                try_files $uri $uri/ =404;
        }
        error_page 404 /404.html;
        error_page 500 502 503 504 /50x.html;
        location = /50x.html {
                root /var/www/html;
        }
        location ~ \.php$ {
                try_files $uri =404;
                fastcgi_pass unix:/var/run/php5-fpm.sock;
                fastcgi_index index.php;
                fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
                include fastcgi_params;
        }
}
