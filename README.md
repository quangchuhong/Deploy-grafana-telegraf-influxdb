# Ansible-grafana-telegraf-influxdb-tags-handers
Triển khai cài đặt ansible-tags-hander tool grafana monitor

# Cấu Trúc triển khai cài đặt hệ thống Monitor Grafana-Influxdb-Telegraf
- Roles: Grafana - Telegraf - Influxdb.

- OS: Triển khai trên hai hệ điều hành Ubuntu16.04 vs CentOS 7.

- Site.yml: File run install tất cả các Roles.

- Copy-telegraf.yml: Copy bộ config template đến all Clients monitor.

- File hosts: Config ansible_ssh_user clients.

# Run file install on Ansibles:

sudo ansible-playbook -i hosts site.yml

sudo ansible-playbook -i hosts site.yml --user quangch --ask-pass

sudo ansible -i hosts -m ping all

# Config Firewall on server grafana
- Centos7: Open port 3000:

    Step 1 – Disable SELinux
    The first step is to check the SELinux status and disable it if it is enabled.

    getenforce
    Modify SELinux configurations as follows:

    vim /etc/sysconfig/selinux
    Change SELINUX=enforcing to SELINUX=disabled

    Reboot system.

    reboot

    Step 2 – Modify Firewall
    Change firewall configuration to allow Grafana port. So run following command.

    firewall-cmd --zone=public --add-port=3000/tcp --permanent
    Reload firewall service.

    firewall-cmd --reload

- Ubuntu16.04: Open port 3000:

    netstat -plntu
    ufw allow ssh
    ufw allow 3000/tcp
    ufw enable
    ufw status


# Cài đặt Ansible vs configure on Ubuntu 18.04.

1. Install Ansible on ubuntu

- Add the following line to /etc/apt/sources.list:

  deb http://ppa.launchpad.net/ansible/ansible/ubuntu trusty main
  
  Then run these commands:

  $ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 93C4A3FD7BB9C367
  
  $ sudo apt update
  
  $ sudo apt install ansible

2. Config ssh from Ansible host to Client

- ansible ping all host and run with user vs ask  pass:

  $ ansible -i hosts -m ping all

  $ sudo ansible -m ping -i hosts all --user quangch --ask-pass

- Add ansible ssh key to Clients:

  $ ssh-keygen -t rsa
  $ ssh-copy-id -i quangch@192.168.1.100
  $ ssh quangch@192.168.1.100
  $ ssh-agent bash
  $ ssh-add ~/.ssh/id_rsa

3. Running file install tu Ansible host

- run ansible-playbook Ask Pass SSH host

  $ sudo ansible-playbook -i hosts site.yml --user quangch --ask-pass



