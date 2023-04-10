
# Mautic Ansible

This project help DevOps teams to configure Mautic installation on EC2 servers, it automates the process of creation with a single ansible playbook

# Limitations
- This project assume you are using AWS EC2 using Ubuntu 22.04.
- You need to provide `key.pem` which the deployment key for your server
- It installs Mautic using `git` so you will need to provide `git` repo 

## Installation

You need to have `Ansible` installed on your machine
You also need to add 

```bash
ansible-galaxy collection install community.general community.general.apache2_module

ansible-galaxy collection install community.mysql

```

## Usage/Examples
In order to use this playbook you need to do the following: 
- Make a copy of `vars.example.yaml`and provide details about your configuration, some vars are already configured for you
- In folder `roles/mautic/templates/home/ubuntu/.ssh` add your deployment key inside the file `github_deploy.pem.j2` this key will be used to do `git clone`
- In `hosts` file insert the IP/domain of your server

- Run the play book either by tags or as a whole

```bash
ansible-playbook -v playbook.yaml -i hosts 

ansible-playbook -v playbook.yaml -i hosts --tags="install_mautic"
```


### Available Tags
- init
- apache
- fpm 
- site 
- mautic
- install
- crons
- create_db
- create_user
- make_local
- install_mautic




## Contributing

Contributions are always welcome!

Please make a PR with the changes you wish to see

## Authors

- [@mabumusa1](https://www.github.com/mabumusa1)

