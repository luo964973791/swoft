# 克隆
git clone https://github.com/swoft-cloud/swoft  
# 进入目录  
cd swoft  
# 修改docker-composer.yml 最后一行  

# 进入  
docker exec -it swoft /bin/bash 
# 安装中国源  
composer config -g repo.packagist composer https://packagist.phpcomposer.com && composer install  

#重启  
docker-compose up --build -d  
