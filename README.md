# AnsibleIAC
### Types of Infrastructure:
- mutable or immutable (Mutable- changes and can be changed. Immutatble - can't be changed.
Largely mostly have used mutable environments, ssh in, run bash, restart servers and get it to the place that the machine needs to be.
Making something from scratch has its drawbacks as it might take longer but in the long run it's more efficient as you get more predictable results)
- on premisises and cloud

### What is IAC?
- 
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
- Automation engine
- Automates cloud provisioning, configuration management, app deployment and more.
- Uses YAML syntax (that why is simple)
- Requires Python on Linux hosts and PowerShell 3 on Windows hosts.
- Push Configuration Tool - Doesn't require an agent to be installed on the host. The server pushes the configuration to the nodes. (Chef and Puppet are opposite, they use the pull configuration)  


### ansible
- is simple becuase it uses Yaml
- agentless
- uses ssh to connect to any other server
- 
