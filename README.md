# 技能清单
1. 雪花算法
2. gin框架
2. zap日志库
3. Viper配置管理
4. swagger生成文档
5. JWT认证
6. 令牌桶限流
7. Go语言操作MySQL **(sqlx)**
8. Go语言操作Redis **(go-redis)**
10. Gihub热榜
12. Docker部署
13. Vue框架
14. ElementUI
15. axios 

# 项目目录结构
## 后端结构树
```bash
.
├── Dockerfile
├── Makefile
├── README.md
├── bin
│   ├── bluebell-plus
│   └── bluebell-plus.conf
├── conf
│   └── config.yaml
├── controller
│   ├── code.go
│   ├── comment.go
│   ├── community.go
│   ├── doc_response_models.go
│   ├── post.go
│   ├── post_test.go
│   ├── request.go
│   ├── response.go
│   ├── user.go
│   ├── validator.go
│   └── vote.go
├── dao
│   ├── mysql
│   │   ├── comment.go
│   │   ├── community.go
│   │   ├── error_code.go
│   │   ├── mysql.go
│   │   ├── post.go
│   │   ├── post_test.go
│   │   └── user.go
│   └── redis
│       ├── error.go
│       ├── keys.go
│       ├── post.go
│       ├── redis.conf
│       ├── redis.go
│       └── vote.go
├── docker-compose.yml
├── docs
│   ├── docs.go
│   ├── swagger.json
│   └── swagger.yaml
├── go.mod
├── go.sum
├── init.sql
├── log
│   └── bluebell-plus.log
├── logger
│   └── logger.go
├── logic
│   ├── community.go
│   ├── post.go
│   ├── truncate.go
│   ├── user.go
│   └── vote.go
├── main.go
├── middlewares
│   ├── auth.go
│   └── ratelimit.go
├── models
│   ├── comment.go
│   ├── community.go
│   ├── create_tables.sql
│   ├── params.go
│   ├── post.go
│   └── user.go
├── pkg
│   ├── jwt
│   │   └── jwt.go
│   └── snowflake
│       └── gen_id.go
├── routers
│   └── routers.go
├── settings
│   └── settings.go
├── static
│   ├── css
│   │   ├── app.5c39da08.css
│   │   └── chunk-vendors.5b539fe5.css
│   ├── favicon.ico
│   ├── fonts
│   │   ├── element-icons.535877f5.woff
│   │   ├── element-icons.732389de.ttf
│   │   ├── fontello.068ca2b3.ttf
│   │   ├── fontello.8d4a4e6f.woff2
│   │   ├── fontello.a782baa8.woff
│   │   └── fontello.e73a0647.eot
│   ├── img
│   │   ├── avatar.7b0a9835.png
│   │   ├── fontello.9354499c.svg
│   │   ├── iconfont.cdbe38a0.svg
│   │   ├── logo.938d1d61.png
│   │   └── search.8e85063d.png
│   └── js
│       ├── app.81e7c3d0.js
│       ├── app.81e7c3d0.js.map
│       ├── chunk-vendors.218b058e.js
│       └── chunk-vendors.218b058e.js.map
├── templates
│   └── index.html
├── version.go
└── wait-for.sh
```
## 前端结构树
```bash
├── bin
│   └── bluebell-plus
├── conf
│   └── config.yaml
├── static
│   ├── css
│   │   └── app.0afe9dae.css
│   ├── favicon.ico
│   ├── img
│   │   ├── avatar.7b0a9835.png
│   │   ├── iconfont.cdbe38a0.svg
│   │   ├── logo.da56125f.png
│   │   └── search.8e85063d.png
│   └── js
│       ├── app.9f3efa6d.js
│       ├── app.9f3efa6d.js.map
│       ├── chunk-vendors.57f9e9d6.js
│       └── chunk-vendors.57f9e9d6.js.map
└── templates
    └── index.html
```


# 项目环境
## github

远程连接url：git@github.com:Cloud1fly/bluebell-blog-forum.git

在linux下将本地代码提交至github上:
```
1. 生成秘钥：ssh-keygen -t rsa -C "XXX@163.com"
2. 查看密钥路径： cat ~/.ssh/id_rsa.pub
3. SSH keys添加到github上
4. 本地克隆仓库： git@github.com:Cloud1fly/bluebell-blog-forum.git
```

