# Linux Server Configuration

Deploy Catalog App from Project 6 to Linux Server

## Step 1
Set up Ubuntu 16.04 LTS instance on Amazon Lightsail.

## Step 2
* Once you have your server running, log into it using either the built-in application or your terminal emulator of choice.
    * To use your own terminal:
        * Download your default ssh key to your local machine
        * Place it in your `.ssh` directory
        * Use `ssh {user}@{server ip here} -i {your key location here}` to login
* Once you successfully login to your server, make sure that everything is up-to-date:
    * run `sudo apt update`, then `sudo apt upgrade`
        * NOTE: If prompted to update GRUB settings, go ahead and keep the suggested defaults


