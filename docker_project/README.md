# Ansible Playbook: docker_project

Docker项目自动化部署的Ansible Playbook。

## 介绍

此Playbook用于自动化部署Docker容器服务，包括：

- 安装Docker、Docker-Compose
- 安装Docker项目：思雨笔记等

## Docker项目

- roles/docker: Docker、Docker-Compose
- roles/siyuan: 思源笔记

## 要求

此角色仅在RHEL及其衍生产品上运行。

## 测试环境

ansible 2.9.27
Python 3.11.9
Centos 7.9 X64

## Playbook File

- site.yml: 主Playbook文件，包含所有角色的调用。
- inventory: Ansible inventory文件，定义了要部署的主机。
- roles: 角色目录，包含所有角色的定义。
- .ansible.cfg: Ansible配置文件，定义了Ansible的行为。
- README.md: 项目说明文件。
- deploy_docker.yml: 部署Docker的Playbook文件。
- deploy_siyuan.yml: 部署思源笔记的Playbook文件。

## 使用

- 克隆或下载本项目到您的本地环境。

```shell
git clone https://gitee.com/wiiuii/playbooks.git
```

- 修改inventory文件中的主机信息，添加需要部署的主机信息。

```shell
cd playbooks/docker_project
vi inventory
------------------------------
# 根据实际环境添加需要部署的主机信息。
[test]
192.168.100.231 ansible_user=root ansible_port=22
```

- 在项目根目录下运行以下命令来执行Playbook：

```shell
cd playbooks/docker_project

# 【不推荐有Docker/Docker-Compose下使用】一键部署所有服务，包括Docker、Docker-Compose、思源笔记等
ansible-playbook -i inventory site.yml

# 【推荐有Docker/Docker-Compose下使用】模块化安装，根据需要选择安装服务
# 单独部署Docker、Docker-Compose服务
ansible-playbook -i inventory ./roles/docker/main.yml -e "target_hosts=test" <-<hosts>主组名

# 有docker、docker-compose的情况下，单独部署思源笔记服务，没有Docker则报错
ansible-playbook -i inventory ./roles/siyuan/main.yml -e "target_hosts=test" <-<hosts>主组名
......
```

## 注意事项

- [非常重要] ansible.cfg文件中，请确保 `[defaults]`部分中的 `roles_path`参数指向roles目录。
- 请确保您的Ansible版本与Playbook兼容。
- 请根据您的实际环境修改inventory文件中的主机信息。
