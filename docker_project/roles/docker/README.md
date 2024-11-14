# 概述

本项目是一个基于Ansible的Playbook，用于自动化部署Docker容器。

# 前置条件

在开始之前，请确保您已经安装了以下软件 or 系统：

- CentOS 7+系统
- Python3.8+
- Ansible (pip install ansible && yum install ansible)

# 运行方法

克隆或下载本项目到您的本地环境。在项目根目录下运行以下命令来执行Playbook：

```shell
ansible-playbook -i inventory tests/test.yml
```

# 目录详细说明：

- **defaults/main.yml** :包含默认变量，例如Docker镜像名称、版本号、镜像源等。
- **handlers/main.yml** :包含处理程序，例如在Docker容器启动或停止时执行的操作。
- **README.md** :项目的说明文档，解释如何使用这个Playbook。
- **tasks/main.yml** :主要任务文件，包含构建Docker镜像、启动容器、停止容器等任务。
- **tests/inventory** :测试环境的库存文件，定义测试主机。
- **tests/test.yml** :测试Playbook，用于验证部署是否成功。

---
