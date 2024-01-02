# Install ROS

Here are two options.

## Follow the standard ROS Installation for Indigo on ARM.


http://wiki.ros.org/indigo/Installation/UbuntuARM


## Or try out the puppet module: 

    # install ruby to get gem
    sudo apt-get install -y ruby ruby1.9.1-dev make
    # install a recent version of puppet (save a lot time not generating the docs)
    sudo gem install puppet --no-rdoc --no-ri
    # install the ros puppet module
    sudo puppet module install tfoote-ros
    # execute the puppet module
    sudo puppet apply -e "include ros"
    
