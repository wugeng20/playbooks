# Ansible Playbook: base_project

Base是一个系统基础配置自动化部署的Ansible Playbook。

## 介绍

Base是一个系统基础配置自动化部署的Ansible Playbook，它可以帮助您快速地部署和配置您的服务器环境。它包含了各种常见的系统配置，如网络配置、用户管理、软件安装等，并且可以轻松地扩展以满足您的需求。

## 功能

- 网络配置：配置网络接口、DNS、NTP等。
- 软件安装：安装常用的软件包，如Python3、Ansible等。
- 系统配置：配置系统参数，如文件系统、内核参数等。

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
- deploy_python3.yml: 安装Python3的Playbook文件。

## 使用

- 克隆或下载本项目到您的本地环境。

```shell
git clone https://gitee.com/wiiuii/playbooks.git
```

- 修改inventory文件中的主机信息，添加需要部署的主机信息。

```shell
cd playbooks/base_project
vi inventory
------------------------------
# 根据实际环境添加需要部署的主机信息。
[test]
192.168.100.231 ansible_user=root ansible_port=22
```

- 在项目根目录下运行以下命令来执行Playbook：

```shell
cd playbooks/base_project

# 【不推荐】一键部署所有服务，包括部署Python等
ansible-playbook -i inventory site.yml

# 【推荐】模块化安装，根据需要选择安装服务
# 单独部署Python3
ansible-playbook -i inventory ./roles/python3/main.yml -e "target_hosts=test" <-<hosts>主组名
ansible-playbook -i inventory ./roles/dns/main.yml -e "target_hosts=test" <-<hosts>主组名
......
```

## 注意事项

- [非常重要] ansible.cfg文件中，请确保 `[defaults]`部分中的 `roles_path`参数指向roles目录。
- 请确保您的Ansible版本与Playbook兼容。
- 请根据您的实际环境修改inventory文件中的主机信息。
