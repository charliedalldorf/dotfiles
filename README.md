# Arch Linux - Sway Window Manager Configuration

#### Sway + Waybar + Termite

![alt tag](https://github.com/charliedalldorf/dotfiles/blob/master/screenshots/ss1.png)

#### Rofi Launcher

![alt tag](https://github.com/charliedalldorf/dotfiles/blob/master/screenshots/ss2.png)

### Purpose

* Portable: Can replicate current Workstation configuration to other setups.
* Flexible: Easy to create new roles and tasks.
* Consistent: Current dotfiles always kept up to date.
* Controlled: Files are Merged and Copied using Ansible.

### How To:

#### 1. Clone Repository

```
git clone https://github.com/charliedalldorf/dotfiles
```

-----

#### 2. Configure Ansible Hosts Inventory

Create Inventory from hosts template.

```
cd dotfiles
cp hosts \etc\ansible\hosts
```

Add Hosts to \etc\ansible\hosts

Example:
```
[workstation]
arch@192.168.1.3

[remote]
manjaro@192.168.1.9
```

-----

#### 3. Configure SSH

Copy SSH Key to all hosts.

```
ssh-copy-id manjaro@192.168.1.9
```

-----

#### 4. Test Hosts Inventory

```
ansible -m ping all
```

Should see **SUCCESS** for all hosts.

-----

#### 4.a (Optional) Run install.yml

Run **install.yml** if you have a fresh Arch Linux install or to make sure you have all the packages.

```
ansible-playbook install.yml -kK
```

-----

#### 5. Run setup.yml

```
ansible-playbook setup.yml -kK
```

#### Optional

If changes are made to existing configuration files, run **sync.yml** to sync config files to Repository.

```
ansible-laybook sync.yml
```