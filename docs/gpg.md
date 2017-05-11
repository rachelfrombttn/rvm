## README

At RVM we use GPG to sign files/releases - for security.

#### Note: gpg vs. gpg2

Both should be fine, sometimes `gpg` has problems downloading keys from 
server, it might be better to work with `gpg2` if it's available for 
your's system.

## For users

Make sure to only trust the keys of people you trust - if you trust to 
run our code - trust our keys.

1. import keys:

        gpg2 --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3 # mpapis@gmail.com


2. refresh keys:

    This step helps to ensure none of the developer keys got revoked,
    it's best to do it periodically - or just add it to cron.

        gpg2 --refresh-keys


3. trust developers:

        echo 409B6B1796C275462A1703113804BB82D39DC0E3:6: | gpg2 --import-ownertrust # mpapis@gmail.com


4. verified installation:

        \curl -sSL https://raw.githubusercontent.com/rvm/rvm/master/binscripts/rvm-installer     -o rvm-installer &&
        \curl -sSL https://raw.githubusercontent.com/rvm/rvm/master/binscripts/rvm-installer.asc -o rvm-installer.asc &&
        \gpg2 --verify rvm-installer.asc &&
        \bash rvm-installer


5. RVM automates GPG for updates to ensure security, no manual steps are needed after installation.
