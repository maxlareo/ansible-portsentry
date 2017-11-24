PortSentry
=========

[![Build Status](https://travis-ci.org/maxlareo/ansible-portsentry.svg?branch=master)](https://travis-ci.org/maxlareo/ansible-portsentry) [![Ansible Galaxy](http://img.shields.io/badge/ansible--galaxy-portsentry-blue.svg)](https://galaxy.ansible.com/maxlareo/portsentry/)

Install and configure PortSentry in Debian-like systems

Requirements
------------

None

Role Variables
--------------

### About the `/etc/portsentry/portsentry.conf` file

- `portsentry_tcp_ports`: [default: `1,11,15,79,111,119,143,540,635,1080,1524,2000,5742,6667,12345,12346,20034,27665,31337,32771,32772,32773,32774,40421,49724,54320`]: TCP port configs for classic and basic Stealth modes
- `portsentry_udp_ports`: [default: `1,7,9,69,161,162,513,635,640,641,700,37444,34555,31335,32770,32771,32772,32773,32774,31337,54321`]: UDP port configs for classic and basic Stealth modes
- `portsentry_advanced_exclude_tcp`: [default: `113,139`]: TCP ports to ignore, PortSentry will simply not respond to incoming requests, in effect PortSentry treats them as if they are actual bound daemons
- `portsentry_advanced_exclude_udp`: [default: `520,138,137,67`]: UDP ports to ignore, PortSentry will simply not respond to incoming requests, in effect PortSentry treats them as if they are actual bound daemons
- `portsentry_ignore_file`: [default: `/etc/portsentry/portsentry.ignore`]: Hosts to ignore
- `portsentry_history_file`: [default: `/var/lib/portsentry/portsentry.history`]: Hosts that have been denied (running history)
- `portsentry_blocked_file`: [default: `/var/lib/portsentry/portsentry.blocked`]: Hosts that have been denied this session only (temporary until next restart)
- `portsentry_RESOLVE_HOST`: [default: `0`]: DNS Name resolution, `1` will turn on DNS lookups, `0` (or any other value) will shut it off
- `portsentry_block_udp`: [default: `0`]: Enable automatic response options for UDP/TCP (you want to block UDP, but not TCP), `0` Do not block UDP/TCP scans, `1` Block UDP/TCP scans, `2` Run external command only
- `portsentry_block_tcp`: [default: `0`]: Enable automatic response options for UDP/TCP (you want to block TCP, but not UDP), `0` Do not block UDP/TCP scans, `1` Block UDP/TCP scans, `2` Run external command only
- `portsentry_kill_route`: [default: `/sbin/iptables -I INPUT -s $TARGET$ -j DROP`]: This command is used to drop the route or add the host into a local filter table
- `portsentry_scan_trigger`: [default: `0`]: Enter in the number of port connects you will allow before an alarm is given, the default is 0 which will react immediately

### About the <è /etc/portsentry/portsentry.ignore.static` file

- `portsentry_ignore_static`: [default: `[]`]: Put hosts in here you never want blocked (format: <ip>/<netmask>), if you don't supply a netmask it is assumed to be 32 bits

Dependencies
------------

None

Example Playbook
----------------

```yaml
- hosts: servers
  roles:
    - portsentry
```

License
-------

MIT

Author Information
------------------

[Maxime Lareo](https://github.com/maxlareo)

Feedback, bug-reports, requests, ...
------------------------------------

Are [welcome](https://github.com/maxlareo/ansible-rkhunter/issues)!
