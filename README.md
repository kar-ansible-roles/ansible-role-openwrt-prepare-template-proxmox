Prepare openwrt template on proxmox
=========
[![Proxmox VE](https://img.shields.io/badge/Proxmox%20VE-9-brightgreen?logo=proxmox&logoColor=white)](https://proxmox.com/en/)

The role is intended for creating a template for an openwrt virtual machine on proxmox virtualization manager, for further cloning. During creation, execution stops at some point, at which point it is necessary to follow the steps described in the terminal and resume execution. After completing the role, a template for an OpenWRT VM with open ports 22, 80, and 443 will appear on your proxmox.

Requirements
------------

Access to internet, Proxmox VE 9, community.proxmox==1.6.0.

Role Variables
--------------

| Variable | Default | Description |
|----------|---------|-------------|
| `openwrt_version` | `24.10.5` | Version of OpenWrt |
| `openwrt_template_id` | `100` | OpenWrt VM template id |
| `openwrt_wan_mac` | `01:23:45:67:89:01` | MAC address of OpenWrt WAN interface |
| `pm_host` | `"{{ ansible_host }}"` | Proxmox ip adress |
| `pm_node` | `pve` | Proxmox node name |
| `pm_user` | `root@pam` | Proxmox user |
| `pm_password` | `MyStrongPassword` | Peoxmox password |
| `pm_phis_adapter` | `nic0` | Phisical adapter? which Proxmox connect to internet |
| `pm_internal_cidr` | `10.10.0.2/24` | IP address of Proxmox host in OpenWrt LAN network |

| `pm_external_cidr` | `192.168.1.2/24` | IP address of Proxmox host in external office network |
| `planned_wireguard` | `true` | If you plan install Wireguard on OpenWrt |
| `wg_network` | `10.10.10.0/24` | Wireguard natework settings |
| `openwrt_gateway_cidr` | `10.10.0.1` | IP address of OpenWrt in OpenWrt LAN network |

Dependencies
------------

None

Example Playbook
----------------

```yaml
  roles:
    - role: ansible-role-openwrt-prepare-template-proxmox
      vars: 
        - openwrt_version: 24.10.5
```

License
-------

MIT License

Author Information
------------------

This role was created in 2026 by [Karen Saakov](https://linkedin.com/in/karen-saakov-4905571a1) DevOps Engineer Karo LLC.
