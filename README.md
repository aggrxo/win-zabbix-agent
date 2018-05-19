# Ansible role for install Zabbix-Agent on the Windows Server


##### Tested platforms are:
* Windows Server 2012 R2


##### Dependency:
This role uses the WinRM module on the local and remote machine.
WinRM module for local machine: `pip install https://github.com/diyan/pywinrm/archive/master.zip#egg=pywinrm`

WinRM module for Windows machine (use PowerShell console): `@powershell -NoProfile -ExecutionPolicy Bypass -Command "iex ((new-object net.webclient).DownloadString('https://github.com/ansible/ansible/raw/devel/examples/scripts/ConfigureRemotingForAnsible.ps1'))"`


##### Role Variables
* zabbix_server_ip - variable for setting IP address of zabbix-server
* zabbix_agent_url - variable for setting URL of zabbix-agent archive
* zabbix_agent_ip - listen IP address in zabbix-agent configuration
* zabbix_agent_port - listen port in zabbix-agent configuration
* zabbix_agent_timeout - timeout for working query in zabbix-agent 



##### Example Inventory file
```
[windows]
10.10.10.4

[windows:vars]
ansible_ssh_user=Administrator
ansible_ssh_port=5986
ansible_connection=winrm
ansible_winrm_server_cert_validation=ignore
```


##### Example Playbook
```
---
- hosts: windows
  remote_user: Administrator
  vars:
    - zabbix_server_ip: '10.10.10.22'
  roles:
    - windows.zabbix
```


Issue? use [https://github.com/qwsj/win-zabbix-agent/issues](https://github.com/qwsj/win-zabbix-agent/issues)
