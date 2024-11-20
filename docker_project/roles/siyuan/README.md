# Ansible Role: siyuan

部署思源笔记

## 介绍

思源笔记是一款隐私优先的个人知识管理系统，支持细粒度块级引用和 Markdown 所见即所得。

官网: https://b3log.org/siyuan/

## 要求

此角色仅在RHEL及其衍生产品上运行。

## 测试环境

ansible 2.9.27
Python 3.11.9
Centos 7.9 X64

## 角色变量

```yaml
# 思源笔记docker项目目录
- siyuan_dir: /opt/siyuan

# 思源笔记容器workspace目录
- workspace_dir_container: /siyuan/SiYuan/

# 思源笔记秘钥
- siyuan_secret: 1234567890

# 思源笔记docker镜像
- image: b3log/siyuan:latest

# 思源笔记docker容器端口
- port: 6806
```

## Example Playbook

```yaml
- hosts: test
  roles:
    - siyuan
```

## 使用

```shell
cd /opt/siyuan
sudo docker-compose up -d
docker-compose down
---------------
cd playbooks/docker_project

ansible-playbook -i inventory ./roles/siyuan/main.yml -e "target_hosts=test" <-<hosts>主组名

```
