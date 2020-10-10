# NextMedia-coding-challenge
This repo has been made in order to participate to the coding challenge by NextMedia for DevOps Engineer application

## Infrastructure Preparing 6 instances (3 Dev instances - 3 test instances) 

1- First of all clone the repo using 
```
Git clone https://github.com/goulahyane/NextMedia-coding-challenge 
```

2- Go throw the repo and check if everything required is installed
```
cd NextMedia-coding-challenge && docker-compose version
```

3- Make a docker-compose alias for the sake of simplicity
```
echo "alias dc='docker-compose'">> ~/.bashrc #(or ~/.zshrc in case u are using MacOs) \
&& 
source ~/.bashrc  
```

4- Build the docker images
```
dc build . # you should be in the right repo in order to make this work
```

5- Run build images and check if everything is up and running  
```
dc up -d && dc ps 
```

6- Connect to the Ansible Master instance
```
dc exec master bash
```

## Installing ELK and Web server using ansible-playbook

1- On the ansible Master instance navigate to:
```
cd /etc/ansible/ && ansible-playbook install.yml
```

I suppose the communication check has been done using:
```
ansible all -m ping 
```

Waiting for the installation to be done, and check the installation once done, using:
```
curl node1:9200 && curl node3
```
You can also check on your local brower by groing to:
```
http://localhost:5601 (Kibana)

http://localhost (Nginx)
```

## Test Environnement 

In the ansible Master insntance, under the ``` /etc/ansible/ ``` a plybook called ``` install_2.yml ``` for ELK cluster installation



1- Connect to the ansible Master instance 
```
dc exec master bash
```

2- Run the playbook
```
ansible-playbook /etc/config/install_2.yml
```

Or
```
cd /etc/ansible/ && ansible-playbook install_2.yml
```
Once the installation is done, you can check the cluster health using the following command line on ansible instance:

``` 
curl node6:9200/_cluster/health?pretty
```
Or in your browser by viewing the Kibana Interface
```
Http://localhost:6500
```
