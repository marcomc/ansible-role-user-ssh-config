[![Build Status](https://travis-ci.com/marcomc/ansible-role-user-ssh-config.svg?branch=master)](https://travis-ci.com/marcomc/ansible-role-user-ssh-config)

# User's ssh_config

This ansible role setup an '$HOME/.ssh/config' file for the targeted user defining the preferred default values for all ssh connections.

It also gives the opportunity to define a ssh proxy server to use for all ssh connections.

This is a role for any unix-like system.

Used in [Splinter, an opinionated provisioning tool for macOS](https://github.com/marcomc/splinter).

## Example Playbook

    - vars:
        target_user_id: "new_dev_account"
        target_user_home_dir: '/home'
        ssh_proxy_enabled: yes
        ssh_proxy_name: 'my.fancy-ssh-proxy.com'
        ssh_proxy_aliases: ['fancy-proxy','mysshproxy','fancy-ssh-proxy.com']
        ssh_proxy_port: 2222

    - hosts: localhost
      roles:
      - marcomc.user_ssh_config

## Variables

    verbose: no
    target_user_id: "{{ ansible_user_id }}" # mandatory - by default is the user running ansible
    target_user_home_dir: ''                # optional - in case the target user home is in an unconventional path
    ssh_proxy_enabled: no                   # optional - toggle the declaration of a SSH Proxy in the .ssh/config file
    ssh_proxy_name: ''                      # optional - dns name or IP of your SSH proxy if you have one
    ssh_proxy_aliases: []                   # optional - aliases or short names you might need to call your SSH proxy with
    ssh_proxy_port: 22                      # optional - port you connect to your SSH proxy server (default is '22')


License
-------

[MIT](LICENSE)

Author : Marco Massari Calderone (c) 2020 - marco@marcomc.com
