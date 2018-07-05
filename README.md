# ubuntu-router

##What: 
1. An Ansible meta-automation solution for automatically creating a home ubuntu server router.

##When:
1. Last Updated: 2018-07-03
2. First Started: 2018-07-02

##Why:
1. Ubuntu router will be flexible and secure. 

##Who: 
1. Developed for anyone who wants to have a home router solution solution.

##How:
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


Tips:
1. Check for DHCP leases here: nano /var/lib/dhcp/dhcpd.leases
2. Restart DHCP service with: sudo /etc/init.d/isc-dhcp-server restart
3. Enable DHCP on interfaces with: ifdown enp1s0; ifup enp1s0