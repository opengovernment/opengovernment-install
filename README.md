This repository contains OpenGovernment install scripts for various platforms.
Right now we only support an Ubuntu 10.10 install.

To use the scripts:

Edit the file run_as_root. You will have to replace the defaults there with your own valuers.

And then, as root (imagine that), from the script's directory, run it.

Once it's done, you will need to make the config/database.yml and config/api_keys.yml files. There are sample files in config/ to get you going.

Then you should be ready to install data and get going.

Thanks to Jeff Roush for putting together the Ubuntu install scripts.

