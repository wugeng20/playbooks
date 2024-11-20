# Ansible Role: docker-compose

安装docker-compose

## 介绍

DockerCompose 是一个用于在单个主机上定义和运行多容器Docker应用程序的工具。使用Compose，您可以使用YAML文件来配置您的应用程序服务。然后，使用一个命令，就可以从配置中创建并启动所有服务。

文档: https://docs.docker.com/compose/

## 要求

此角色仅在RHEL及其衍生产品上运行。

## 测试环境

ansible 2.9.27
Python 3.11.9
Centos 7.9 X64

## 角色变量

```yaml
# docker-compose版本
docker_compose_version: "v2.30.3"

# docker-compose下载地址国内加速
docker_compose_url: "https://github.moeyy.xyz/https://github.com/docker/compose/releases/download/{{ docker_compose_version }}/docker-compose-$(uname -s)-$(uname -m)"
```

## Example Playbook

```yaml
- hosts: test
  roles:
    - docker-compose
```

## 使用

```shell
cd playbooks/docker_project

ansible-playbook -i inventory ./roles/docker-compose/main.yml -e "target_hosts=test" <-<hosts>主组名
```
