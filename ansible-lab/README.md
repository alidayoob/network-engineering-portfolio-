# Ansible Basics on a Cisco Modeling Labs (CML) Lab

My first steps with Ansible for network devices: a small CML lab (one router, one switch) managed from an Ubuntu control node.

> Work in progress. I am learning Ansible step by step and adding to this repository as I go.

## Goal

Learn the Ansible fundamentals on Cisco devices:

- What an inventory is and how to group devices
- How `ansible.cfg` changes Ansible's default behaviour
- How to run ad-hoc commands against a device or a whole group

## Lab Setup

| Component | Details |
| --- | --- |
| Host | Windows laptop, VMware Workstation 17 |
| Network lab | Cisco Modeling Labs Free (CML-Free) running as a VM |
| Router | R1 (IOL), `192.168.11.11/24` |
| Switch | SW1 (IOL-L2), `192.168.11.12/24` |
| Control node | Ubuntu 24.04 VM with Ansible core 2.21 |
| Access to lab | CML External Connector (bridge) and an unmanaged switch, on the VMware NAT network `192.168.11.0/24` |

```text
Ubuntu (Ansible) --- VMware NAT --- External Connector --- Unmanaged Switch --+-- R1  (IOL)
                                                                              |
                                                                              +-- SW1 (IOL-L2)
```

Both devices have SSH enabled with a local user at privilege level 15.

## Files

```text
.
├── README.md
├── ansible.cfg    # project-level Ansible settings
└── hosts          # inventory (INI format)
```



| Setting | Meaning |
| --- | --- |
| `inventory` | Where the list of devices is, so `-i` is not needed on every command |
| `timeout` | Connection timeout in seconds (network devices can be slow) |
| `host_key_checking` | Skips the SSH host-key prompt. Lab use only |
| `forks` | How many devices Ansible works on in parallel |


```

- `[group]` defines a group. Calling a group in a command targets every device in it.
- `[group:children]` builds a group out of other groups.
- `[group:vars]` sets values (like the SSH user) for the whole group.

## Example Commands
```bash
ansible all --list-hosts                 # list all devices in the inventory
ansible routers --list-hosts             # only the router group
ansible-inventory --graph                # show the group tree
ansible routers -m raw -a 'show ip interface brief' -k    # ad-hoc command (-k asks for the SSH password)
```

##Result of adding the YAML inventory File:
```yaml
@all:
  |--@ungrouped:
  |--@cisco:
  |  |--@crouters:
  |  |  |--R1
  |  |--@cswitches:
  |  |  |--SW1
  |--@crouters:
  |  |--R1
  |--@cswitches:
  |  |--SW1
  |--@juniper:
  |  |--@jrouters:
  |  |  |--jR1
  |  |--@jswitches:
  |  |  |--jSW1
  |--@jrouters:
  |  |--jR1
  |--@jswitches:
  |  |--jSW1
```

## What I Learned

- An ad-hoc command has the shape `ansible <devices> -m <module> -a "<arguments>"`, and the order of the options is free.
- Ansible's `ping` module does not work on Cisco devices (they have no Python). `raw` works but always reports `CHANGED`.
- Ansible silently ignores unknown settings in `ansible.cfg`. A typo such as `folks` instead of `forks` does nothing, so check with `ansible-config dump --only-changed`.
- Linux paths are case-sensitive: a wrong folder name was enough to break the inventory.
- Start the External Connector and the unmanaged switch in CML before testing, otherwise the devices are unreachable.

## Next Steps

- Inventory in YAML format
- Cisco modules (`cisco.ios.ios_command`, `ios_facts`, `ios_config`)
- A playbook that backs up device configurations
- Jinja2 templates, roles, and Ansible Vault

## Notes

- No passwords, tokens, or vendor images (ISO, OVA, qcow2) are stored in this repository.
- The lab runs on Cisco Modeling Labs Free; the device images come with CML.

---

## Kurzfassung auf Deutsch

Dieses Repository dokumentiert meine ersten Schritte mit Ansible. In einem Cisco-Modeling-Labs-Lab (ein Router und ein Switch) habe ich ein Inventory mit Gruppen, eine `ansible.cfg` und erste Ad-hoc-Befehle ausprobiert. Zugangsdaten und Hersteller-Images sind nicht im Repository gespeichert. Das Projekt wird laufend erweitert.
