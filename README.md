# Ansible Arch Linux Role

This role is intended for automation of first-time setup and configuration file synchronization of an Arch Linux development environment. It should not be used for day-to-day maintenance/updates. **Don't run this if you don't have a backup, and don't use this as a replacement for regular manual updates.** Using this for regular updates violates [The Arch Way](https://wiki.archlinux.org/index.php/The_Arch_Way) and you're going to screw up your machine when manual intervention is required.

## Variables

* `archlinux_username` (string) - The username of the non-root user this role will create and configure
* `archlinux_user_real_name` (string) - The non-root user's real name (used for git configuration)
* `archlinux_user_email` (string) - The non-root user's email address (used for git configuration)

## Usage

Before running the playbook, perform a full upgrade and resolve any necessary manual interventions. Although I have tested the playbook and have found no destructive side effects, I cannot guarantee your system. Make sure your backups are current.

Install Ansible from the official repositories:

```bash
pacman -Syu ansible
```

Run the playbook:

```
ansible-playbook --ask-become-pass site.yml
```

Answer the prompts and watch it go.

You will have to set the non-root user's password and sudo privileges manually using `passwd` and `visudo`. Enabling sudo access for the `wheel` group should suffice, e.g. `%wheel ALL=(ALL) ALL`.

## Customization

You can select a colorscheme for the shell and Vim by typing on of the commands starting with `base16_`.

You can place an image file at "~/.wallpaper", and it will automatically be set as the desktop background at login. 

YouCompleteMe for Vim will be installed with the default completers. To enable the Clang and Go semantic completers, run `vim-plugin-update`.
