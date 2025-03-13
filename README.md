# ns8-openvpn

[OpenVPN Access Server](https://openvpn.net/access-server) is a secure remote access solution to your private network, in the cloud or on-prem.

## Install

Install via Software center:

  - Add a Software repository pointing to `https://repo.mrmarkuz.com/ns8/updates/`, check out the [repo webpage](https://repo.mrmarkuz.com) how to do it.
  - Install OpenVPN Access server via Software Center

To install latest version on CLI:

    add-module ghcr.io/nethserver/openvpn:latest 1

## Configure

Set the FQDN to access the OpenVPN Access Server.

To set the password SECRET for user openvpn in app instance openvpn1:

    runagent -m openvpn1 podman exec openvpn-app sacli --new_pass=SECRET -u openvpn SetLocalPassword

Just for info: The initial password for the openvpn user of instance openvpn1 can be found in the logs:

    journalctl _UID=$(id -u openvpn1) --grep "Auto-generated pass = " | cut -d '"' -f 2

Browse to the FQDN and login as user openvpn with the password you set in the previous step.

### Admin interface

Browse to https://openvpn.domain.tld/admin

Here you can create users.

### User interface

Browse to https://openvpn.domain.tld and login

Here you can download/import the VPN configuration to a client device.

### TODO

- LDAP