git提交代码到github：
```
1. git add *
2. git commit -m <message>
3. git status
4. git push
```

git提示 Your branch is up-to-date with 'origin/master' :
```
1. 新建一个分支： git branch newBranch
2. 检查分支是否创建成功： git branch
3. 切换到新建的分支： git checkout newBranch
4. 将改动提交到新分支: git add .
5. git commit -m "the new branch"
6. 新分支提交的改动合并到主分支: git merge newBranch
7. 查看是否提交成功: git status
8. push代码到远端仓库: git push -u origin main
9. 删除新分支: git branch -D newBranch
```

git常用命令：
```
git clone <address>：复制代码库到本地；
git add <file> ...：添加文件到代码库中；
git rm <file> ...：删除代码库的文件；
git commit -m <message>：提交更改，在修改了文件以后，使用这个命令提交修改。
git pull：从远程同步代码库到本地。
git push：推送代码到远程代码库。
git branch：查看当前分支。带*是当前分支。
git branch <branch-name>：新建一个分支。
git branch -d <branch-name>：删除一个分支。
git checkout <branch-name>：切换到指定分支。
git log：查看提交记录（即历史的 commit 记录）。
git status：当前修改的状态，是否修改了还没提交，或者那些文件未使用。
git reset <log>：恢复到历史版本。
```


## mysql环境搭建
1. 用docker创建一个mysql容器
```
docker run --name (容器名) -e MYSQL_ROOT_PASSWORD=123456 -d -e MYSQL_DATABASE=(database初始化名字) -p 8086:3306 mysql:8.0

docker run：这是用于在 Docker 上运行容器的命令。
--name (容器名)：通过 --name 参数指定容器的名称为 (容器名)。
-e MYSQL_ROOT_PASSWORD=123456：通过 -e 参数设置环境变量 MYSQL_ROOT_PASSWORD 的值为 123456，这将作为 MySQL 的 root 用户的密码。
-d：通过 -d 参数让容器在后台运行（detached 模式）。
-e MYSQL_DATABASE=(database初始化名字)：通过 -e 参数设置环境变量 MYSQL_DATABASE 的值为 (database初始化名字)，这将在容器中创建一个名为 (database初始化名字) 的数据库。
-p 8086:3306：通过 -p 参数将容器的端口 3306 映射到主机的端口 8086，这样可以通过主机的 8086 端口访问 MySQL 服务。
mysql:8.0：指定要运行的镜像为 mysql:8.0，这将从 Docker Hub 上拉取 MySQL 8.0 版本的镜像并在容器中运行。
```

不指定database初始化名字登入mysql：
```
docker run --name docker_mysql -e MYSQL_ROOT_PASSWORD=123456 -d -p 8086:3306 mysql:8.0
```


2. 查看docker是否启动
```
docker ps     //列出当前正在运行的容器。如果不加任何选项，这个命令只会列出正在运行的容器。
dokcer ps -a  //显示所有的容器，包括正在运行的和已经停止的容器
docker ps -aq //-q 选项表示只显示容器的 ID。
```

3. 登入容器内的mysql
```
指定登录数据库名字： docker run -it --network=host mysql:8.0 mysql -h 0.0.0.0 (database名字) -P 8086 -u root -p
不指定登录数据库名字：docker run -it --network=host mysql:8.0 mysql -h 0.0.0.0 -P 8086 -u root -p
```

4. 删除容器内的mysql
```
docker rm CONTAINER ID 
```

5. 启动/删除docker所有容器
```
docker start $(docker ps -aq)  //启动所有容器
docker stop $(docker ps -aq)   //停止所有容器
docker rm $(docker ps -aq)     //删除所有容器
```


## 使用navicat连接mysql

直接连接即可

# redis环境搭建
1. 启动redis服务
```
docker run --name (redis_name) -d -p 8089:6379 redis:6.2-rc2
```

2. 查看
```
docker ps
```

3. 在开发机上验证redis是否ok
```
docker exec -it <CONTAINER ID> redis-cli -h 0.0.0.0 -p 6379

docker exec -it 574071e2feef redis-cli -h 0.0.0.0 -p 6379

<CONTAINER ID> 是docker ps中查看的ID
```