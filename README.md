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

<br>

# Structure
Sections have been broken down into roles with the site.yml file referencing each role in appropriate sequence:
- System
  - Hostname.
- User
  - Create directory structure.
  - Add git profile.
  - Add SSH keys.
  - #TODO: Change home directory.
  - #TODO: Add avatar.
- App-packages
  - Add RPM repos.
  - Add third party repos.
  - Add flatpak repo.
  - Install:
    - Drivers.
    - Gnome packages.
    - Codecs.
    - User packages.
    - User flatpaks.
  - Remove:
    - Unwanted packages.
- App-config
  - Configure user applications.
    - #TODO: vscodium extensions.
- Desktop-customisation
  - Install
    - #TODO: Add variables for theming elements. Hard-coded to use Graphite-GTK-Theme, and associated cursors and icons: https://github.com/vinceliuice/Graphite-gtk-theme
    - Theme.
    - Icons.
    - Cursors.
    - Wallpaper.
  - Apply 
    - #FIXME: This does not seem to apply with gsettings command despite reboot. Using gnome-tweaks manually for now.
    - Theme
    - Icons.
    - Cursors.
    - Wallpaper.

# Usage
The playbook requires elevation for the bulk of the installs. It is assumed that the user has sudo elevation.

## Examples
### Example: Run every role and task:
1. Update any var files and global vars as required.
2. From within the ansible-workstation directory:

```shell
ansible-playbook --inventory localhost site.yml -ask-become-pass
```
### Example: Run only themes tag
1. Update any var files and global vars as required.
2. From within the ansible-workstation directory:

```shell
ansible-playbook --inventory localhost site.yml -ask-become-pass -tags theme
```

### Example: Run every but the themes tag
1. Update any var files and global vars as required.
2. From within the ansible-workstation directory:

```shell
ansible-playbook --inventory localhost site.yml -ask-become-pass --skip-tags theme
```
<br>

## Tags
### Available Tags:
Show available tags:

```shell
ansible-playbook --inventory localhost site.yml --list-tags
```
```shell
playbook: site.yml

  play #1 (localhost): Fedora Workstation Configuration	TAGS: []
      TASK TAGS: [app-config, apps, cleanup, codecs, cursors, customisation, debug, devops, dnf, drivers, flatpaks, git, gnome, icons, remove, ssh, system, theme, wallpaper]
```

### Tags and Reference
#TODO: Add table and description for each tag.
- app-config
- apps
- cleanup
- codecs
- cursors
- customisation
- debug
- devops
- dnf
- drivers
- flatpaks
- git
- gnome
- icons
- remove
- ssh
- system
- theme
- wallpaper