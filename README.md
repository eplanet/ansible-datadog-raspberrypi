datadog-ansible-raspberrypi
===========================

[![Build Status](https://travis-ci.org/eplanet/ansible-datadog-raspberrypi.svg?branch=master)](https://travis-ci.org/eplanet/ansible-datadog-raspberrypi)

The installation of Datadog agent on a Raspberry Pi is possible and well explained in that [post](https://help.datadoghq.com/hc/en-us/articles/208163513-Deploying-the-Agent-on-RaspberryPI). However this might be a bit too manual and time consuming, which is why I decided to create that Ansible role to facilitate tedious work.

Installation process follow this order:
- Install dependencies `libpython2.7-dev` and `sysstat`
- Verify agent is installed and if not proceed to installation
- Setup startup command in /etc/rc.local
- Launch Datadog agent

# Variables
- `datadog_api_key`: Your Datadog API key, found [here](https://app.datadoghq.com/account/settings#api). No default value!
- `datadog_agent_home`: The directory to install the agent to. Default: /opt/datadog-agent
- `datadog_log_file`: Override the logging file path. Default: /var/log/datadog-agent.log
- `datadog_skip_integrations`: Tell installation script to skip integrations installation, values: 1 to skip, 0 to install. Default: 1
- `datadog_hostname` (optional): Override the hostname reported to Datadog

# Example playbook
## Minimal
```yaml
- hosts: servers
  roles:
    - { role: ansible-datadog-raspberrypi, become: yes, datadog_api_key: "123456" }
```

## Overriding variables
```yaml
---
- hosts: servers
  roles:
    - { role: ansible-datadog-raspberrypi, become: yes }
  vars:
    datadog_api_key: "123456"
    datadog_agent_home: "/home/pi/datadog-agent"
    datadog_skip_integrations: 1
    datadog_log_file: "/home/pi/datadog-agent/logs"
    datadog_hostname: "myraspberrypi"
```

# License
[Apache 2.0](LICENSE)

# Contributing
Contributions very welcome! If you notice any issue or room for improvement, do not hesitate to open an issue or submit a pull request.
