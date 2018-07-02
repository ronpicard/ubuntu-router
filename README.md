# ubuntu-router

What: 
    An Ansible meta-automation solution for automatically creating a home ubuntu router.

When:
    Last Updated: 2018-07-02
    First Started: 2018-07-02

Why:
    Ubuntu router will be flexible and secure. 

Who: 
    Developed for anyone who wants to have a home router solution solution.

How:
    1. Install linux subsystem Windows 10
        a. Control Panel -> Programs -> Turn Windows Features on or off -> Windows Subsystem for Linux
        b. Go to microsoft store, seach Linux, and install Ubuntu
    2. Install ansible
        a. Go to command prompt, type bash
        b. sudo -s
        c. apt-get install software-properties-common
        d. sudo apt-add-repository ppa:ansible/ansible
        e. sudo apt-get update
        f. sudo apt-get install ansible
    3. Put the "hosts" file in the /etc/ansible directory
    4. Use the command ssh-keygen to create an ssh key
    5. Option 1: Run these commands sudo -i, cd ~/.ssh, sftp 
    user@XXX.XXX.XXX, put id_rsa.pub
    6. Option 2: Run this command: ssh-copy-id user@XXX.XXX.XXX
    7. Run the ansible script with: ansible-playbook main.yml
