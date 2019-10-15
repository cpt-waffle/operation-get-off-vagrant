
# How to set-up your machine (AKA get off Vagrant !!!)  # UNOFFICIAL

## Installing NVM
Open terminal and type this command.
```
curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.0/install.sh | bash
```
Exit terminal, then open it again then type `nvm`


```
nvm install 8.9.4
nvm install 10.15.3
```



### Installing Postgres

In the terminal write
```
sudo apt-get install postgresql postgresql-contrib
```
this will install postgres. Once the installation finished run this command to set it to run on boot.

```
update-rc.d postgresql enable
```

Then run this command to actually start postres
```
service postgresql start
```
Also run this

`sudo apt-get install postgresql-client libpq5 libpq-dev`
this will be needed for later.


if you write `psql` in your terminal you won't be able to connect to it because of database not existing.
To fix this type:
`sudo -u postgres -i`
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
## Next is to Install RVM OR RBENV

# NOTE: ONLY INSTALL ONE OR OTHER BUT NOT BOTH !!!!!!! ( Suggestion: install rbenv ) 

### Installing RBENV

First run these command to get the correct dependencies

`sudo apt install autoconf bison build-essential libssl-dev libyaml-dev libreadline6-dev zlib1g-dev libncurses5-dev libffi-dev libgdbm5 libgdbm-dev`

Then clone rbenv 

`git clone https://github.com/rbenv/rbenv.git ~/.rbenv`

Next, is to add the correct path to your bashrc so you are able to use `rbenv`

`echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bashrc`

`echo 'eval "$(rbenv init -)"' >> ~/.bashrc`

Then reload your `bashrc` with this command

`source ~/.bashrc`

Now install the latest ver of ruby with this command

`rbenv install 2.6.5`

Once that command completes, make the latest ver of ruby the `global` ruby for your machine 

`rbenv global 2.6.5`

Then install ruby 2.3.5 for running old projects 

`rbenv install 2.3.5`

Use the `local` command to run folders/projects in specific ver of ruby ( such as older rails projects ) 

`rbenv local 2.3.5`

### Installing RVM ( ONLY IF YOU DIDN"T INSTALL RBENV )

We need to run this command

```
gpg --keyserver hkp://pool.sks-keyservers.net --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3 7D2BAF1CF37B13E2069D6956105BD0E739499BDB
```

```
\curl -sSL https://get.rvm.io | bash
rvm get stable
```

```
sudo apt-get install postgresql-client libpq5 libpq-dev
```

and after this exit and close your terminal.
Then open the terminal again and run `rvm install 2.3.5`. This will install Ruby ver 2.3.5 to your computer
We will also install 2.6.3 (or any latest ruby version at this time)
`rvm install 2.6.3`

## BONUS STUFF TO INSTALL

### Installing pgadmin3
`sudo apt install pgadmin3`

### Byobu Terminal
 [http://byobu.co/](http://byobu.co/)
