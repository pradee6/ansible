# Ansible Installation

Ansible is an open-source automation platform. It is very, very simple to set up and yet powerful. Ansible can help you with configuration management, application deployment, task automation.

### Pre-requisites

1. An AWS EC2 instance (on Control node)

### Installation steps:
#### on Amazon EC2 instance

1. Install python and python-pip
   ```sh
   yum install python
   yum install python-pip
   ```
1. Install ansible using pip check for version
    ```sh
    pip install ansible
   ansible --version
   ```
   
1. Create a user called ansadmin (on Control node and Managed host)  
   ```sh
   useradd ansadmin
   passwd ansadmin
   ```
1. Below command grant sudo access to ansadmin user. But we strongly recommended using "visudo" command if you are aware vi or nano editor.  (on Control node and Managed host)
   ```sh
   echo "ansadmin ALL=(ALL) NOPASSWD: ALL" >> /etc/sudoers
   ```
   
1. Log in as a ansadmin user on master and generate ssh key (on Control node)
   ```sh 
   ssh-keygen
   ```
1. Copy keys onto all ansible managed hosts (on Control node)
   ```sh 
   ssh-copy-id ansadmin@<target-server>
   ```

1. Ansible server used to create images and store on docker registry. Hence install docker, start docker services and add ansadmin to the docker group. 
   ```sh
   yum install docker
   
   # start docker services 
   service docker start
   service docker start 
   
   # add user to docker group 
   usermod -aG docker ansadmin

   ```
1. Create a directory /etc/ansible and create an inventory file called "hosts" add control node and managed hosts IP addresses to it. 
 
### Validation test



---------------------------ansible all commands---------------------------------------------------------------------------------------------------
1. ansible
Description: Ad-hoc command that runs a single task on one or more hosts.
Example: ansible all -m ping
2. ansible-playbook
Description: Runs playbooks, which are YAML files defining a set of tasks to execute on remote hosts.
Example: ansible-playbook site.yml
3. ansible-inventory
Description: Manages and displays the inventory of hosts. You can list, graph, or dump inventory data.
Example: ansible-inventory --list
4. ansible-doc
Description: Displays documentation on Ansible modules, plugins, and roles.
Example: ansible-doc -s yum
5. ansible-galaxy
Description: Manages Ansible roles and collections from the Ansible Galaxy repository or other sources.
Example: ansible-galaxy install geerlingguy.mysql
6. ansible-vault
Description: Encrypts, decrypts, or rekeys sensitive data files, such as those containing passwords or other secrets.
Example: ansible-vault encrypt secrets.yml
7. ansible-pull
Description: Pulls playbooks from a Git repository and runs them locally, useful for self-provisioning nodes.
Example: ansible-pull -U https://github.com/your/repo.git
8. ansible-config
Description: Manages and displays Ansible configuration settings.
Example: ansible-config dump --only-changed
9. ansible-console
Description: An interactive command-line interface for Ansible, allowing you to run ad-hoc commands and interact with hosts in real-time.
Example: ansible-console
10. ansible-connection
Description: A lower-level command dealing with Ansible connection plugins. It is mostly used internally and rarely by end-users.
11. ansible-inventory-plugin
Description: Manages custom inventory plugins.
12. ansible-test
Description: Runs tests on Ansible or Ansible-related codebases. It’s mainly used for testing roles, modules, and plugins.
Example: ansible-test integration
13. ansible-validate
Description: Used to validate playbooks and tasks before running them. Ensures that the syntax and structure are correct.
Example: ansible-playbook --syntax-check site.yml
14. ansible-shell
Description: Deprecated in favor of ansible-console.
15. ansible-runner
Description: A tool for interfacing with Ansible directly from Python, mainly for advanced users who need to interact with Ansible programmatically.
Example: ansible-runner run
16. ansible-doc-compile
Description: Compiles documentation for Ansible modules and plugins. Useful for developers contributing to Ansible.
Example: ansible-doc-compile collection
17. ansible-role-init
Description: Creates a new role with the standard directory structure. It’s part of the ansible-galaxy command.
Example: ansible-galaxy role init my_role
18. ansible-podman
Description: Used with podman, a daemonless container engine. Provides integration with Podman-managed containers.
Example: ansible-podman
19. ansible-builder
Description: Builds container images for execution environments with Ansible dependencies.
Example: ansible-builder create
20. ansible-collection
Description: Manages Ansible collections, which are distributions of roles, modules, and plugins.
Example: ansible-collection install namespace.collection_name
21. ansible-test-network-integration
Description: Specific to testing Ansible network modules.
Example: ansible-test network-integration
22. ansible-lint
Description: A tool to lint (check) Ansible playbooks for practices that should be followed or avoided.
Example: ansible-lint playbook.yml
23. ansible-silo
Description: Runs Ansible in an isolated environment, often used in CI/CD pipelines or environments where Ansible dependencies are complex.
24. ansible-navigator
Description: A user interface for Ansible Automation Platform that helps navigate playbooks, inventories, and logs.
Example: ansible-navigator run site.yml
25. ansible-molecule
Description: Used for testing roles and playbooks in various environments, ensuring they work as expected.
Example: molecule test
   ```

   

