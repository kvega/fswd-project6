# Linux Server Configuration

Deploy Catalog App from Project 6 to Linux Server

## Step 1: Create your server
Set up Ubuntu 16.04 LTS instance on Amazon Lightsail.

## Step 2: Log into your server
* Once you have your server running, log into it using either the built-in application or your terminal emulator of choice.
    * To use your own terminal:
        * Download your default ssh key to your local machine
        * Place it in your `.ssh` directory
        * Use `ssh {user}@{server ip here} -i {your key location here}` to login

## Step 3: Secure your server
* Once you successfully login to your server, make sure that everything is up-to-date:
    * run `sudo apt update`, then `sudo apt upgrade`
        * NOTE: If prompted to update GRUB settings, go ahead and keep the suggested defaults
* Change the default ports on server
    * Configure the Uncomplicated Firewall to only allow incoming connections for SSH (port 2200), HTTP (port 80), and NTP (port 123).
        * This can be done with the following commands:
            * `sudo ufw default deny incoming`
            * `sudo ufw default allow outgoing`
            * `sudo ufw allow 2200/tcp`
            * `sudo ufw allow 80/tcp`
            * `sudo ufw allow 123/udp`
* Configure Lightsail firewall to allow connections on port 2200
* On your server run `sudo ufw enable` to restart the firewall with the new configuration
* Check that the firewall is active with `sudo ufw status`

## Step 4: Create `grader`
* Use `sudo adduser grader` to create the new user
* Grant `grader` the permission to `sudo` using `sudo visudo`
    * Below the line `root  ALL=(ALL:ALL) ALL`, add `grader  ALL=(ALL:ALL) ALL`
* In `/home/grader`, `mkdir .ssh`
* Then `touch .ssh/authorized_keys`, here you place the public key created on your local machine using `ssh-keygen`

## Step 5: Preparing the server
* Install Apache 2, `sudo apt install apache2`
* Then install module to run `wsgi` applications, `sudo apt install libapache2-mod-wsgi python-dev`
    * Enable the module with: `sudo a2enmod wsgi`
* Next install additional python modules: `sudo apt install python-pip python-psycopg2`
    * To manage python modules specific to this application use a virtual environment. To do this, you will need `virtualenv`
        * Use `sudo pip install virtualenv`
