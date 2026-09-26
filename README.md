# Network and System Administration Test Assignment

This repository contains the configuration and documentation created as part of a system and network administration test assignment.

## Environment

- Hypervisor: Proxmox VE
- Virtual machine: Ubuntu Server
- Hostname: `ubuntu-test`
- Administration: SSH
- Version control: Git
- VPN: WireGuard

## Network Configuration

The virtual machine uses the following network configuration:

- Main interface: `ens18`
- Management IP: `192.168.243.135/24`
- Gateway: `192.168.243.2`
- VLAN 10: `192.168.10.1/24`
- VLAN 20: `192.168.20.1/24`

VLAN 10 and VLAN 20 are configured on the physical interface `ens18`
using IEEE 802.1Q VLAN tagging.

The Netplan configuration example is available in:

`configs/netplan.yaml`

Additional information about the network configuration is available in:

`docs/network-description.md`

## WireGuard VPN

WireGuard is configured to provide secure remote access to the Ubuntu server.

Server configuration:

- Interface: `wg0`
- Server VPN address: `10.10.10.1/24`
- Client VPN address: `10.10.10.2/32`
- UDP port: `51820`

The WireGuard service is managed using `wg-quick`.

For security reasons, the real WireGuard private key is not stored in this repository.
A sanitized configuration example is available in:

`configs/wg0.conf.example`

The VPN connection was verified using a WireGuard handshake, ICMP ping,
and SSH access to `10.10.10.1`.

## Virtualization

The Ubuntu Server virtual machine runs on Proxmox VE using KVM/QEMU virtualization.

Additional information is available in:

`docs/virtualization-description.md`

## Repository Structure

- `configs/` - network and VPN configuration examples
- `docs/` - documentation
- `screenshots/` - screenshots demonstrating the completed configuration
- `.gitignore` - prevents private keys and sensitive files from being committed

## Security

Private SSH and WireGuard keys are not stored in the repository.

Remote administration is performed over SSH.
A separate SSH key is used for authentication with GitHub.
