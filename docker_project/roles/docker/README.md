# Ansible Role: docker

安装docker、docker-compose

## 介绍

Docker 是一个开源的应用容器引擎，让开发者可以打包他们的应用以及依赖包到一个可移植的容器中，然后发布到任何流行的 Linux 机器上，也可以实现虚拟化。容器是完全使用沙箱机制，相互之间不会有任何接口。

官网: https://www.docker.com/

## 要求

此角色仅在RHEL及其衍生产品上运行。

## 测试环境

ansible 2.9.27
Python 3.11.9
Centos 7.9 X64

## 角色变量

```yaml
# docker 镜像源
docker_repo: "https://mirrors.aliyun.com/docker-ce/linux/centos/docker-ce.repo"

# docker 历史版本
docker_old:
  - docker
  - docker-common
  - docker-selinux
  - docker-engine

# 依赖包
docker_packages:
  - lvm2
  - yum-utils
  - device-mapper-persistent-data
  - bash-completion

docker_ce_packages:
  - docker-ce
  - docker-ce-cli
  - containerd.io

# docker 镜像加速
docker_registry_mirrors: ["https://docker.1panel.dev"]

# docker-compose版本
docker_compose_version: "v2.30.3"

# docker-compose下载地址国内加速
docker_compose_url: "https://github.moeyy.xyz/https://github.com/docker/compose/releases/download/{{ docker_compose_version }}/docker-compose-$(uname -s)-$(uname -m)"
```

## Example Playbook

```yaml
- hosts: test
  roles:
    - docker
```

## 使用

```shell
cd playbooks/docker_project

ansible-playbook -i inventory ./roles/docker/main.yml -e "target_hosts=test" <-<hosts>主组名
```
