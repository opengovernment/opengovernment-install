This repository contains OpenGovernment install scripts for various platforms.
Right now we only support an Ubuntu 11.04 or 10.10 install.

To use the scripts:

1. Start with a copy of Ubuntu 11.04. The scripts were tested on clean installs of [Ubuntu server](http://www.ubuntu.com/server/get-ubuntu/download) in a virtual machine using [VirtualBox](http://www.virtualbox.org/). VirtualBox is free, works great, and runs under Windows, OS X, and Linux. [VMWare](http://www.vmware.com/) would work fine, too, if you prefer that.

2. The scripts do have one prerequisite: git. And if you want to download a read-write copy of your own fork of opengovernment, you will need to [exchange ssh keys](http://help.github.com/linux-key-setup/) between github and your new Ubuntu machine before you run the script.

3. So the procedure, briefly, is this:

        sudo apt-get install git
    
        (If you want to get a read-write repository: ssh-keygen, then exchange ssh keys with git)
    
        git clone git@github.com:opengovernment/opengovernment-install.git
        cd opengovernment-install
        sudo ./install_on_ubuntu_1104 your_ubuntu_username [your_opengovernment_fork_github_url] [password_for_new_psql_account]


The script has these options:

* Your username. 
* [Optional] The url to your opengovernment repository, if you have your own fork. This defaults to a read-only copy of the main repository.
* [Optional] A password for the new postgresql user. This defaults to 'foobar'. Pretty secure, huh? You might want to provide your own.

Once the script is done, you will need to make the config/database.yml and config/api_keys.yml files. There are sample files in config/ to get you going.

Then you should be ready to install data and get going.

## Note on developing in a virtual machine via ssh

Because of the way the site uses subdomains to specify states, you need to [browse the site as localhost](https://raw.github.com/gist/403002/7e1b16a04e5e66b5ece8922806e924715d482d6b/gistfile1.txt). 

But if you've installed the site in a virtual machine, you probably want to browse it with your desktop's web browser -- and Rails on the virtual machine will see your requests as coming in from the web, which won't work.

An easy way around this is to let ssh forward localhost:3000 to the virtual machine. Basically, on your desktop, you ssh to the virtual machine with these options:

     ssh -X -L 3000:localhost:3000 virtualmachinename

Then on the server use "rails s" to start the site in webrick. Then, on your desktop, point your browser to localhost:3000, and rails on the server will see the requests as coming in locally.