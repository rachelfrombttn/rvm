# Signing RVM releases

## Preconditions

### Creating new developer key

You must have a valid GPG key. You might follow this tutorial if you want to [create perfectly safe key pair](https://alexcabal.com/creating-the-perfect-gpg-keypair/) with a signing subkey.

After creating or changing your GPG key you need to reference it in few places:
 
1. Add your key signature in RVM source code:
 
    * `binscripts/rvm-installer` in function `verify_package_pgp`
    * `scripts/functions/cli` in function `verify_package_pgp`

2. Export your public key to the root of [rvm-site](https://github.com/rvm/rvm-site)


    gpg --armor --export NAME > NAME.asc

3. Add your key signature in following sections of the documentation

    * [Index](https://github.com/rvm/rvm-site/blob/master/content/index.haml)
    * [Install](https://github.com/rvm/rvm-site/blob/master/content/rvm/install.md)
    * [Security](https://github.com/rvm/rvm-site/blob/master/content/rvm/security.md)
    * [Vagrant](https://github.com/rvm/rvm-site/blob/master/content/integration/vagrant.md)

### Expiration date

It is a good practice to set an expiration date on your GPG key. Before signing release, make sure your key has not expired. If it did, you might want to follow this tutorial to [extending key expiration date](https://www.g-loaded.eu/2010/11/01/change-expiration-date-gpg-key/)

## Signing installer

Whenever you make a change to `binscripts/rvm-installer`, you should also update the installer signature and include it in your pull request:

    rm binscripts/rvm-installer.asc && gpg --armor --detach-sig binscripts/rvm-installer
        
To add second (yours) signature to already correctly signed installer:

    mv binscripts/rvm-installer.asc binscripts/rvm-installer.asc.org
    gpg --armor --sign-detach binscripts/rvm-installer
    cat binscripts/rvm-installer.asc.org >> binscripts/rvm-installer.asc
    rm binscripts/rvm-installer.asc.org

## Signing release

To sign the release follow on screen instructions:

    bash sign-releases.sh
