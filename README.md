# postgresql
community postgresql release

## AWS
Edit `configuration.yml` and change the region to match the closest geographic AWS [region](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-regions-availability-zones.html#concepts-available-regions). Run via the following:

     AWS_PROFILE=svx-ProdA ./provision-postgresql -e "configuration=aws-configuration.yml"

Enter proxy location:
        
        ./eg-certs.tar.gz
        
        proxy_env:
          http_proxy: http://sys_sde_apps:Sw%40nLake9@proxy.auiag.corp:8080
          https_proxy: http://sys_sde_apps:Sw%40nLake9@proxy.auiag.corp:8080
          
Connect to the Linux instance (the code will modify your ~/.ssh/config):
     
     ssh dn_postgresql
     
Connect to the postgresql database:

     sudo -u postgres -i psql
     
     
## OSP




- name: adding http_proxy_url to yum.conf if defined
  lineinfile:
    dest: /etc/yum.conf
    regexp: "^proxy="
    line:  "proxy={{ http_proxy_url }}"
    state: present
  become: true
  when:
    - http_proxy_url is defined
    - local_yum_repo == 'no'