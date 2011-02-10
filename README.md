This repository contains OpenGovernment install scripts for various platforms.
Right now we only support an Ubuntu 10.10 install.

To use the scripts:

1. Start with a copy of Ubuntu 10.10. The scripts were tested on clean installs of [Ubuntu server](http://www.ubuntu.com/server/get-ubuntu/download) in a virtual machine using [VirtualBox](http://www.virtualbox.org/). VirtualBox is free, works great, and runs under Windows, OS X, and Linux. [VMWare](http://www.vmware.com/) would work fine, too, if you prefer that.

2. The scripts do have one prerequisite: git. And if you want to download a read-write copy of your own fork of opengovernment, you will need to [exchange ssh keys](http://help.github.com/linux-key-setup/) between github and your new Ubuntu machine before you run the script.

3. So the procedure, briefly, is this:

    sudo apt-get install git

    # (If you want to get a read-write repository: ssh-keygen, then exchange ssh keys with git)

    git clone git@github.com:opengovernment/opengovernment-install.git
    cd opengovernment-install
    sudo ./install_on_ubuntu_1010 your_ubuntu_username [your_opengovernment_fork_github_url] [password_for_new_psql_account]


The script has these options:
* Your username. 
* [Optional] The url to your opengovernment repository, if you have your own fork. This defaults to a read-only copy of the main repository.
* [Optional] A password for the new postgresql user. This defaults to 'foobar'. Pretty secure, huh? You might want to provide your own.

Once the script is done, you will need to make the config/database.yml and config/api_keys.yml files. There are sample files in config/ to get you going.

Then you should be ready to install data and get going.

Thanks to Jeff Roush for putting together the Ubuntu install scripts.

