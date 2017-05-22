# Secure RVM installation

At RVM we use GPG to sign files and releases. Whenever you upgrade RVM, we automatically check if packages downloaded from the internet are authentic. This way we keep you secure from unauthorized modifications.

#### Note: gpg vs. gpg2

Both versions should be fine, however we noticed that sometimes `gpg` has problems downloading keys from 
server. Usage of `gpg2` is recommended, whenever it is available for your system.

## Import RVM keys
  
All you have to do to enable verified installations, is to import our developer's GPG keys:

        gpg2 --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3 # mpapis@gmail.com
        gpg2 --recv-keys 7D2BAF1CF37B13E2069D6956105BD0E739499BDB # piotr.kuczynski@gmail.com


3. trust developers:

        echo 409B6B1796C275462A1703113804BB82D39DC0E3:6: | gpg2 --import-ownertrust # mpapis@gmail.com
        
From now on, you installations will stay secure.

## Periodically refresh keys

To ensure that none of the keys has been revoked, it is a good practice to check them from time to time. You might want to run this as a regular cron job.

        gpg2 --refresh-keys

## Secure initial RVM installation

RVM will only verify upgrades and following installations once it is active in your system. If you want to secure the initial installation instead of using plain `curl`, run following command:

        \curl -sSL https://raw.githubusercontent.com/rvm/rvm/master/binscripts/rvm-installer -o rvm-installer &&
        \curl -sSL https://raw.githubusercontent.com/rvm/rvm/master/binscripts/rvm-installer.asc -o rvm-installer.asc &&
        \gpg2 --verify rvm-installer.asc &&
        \bash rvm-installer



