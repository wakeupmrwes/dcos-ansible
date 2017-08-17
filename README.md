# Documentation for dcos-ansible

This repo contains Ansible playbooks that can be used to deploy a DC/OS cluster
running the community version of DC/OS.

## Dependencies

* Ansible needs to be installed on the system that will drive the deployment
  process.

  On Mac OS:

  ```
  brew install ansible
  ```

  On Red Hat Enterprise Linux:

  ```
  sudo yum -y install epel-release
  sudo yum -y install ansible
  ```

  On Windows:

  lol.

  Other platforms:

  Refer to the install guide found at
  http://docs.ansible.com/ansible/latest/intro_installation.html

## Usage

Clone this repository:

```
git clone https://pumphouse_p@bitbucket.org/pumphouse_p/dcos-ansible.git
cd dcos-ansible
```

Modify the `hosts` file and update it with the IP addresses for the systems you
have and want to use for DC/OS. Ensure you place your `bootstrap`, `masters`,
`public-agents` and `private-agents` in the appropriate group in the `hosts`
file.

If you have not already made an ssh connection to your remote systems, you will
want to disable Ansible host key checking. This can be done in one of the
following ways:

```
export ANSIBLE_HOST_KEY_CHECKING=False
```

Or by creating/modifying `~/.ansible.cfg` with the following option:

```
[defaults]
host_key_checking=False
```

When ready to start installing DC/OS, run the following command:

```
ansible-playbook -i hosts --private-key <path_to_ssh_key> main.yaml
```
