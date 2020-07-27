# Ansible-grafana-telegraf-influxdb
Triển khai hệ thống monitor tool grafana

# Cấu Trúc triển khai cài đặt hệ thống Monitor Grafana-Influxdb-Telegraf
- Roles: Grafana - Telegraf - Influxdb - iptables

- OS: Triển khai trên hai hệ điều hành Ubuntu16.04 vs CentOS 7.

- Site.yml: File run install Roles.

- Copy-telegraf.yml: Copy bộ config template đến all agent.

- File hosts: List ip server

- Template: telegraf.conf.j2. f

# Run Ansibles:

- ansible-playbook -i hosts site.yml

- ansible-playbook -i hosts site.yml --user quangch --ask-pass

- ansible -i hosts -m ping all

- ansible-playbook -i hosts site.yml --tags install-telegraf
  
- ansible-playbook -i hosts site.yml --tags install-grafana
  
- ansible-playbook -i hosts site.yml --tags install-influxdb

# Config Firewall on server 




# Config ssh from Ansible host to Client

- ssh-keygen -t rsa
  
- ssh-copy-id -i quangch@192.168.1.100
  
- ssh quangch@192.168.1.100
 
- ssh-agent bash
  
- ssh-add ~/.ssh/id_rsa


  


