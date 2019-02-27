# 克隆
git clone https://github.com/swoft-cloud/swoft  
# 进入目录  
cd swoft  
# 修改docker-composer.yml 最后一行  
version: '3'

services:
    swoft:
    image: swoft/swoft:latest
       container_name: swoft
       ports:
         - "666:80"
       volumes:
         - ./:/var/www/swoft
       stdin_open: true
       tty: true
       privileged: true
       entrypoint: ["sh"]
# 进入  
docker exec -it swoft /bin/bash 

# 安装中国源  
composer config -g repo.packagist composer https://packagist.phpcomposer.com && composer install  

# 继续修改docker-composer.yml  
version: '3'

services:
    swoft:
       image: swoft/swoft:latest
       container_name: swoft
       ports:
         - "666:80"
       volumes:
         - ./:/var/www/swoft
       stdin_open: true 
       tty: true
       privileged: true
       entrypoint: ["php", "/var/www/swoft/bin/swoft", "start"]  

#重启  
docker-compose up --build -d  
