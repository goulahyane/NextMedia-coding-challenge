# NextMedia-coding-challenge
This repo has been made in order to participate to the coding challenge by NextMedia for DevOps Engineer application

## Infrastructure Preparing

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



