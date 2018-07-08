# ubuntu-router

## What: 
1. An Ansible meta-automation solution for automatically creating a home ubuntu server router.

## When:
1. Last Updated: 2018-07-03
2. First Started: 2018-07-02

## Why:
1. Ubuntu router will be flexible and secure. 

## Who: 
1. Developed for anyone who wants to have a home router solution solution.

## How:
1. Install linux subsystem Windows 10
    - a. Control Panel -> Programs -> Turn Windows Features on or off -> Windows Subsystem for Linux
    - b. Go to microsoft store, seach Linux, and install Ubuntu
2. Install ansible
    - a. Go to command prompt, type bash
    - b. sudo -s
    - c. apt-get install software-properties-common
    - d. sudo apt-add-repository ppa:ansible/ansible
    - e. sudo apt-get update
    - f. sudo apt-get install ansible
3. Set up SSH keys
    - a. On local host (machine you will use to ssh into the router) open bash in the command prompt and run these commands
    - b. sudo -i
    - c. ssh-keygen
    - d. ssh-copy-id user@XXX.XXX.XXX.XXX (replace user with router username & replace XXX.XXX.XXX.XXX with your router's IP address)
3. Edit the "hosts" file in the /etc/ansible directory
    - a. add a line at the top of the following
        - i. [router]
        - ii. XXX.XXX.XXX.XXX ansible_user=user (replace user with router username & replace - XXX.XXX.XXX.XXX with your router's IP address)
4. Manually install python2.7 on the ubuntu server router: sudo apt-get install python
5. Run the ansible script with: ansible-playbook main.yml --ask-become-pass


## Tips:
1. Check for DHCP leases here: nano /var/lib/dhcp/dhcpd.leases
2. Restart DHCP service with: sudo /etc/init.d/isc-dhcp-server restart
3. Restart iptables: sudo systemctl restart netfilter-persistent
4. Enable iptables: sudo systemctl restart netfilter-persistent
5. Update iptables:sudo /etc/network/if-pre-up.d/iptables
6. Restart DNS: sudo systemctl restart bind9
7. Restart Networking: sudo systemctl restart networking.service
8. Check Service Status (+ means service running, - means not running): sudo service --status-all 
9. Note: if interfaces won't start, it typically means /etc/iptables/rules.v4 has an error
10. Note: /etc/iptables/rules.v4 is whitepsace sensitive. Each COMMIT lines must have not spaces before or after the work COMMIT and a blank line (with no spaces) above and below it. Also make sure that no line has extra whitepsace anywhere.
11. Attempt to raise or lower interfaces: ifdown enp1s0, ifup enp1s0
