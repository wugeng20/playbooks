# Ansible Role: Python3

安装Python3

## 介绍

Python3是Python的第三个版本，它引入了许多新特性，包括类型提示、异步编程、改进的垃圾回收等。Python3是Python的官方版本，它向后不兼容Python2，因此需要安装Python3才能运行Python3代码。

官网: https://www.python.org/

## 要求

此角色仅在RHEL及其衍生产品上运行。

## 测试环境

ansible 2.9.27
Python 3.11.9
Centos 7.9 X64

## 角色变量

```yaml
---
python_version: "3.11.9"

# python下载地址
python_download_url: "https://www.python.org/ftp/python/{{ python_version }}/Python-{{ python_version }}.tgz"

# 下载python安装包存放目录
python_download_dir: "/tmp/"

# python安装目录
python_install_dir: "/usr/local/python3"

# python安装源码编译需要的编译环境
python_packages:
  - zlib-devel
  - bzip2-devel
  - openssl-devel
  - ncurses-devel
  - sqlite-devel
  - readline-devel
  - tk-devel
  - gcc
  - make
  - wget

# pip3安装源
pip3_mirror: "https://pypi.tuna.tsinghua.edu.cn/simple"
pip3_trusted_host: " pypi.tuna.tsinghua.edu.cn"
```

## Example Playbook

```yaml
- hosts: test
  roles:
    - python3
```

## 使用

```shell
cd playbooks/base_project

ansible-playbook -i inventory ./roles/python3/main.yml -e "target_hosts=test" <-<hosts>主组名
```
