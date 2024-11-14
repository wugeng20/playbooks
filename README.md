# 概述

本项目是一个基于Ansible的Playbook，用于自动化部署业务。

# 系统环境

在开始之前，请确保您已经安装了以下软件 or 系统（本仓库主要以CentOS 7进行的，部分模块可能不适用于其他系统。）：

- CentOS 7+
- Python3.8+
- Ansible 2.9+

# 安装

- 安装ansible、python3、git 体自行百度一下
- 克隆本仓库到本地

```shell
git clone https://gitee.com/wiiuii/playbooks.git
```

- 添加主机清单
  进入项目目录下，修改 `inventory` 文件，添加需要部署的主机信息。

```shell
[test]
192.168.100.231 ansible_user=root ansible_port=22
```

- 修改depoly_*.yml中hosts
  ```yaml
  ---
  # 部署docker
  - hosts: test  # <---修改这里
    roles:
      - docker
    become: yes
  ```
- 执行playbook

```shell
ansible-playbook -i inventory site.yml
```

# 注意事项

- 本项目仅供参考，请根据实际需求进行修改。
- 本项目中的脚本和配置文件可能需要根据您的环境进行适当的修改。

# 联系方式

如有任何问题，请通过以下方式联系我们：

- 邮箱：1431258805@qq.com
