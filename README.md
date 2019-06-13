# How to set-up your machine (AKA get off Vagrant !!!)  #UNOFFICIAL


### For Mac

Step one Install Brew


from the [brew site](https://brew.sh/).
```
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```
Once you run this it will install a package manger and xcode for your mac.

### Installing NVM (Node version manager) with Brew

This will install node version manager.
Run these commands. from this [site](http://dev.topheman.com/install-nvm-with-homebrew-to-use-multiple-versions-of-node-and-iojs-easily/)

```
brew update
brew install nvm
nano ~/.bash_profile
```
A terminal editor will pop up. Here you will have to insert this piece of code. Inside of the terminal window.

```
export NVM_DIR=~/.nvm
source $(brew --prefix nvm)/nvm.sh
```
Once thats done, Press CNTRL + X, it will then ask you if you want to save, press `Y` and then hit up enter. Then write `exit` to kill your terminal session, and close your terminal.

Then reopen your terminal, write `nvm` and hit enter.  If it prints out `nvm` help documentation you are done !!!!!

#### Installing a Node (version)

```
nvm install 8.9.4
```

### Installing Postgres

Inside your terminal run

```
brew install postgresql
```
Once installed make sure to run `brew services start postgresql` (If you restart your computer and postgres is not on, make sure to run this command again.)

#### Configuration of postgres account

If you run `psql` it will say `FATAL: database username does not exist`. This means that we need to make a user role and a database with the current user.
To do this:

```
psql postgres
CREATE USER <YOUR USERNAME OF THE MACHINE>;
CREATE DATABASE <YOUR USERNAME OF THE MACHINE>;
ALTER USER <YOUR USER NAME> WITH Superuser createrole createdb replication;
```
lets also create a user with a password (maybe needed for some projects)
```
CREATE USER labber WITH PASSWORD 'labber';
CREATE DATABASE labber OWNER labber;
ALTER USER labber WITH Superuser createrole createdb replication;
```
Once we're done quit out of postgres. And try to log in by just writting `psql`. If it works then everything worked correctly.

### Installing RVM

We need to run this command

```
\curl -sSL https://get.rvm.io | bash
rvm get stable
```

and after this exit and close your terminal.
Then open the terminal again and run `rvm install 2.3.0`. This will install Ruby ver 2.3.0 to your computer
We will also install 2.6.3 (or any latest ruby version at this time)
`rvm install 2.6.3`

Note: if you have error `bundle install` on jungle with rmagick
these are the commands to fix
```
brew unlink imagemagick
brew install imagemagick@6 && brew link imagemagick@6 --force
```

## BONUS STUFF TO INSTALL

###Installing Postico

Go to this [website](https://eggerapps.at/postico/) and install Postico.
Postico will help you see your database and visualize each table. It helps alot when developing.

### Add A Little bit of Color to your Terminal

```
nano ~/.bash_profile
```

### Installing ImageMagick (required for many rails projects)

If you already have the old version installed
```
brew unlink imagemagick
```
Then install and link version 6
```
brew install imagemagick@6
brew link imagemagick@6 --force
```


while in there add

```
export CLICOLOR=1
export LSCOLORS=ExFxCxDxBxegedabagacad
```

save and restart your terminal (exit and close)
Once open, write `ls` and you should have some color on your terminal files.
