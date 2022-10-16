# Ansible Playbook for Initial Server Setup

This [Ansible](https://www.ansible.com/) playbook is intended to be used on all new servers on my local and cloud networks, whether they be a physical box, VM, or VPS.

## Features

- Basic security and SSH configuration
- SNMP and RSyslog configuration for use with [LibreNMS](https://www.librenms.org/)
- [Tailscale](https://tailscale.com/) enrollment

## Goals

- Automate initial server configuration for my homelab and cloud environments
- Ensure that basic security practices are in place accross all servers
- Use consistent SNMP configurations accross all devices while taking advtange of device-specific SNMP plug-ins (Pi-Hole, ZFS, etc.)

## Requirements

- Up-to-date Ansible install
- Red Hat or Debian based operating systems on your hosts
- Working LibreNMS install with network access
- Tailscale account and a valid enrollment key

## Instructions

While the playbook can target single devices, it was designed to run repeatedly on multiple servers to ensure compliance with the stated goals. If you're not me, you'll probably want to tweak the playbook to your liking, but the below steps should get you going.

1. Clone the repository
2. Add your hosts to the `hosts` file in the repo (or use your own inventory)
3. Edit the `group_vars/all` file with your own data. If something doesn't apply to your environment, you can leave it blank.
4. Add your SSH keys to `roles/common/files/keys-default`. These will be added to the `authorized_keys` file of each host you target.
5. Run the playbook
   ```
   cd ansible-server-setup
   ansible-playbook site.yml -K -i hosts
   ```

## Questions / Feedback

Feel free to open a Github issue or reach out to me on Element -  @skoobasteeve:linuxdelta.com.