# ansible-role-servermonkey-ww-logger

Extra logging system for wildwest https://github.com/ServerMonkey/wildwest

This role will save a variable to a custom log file and append the log files
name to a list.

## Usage

Save stdout to a logfile:

```
- name: Deploy environment
  shell: "echo Hello World"
  register: shell_command
  become: true

- include_role: name=servermonkey.ww_logger
  vars:
    ww_log: "{{ shell_command }}"
    ww_logfile: servermonkey.hello
```

Save a variable to a logfile:

```
- include_role: name=servermonkey.ww_logger
  vars:
    ww_msg: "World Hello"
    ww_logfile: servermonkey.world
```

If you are not using wildwest and only Ansible, you can use this role anyway.
Just disable logging in your playbook:

```
set_fact:
  ww_nolog: true
```

To log shell script output directly via ww_logger take a look at:
https://github.com/ServerMonkey/ansible-role-servermonkey-sh
