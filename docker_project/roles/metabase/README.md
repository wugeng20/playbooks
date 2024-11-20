# Ansible Role: Metabase

部署Metabase开原BI系统

## 介绍

Metabase 是一款开源的BI工具，它可以帮助用户轻松地创建和分享数据可视化报表。Metabase支持多种数据源，包括MySQL、PostgreSQL、SQLite、Google Analytics等，用户可以通过简单的SQL查询来获取数据，并使用Metabase提供的可视化工具来创建报表。

官网: https://www.metabase.com/

## 要求

此角色仅在RHEL及其衍生产品上运行。

## 测试环境

ansible 2.9.27
Python 3.11.9
Centos 7.9 X64

## 角色变量

```yaml
---
# 项目目录
metabase_dir: /opt/metabase

# 镜像
metabase_image: metabase/metabase:latest

# 端口
metabase_port: 8100
```

## Example Playbook

```yaml
- hosts: test
  roles:
    - metabase
```

## 使用

```shell
cd /opt/metabase
sudo docker-compose up -d
docker-compose down
---------------
cd playbooks/docker_project

ansible-playbook -i inventory ./roles/metabase/main.yml -e "target_hosts=test" <-<hosts>主组名

```
