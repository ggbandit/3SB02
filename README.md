# 3SB02
Lab3SB02
Install docker-compose
//ใส่ลิงค์ บน cmp
curl -L https://github.com/docker/compose/releases/download/1.18.0/docker-compose-`uname -s`-`uname -m` -o /usr/local/bin/docker-compose
chmod +x /usr/local/bin/docker-compose
//วางลิงค์ shift+insert

docker-compose --version
สร้างไฟล์ docker-compose.yml ไว้ในโฟลเดอร์ wp //ต้องแก้โค้ดใหม่ 
version: '3'

services:
   db:
     image: x.coe.phuket.psu.ac.th:8443/wordpress/mysql:5.7
     volumes:
       - db_data:/var/lib/mysql
     restart: always
     environment:
       MYSQL_ROOT_PASSWORD: somewordpress
       MYSQL_DATABASE: wordpress
       MYSQL_USER: wordpress
       MYSQL_PASSWORD: wordpress

   wordpress:
     depends_on:
       - db
     image: x.coe.phuket.psu.ac.th:8443/wordpress/wordpress:latest
     ports:
       - "8000:80"
     restart: always
     environment:
       WORDPRESS_DB_HOST: db:3306
       WORDPRESS_DB_USER: wordpress
       WORDPRESS_DB_PASSWORD: wordpress


//ใช้ tmux
tmux new -s wordpress

เริ่มใช้งาน docker
docker-compose up -d
