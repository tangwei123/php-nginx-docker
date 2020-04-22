# php+nginx的docker容器

## 搭建nginx容器
    注意修改 DockerfileNginx文件，因为每次使用的nginx版本不一样。
    nginx.conf文件，修改 解析php的php-fpm监听的地址和端口，php文件所在路径
    
    运行命令：
            docker build -f DockerfileNginx -t nginx:v1 .
            docker run --ip 182.10.0.18 -d -v nginxfile:/usr/local/nginx --name nginx --net 网络名称 -p 80:80 镜像名称

## 搭建php容器
    注意修改DockerfilePHP文件，因为每次使用的php版本不一样，编译语句可能略有差别，至少php7.2.30这样编译没有问题
    修改php-fpm.conf文件
    修改www.conf文件，修改php-fpm的监听端口等问题
    error.log只要空白即可
    
    运行命令：
            docker build -f DockerfilePHP -t php7:v1 .
            docker run --ip 182.10.0.19 -d -v php7file:/usr/local/php7 --name php7 --net 网络名称 -p 9000:9000 镜像名称