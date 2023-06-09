# Overview
Setup Fedora Workstation post installation for home use. 
- Why?
  - I've wanted to learn ansible for some time and this was a good learning opportunity.
  - Just so much easier to reinstall and get going again!
- Sharing for educational purposes after reviewing some other similar repos on GitHub which were helpful in the learning process. Hope it helps someone get started.
- **Use at your own risk!**
  
## Requirements
- Fresh installation of Fedora Workstation.
  - Tested with Fedora 38 and Gnome 44.
- Ansible
- Git

```shell
sudo dnf install ansible git -y
git clone git@github.com:steve-rackham/ansible-workstation.git
```

## Usage
First:
- Update any var files and global vars as required.
- From within the ansible-workstation directory:

Then run one of the following examples: 

```shell
# Example: Run all roles and tasks on localhost:
ansible-playbook --inventory localhost site.yml -K

# Example: Run only themes tag
ansible-playbook --inventory localhost site.yml -K --tags theme

# Example: Run every but the themes tag
ansible-playbook --inventory localhost site.yml -K --skip-tags theme

```

Check out blog post for further details: https://siliconwolf.net/setup-fedora-workstation-ansible/
