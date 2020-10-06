# Ansible-Playbook---Disable-root-login

vi ssh.yml
- name: Log in as new user to disable root
  hosts: all
  gather_facts: false
  become: yes
  tasks:
  - name: Disable root login over SSH
    lineinfile: dest=/etc/ssh/sshd_config regexp="^PermitRootLogin" line="PermitRootLogin no" state=present
    notify:
      - restart sshd
