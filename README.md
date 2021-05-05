# AnsibleIAC
### Types of Infrastructure:
- mutable or immutable (Mutable- changes and can be changed. Immutatble - can't be changed.
Largely mostly have used mutable environments, ssh in, run bash, restart servers and get it to the place that the machine needs to be.
Making something from scratch has its drawbacks as it might take longer but in the long run it's more efficient as you get more predictable results)
- on premisises and cloud

### What is IAC?
- Infrastructure as Code is the process of provisioning and configuring an environment through code instead of manually setting up the required devices and systems. Once code parameters are defined, developers run scripts, and the IaC platform builds the cloud infrastructure automatically.

### Benefits:
 - speed and simplicity
 - configuration consistency
 - Minimasing of risk
 - Increased efficienty in software development
 - costa saving
 
 ### Best practices: 
 - codify everything
 - documents as little as possible
 - continously test, integrate and deploy


### To Parts of IaC:
- **Configuration Management**  - tools are resposible for provisioning and maintaining the state of your systems. Tools: (Checf, Puppet, Ansible)
- **Orchestration** - once we created the teplates for all parts of the system we need orchestration tools and scripts that talks to the cloud to pull them together into arhcitecture (CloudFormation(AWS), Ansible, Terraform)

### What is Ansible?
- Ansible is a software tool that provides automation for cross-platform computer support. It automates cloud provisioning, configuration management, application deployment, intra-service orchestration, and many other IT needs.

- Automation engine
- Automates cloud provisioning, configuration management, app deployment and more.
- Uses YAML syntax (that why is simple)
- Requires Python on Linux hosts and PowerShell 3 on Windows hosts.
- Push Configuration Tool - Doesn't require an agent to be installed on the host. The server pushes the configuration to the nodes. (Chef and Puppet are opposite, they use the pull configuration)  


### ansible
- is simple becuase it uses Yaml
- agentless
- uses ssh to connect to any other server
- works only on Linux and Mac (not on Windows)

- ![image](https://user-images.githubusercontent.com/47173937/117027612-c5797080-acf4-11eb-8b6e-7219fe02df4c.png)


### How to set up the ansible:
 - add Vagrantfile to directory and run it with `vagrant up` command
 - ( if it's not working for you comment the network ips for the first vagrant up, and then uncomment and restart vagrant)
 - `vagrant status`
 - `vagrant ssh controller`
 - add provision file `sudo nano provision.sh` 
 - `sudo apt-get update
sudo apt-get install software-properties-common
sudo apt-add-repository ppa:ansible/ansible
sudo apt-get update
sudo apt-get install ansible`
 - add `sudo chmod +x provision.sh`
 - to run provision file: `./provision.sh`
 - after running the provision file, check the ansible version `ansible --version`
 - check connections to different instances: `ping 192.168.33.10` the app, and `ping 192.168.33.11` to check the db
 - `sudo apt-get install tree` to install tree
 - next, go to `cd /ect/ansible`
 - use `tree` to see the tree structure
 - use `sudo nano hosts` command and add before ex.1: `[web]
192.168.33.10 ansible_connection=ssh ansible_ssh_user=vagrant ansible_ssh_pass=vagrant`
- to check if everything works `ansible -m web ping`

### Adhoc commands:
- used for looking for information, restarting instnaces
- benefits:

### Yaml:
- is a scripting(markdown) language
- yaml playbooks
- benefits: 

### Day 2 of Ansible - commands:
- to ping all instnaces from controller `ansible all -m ping` 
- to check the name of a different instance from controller `ansible web -a "uname -a"`
- to check date on specified instance `"ansible web -a "date"`
- to check free memory `ansible web -a "free -m"`
- check whats in specified instance `ansible web -m shell -a "ls -a"`
- add db info into hosts files, at the top the hosts file

- to check machines loading time `ansible all -m shell -a "uptime"`
- to check only on one machine `ansible db -m shell -a "uptime"`

- https://docs.ansible.com/ansible/latest/user_guide/intro_adhoc.html


- to update all available machines `ansible all -m shell -a "sudo apt-get update -y"`
- to update all machines `ansible all -m shell -a "sudo apt-get update -y"`

- command to upgrade `ansible all -m shell -a "sudo apt-get upgrade -y"`


- playbooks are written in YAML with .yaml/.yml extension with instractions
- each playbook has to start with three dashes ---
- `sudo nano install_nginx.yml`
- `ansible-playbook install_nginx.yml` 
- `sudo nano install_sql.yml`
- `ansible-playbook install_sql.yml`
- make sure to have the right indentation!
- `sudo nano install_nodejs.yml`
- `ansible-playbook install_mogodb.yml`
- to check the version of nodejs on web `ansible web -m shell -a "sudo nodejs --version"`
- to check the version of mongodb on db `ansible db -m shell -a "sudo mongod --version"`



