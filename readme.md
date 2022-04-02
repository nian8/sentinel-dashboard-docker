# Sentinel Dashboard Docker

[Docker Pulls](https://hub.docker.com/r/cike/sentinel-dashboard-docker)

本项目是 Alibaba Sentinel Dashboard [Sentinel](https://github.com/alibaba/Sentinel).

## Project directory

* build：Sentinel Dashboard makes the source code of the docker image
* env: Environment variable file for compose yaml
* docker-compose: Docker compose example for Sentinel Dashboard server

## Quick Start

Run the following command：

* Clone project

```sh
git clone https://github.com/zhoutaoo/sentinel-dashboard-docker.git
```

* Build Image

```shell
cd build
# 默认 -f Dockerfile
docker build -t nian8/sentinel-dashboard .
docker push nian8/sentinel-dashboard
```

* Run With docker

```sh
docker run -p 8858:8858 -it nian8/sentinel-dashboard
```

* Run With docker-compose

```sh
docker-compose up -d
```

* Open the Sentinel Dashboard console in your browser

link：[http://127.0.0.1:8858](http://127.0.0.1:8858/)

## Common property configuration

| name                         | description                            | option                         |
| ---------------------------- | -------------------------------------- | ------------------------------ |
| SERVER_PORT                  | server启动的端口                         | 8858                           |
| PROJECT_NAME                 | 项目名称                                 | sentinel-dashboard             |
| USERNAME                     | dashboard登陆用户名                      | 默认sentinel                    |
| PASSWORD                     | dashboard登陆密码                        | 默认sentinel                    |
