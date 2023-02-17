## MySQL on Docker

### 1. 在 Docker 啟動 mySQL container
#### 1. (Optional) 下載 mySQL image 並 啟動
https://hub.docker.com/_/mysql
```docker
docker pull mysql:8.0
```

#### 2. 使用 ``.yml`` 來啟動 
```yml
version: "2"
services:
  mysql:
    image: mysql:8.0
    container_name: m_mysql
    restart: always
    ports:
      - "3306:3306"
    volumes:
      - ./dbdata:/var/lib/mysql
    environment:
      MYSQL_ROOT_PASSWORD: "password123"
```
背景運行 MySQL container
```docker
docker-compose up -d
```

#### 3. (Optional) 可以使用 phpmyadmin 來檢閱 mySQL的資料庫
```yml
phpmyadmin:
image: phpmyadmin/phpmyadmin:latest
container_name: m_phpmyadmin
restart: always
ports:
    - "9000:80"
environment:
    PMA_HOST: m_mysql
```


### 2. 在 Docker 中更改 MySQL 的密碼
值得注意的是，即使你關閉 mySQL container，並且更改 yml 檔密碼來啟動，密碼仍會是舊的。
這是因為你的data沒有清乾淨，docker 會一直抓舊的資料，因此我們需要進入 mySQL 中直接修改 ``USER`` Table。

#### 1. 先在docker 中運行 mysql container
```docker
docker exec -it [mysql container name] mysql -uroot -p
```
並接著輸入原密碼，順利進入 mySQL。

#### 2. 更改 ``USER`` Table 的資料
``` sql
ALTER USER 'root'@'localhost' IDENTIFIED BY 'MyN3wP4ssw0rd';
exit;
```

#### 3. 測試更改是否成功
```docker
docker exec -it [mysql container name] mysql -uroot -p
```
輸入新密碼測試是否可以登入。