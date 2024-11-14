# 概述

本项目是一个基于Ansible的Playbook，用于自动化部署业务。

# 系统环境

在开始之前，请确保您已经安装了以下软件 or 系统（本仓库主要以CentOS 7进行的，部分模块可能不适用于其他系统。）：

- CentOS 7+
- Python 3.8+
- Ansible 2.9+

# 安装

- 安装、配置ansible、python3、git 自行百度一下
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
cd playbooks/<playbook_project>

# 【不推荐】一键部署所有服务
ansible-playbook -i inventory site.yml

# 【推荐】模块化安装，根据需要选择安装服务
# -----------------示例-----------------#
# 单独部署Docker、Docker-Compose服务
ansible-playbook -i inventory deploy_docker.yml

# 有docker、docker-compose的情况下，单独部署思源笔记服务，没有Docker则报错
ansible-playbook -i inventory deploy_siyuan.yml
......
```

# 注意事项

- 本项目仅供参考，请根据实际需求进行修改。
- 本项目中的脚本和配置文件可能需要根据您的环境进行适当的修改。

# 联系方式

如有任何问题，请通过以下方式联系我们：

- 邮箱：1431258805@qq.com
