# Server configuration

This is an Ansible playbook which provisions an Ubuntu 18.04 server with a
hardened configuration intended for being exposed to the internet.

## Requirements

- Ubuntu 18.04 server

## Usage

One privileged user account with configurable username (`user_username`) will be
created. It has passwordless sudo access and requires an SSH key for connecting.
All password logins are disabled and a firewall is setup which allows incoming
traffic only to port 22.

- Copy `hosts.template` as `hosts` and fill the correct IP address of the
  server
- Copy `group_vars/vars.template` as `group_vars/vars` and fill the values
- For the first run, change `remote_user` to `root` in `playbook.yml`. Afterwards
  revert back to `{{ user_username }}`
- Install Ansible on some computer. Execute 
  `ansible-playbook -i hosts -v playbook.yml --ask-pass`. On subsequent runs drop
  the `--ask-pass` and make sure ssh-agent is set up correctly for key
  authentication.

