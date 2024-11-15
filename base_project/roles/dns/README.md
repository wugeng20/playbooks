# Ansible Role: DNS

配置DNS服务

## 介绍

DNS (Domain Name System) 是互联网的一项服务，它将域名解析为IP地址，使得用户可以通过域名访问网站。

## 要求

此角色仅在RHEL及其衍生产品上运行。

## 测试环境

ansible 2.9.27
Python 3.11.9
Centos 7.9 X64

## 角色变量

```yaml
---
# DNS configuration
dns_servers:
  - 119.29.29.29
  - 223.5.5.5
  - 8.8.8.8
```

## Example Playbook

```yaml
- hosts: test
  roles:
    - dns
```

## 使用

无
