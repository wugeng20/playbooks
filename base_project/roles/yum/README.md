# Ansible Role: YUM

配置yum国内源

## 介绍

yum是RHEL及其衍生产品上的包管理工具，此角色用于配置yum国内源。

## 要求

此角色仅在RHEL及其衍生产品上运行。

## 测试环境

ansible 2.9.27
Python 3.11.9
Centos 7.9 X64

## 角色变量

```yaml
---
# 默认变量，定义国内源URL
repo_download_url: "http://mirrors.aliyun.com/repo/Centos-7.repo"
```

## Example Playbook

```yaml
- hosts: test
  roles:
    - yum
```

## 使用

```shell
cd playbooks/base_project

ansible-playbook -i inventory ./roles/yum/main.yml -e "target_hosts=test" <-<hosts>主组名
```
