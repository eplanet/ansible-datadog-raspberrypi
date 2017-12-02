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
- `datadog_api_key`: You Datadog API key, found [here](https://app.datadoghq.com/account/settings#api). No default value!
- `datadog_agent_home`: The directory to install the agent to. Default: /opt/datadog-agent
- `datadog_log_file`: Override the logging file path. Default: /var/log/datadog-agent.log
- `datadog_hostname` (optional): Override the hostname reported to Datadog

# License
[Apache 2.0](LICENSE)
