sod-spellparser
===============

Rails Parser for the Shards of Dalaya spells_us File

## Ubuntu 20.04 Installation Instructions:

# Install basics for ruby on rails development (will isntall ruby 2.7.1)
`sudo apt install ruby`
`sudo apt install ruby-dev`
`sudo apt install build-essential patch ruby-dev zlib1g-dev liblzma-dev`
# Install mysql
Download `mysql-apt-config_0.8.15-1_all.deb` from dev.mysql.com
Install with `sudo dpkg -i path/to/mysql-apt-config_0.8.15-1_all.deb`
`sudo apt-get update`
`sudo apt install mysql-community-server` - NOTE: assumed password is `foo123`, if you use a different one you will need to update config/database.yml
# Create database and import dump
`mysql -u root -p`
`create database sod_spells;`
`use database sod_spells;`
`source path/to/databasedump.sql`
`quit;`
# Install last set of prerequisites
`sudo apt-get install libmysqlclient-dev libnetcdf-dev libssl-dev libcrypto++-dev libgmp-dev`
# Install and run the project!
Clone the repo, change directory to it
Copy config/database.yml.example into the same directory and rename to database.yml
`gem install bundler`
`bundle install`
`rails s` (development mode by default)

## To run in production mode:
# Set up Apache/Passenger
(May need to uninstall any older versions of Phusion Passenger first)
`sudo apt-get update`
`sudo apt-get install apache2`
`sudo apt-get install libapache2-mod-passenger`


## Irrelevant Depreciation Warnings
These two sets of depration warnings are because of rails itself, and can be safely ignored
```/var/lib/gems/2.7.0/gems/sprockets-rails-3.2.1/lib/sprockets/rails/helper.rb:355: warning: Using the last argument as keyword parameters is deprecated; maybe ** should be added to the call```
```/var/lib/gems/2.7.0/gems/sprockets-4.0.2/lib/sprockets/base.rb:118: warning: The called method `[]' is defined here```
You can permanently ignore them by doing any of the following:
`export RUBYOPT='-W:no-deprecated -W:no-experimental'` (ignores them forever)
Add `RUBYOPT='-W:no-deprecated -W:no-experimental'` before your server command, i.e. `RUBYOPT='-W:no-deprecated -W:no-experimental' rails server` (ignores it for that instance)
Add the line `Warning[:deprecated] = false` to Gemfile (ignores them for as long as that line exists)
See `https://github.com/rails/rails/issues/38202` and `https://rubyreferences.github.io/rubychanges/2.7.html#warning-and-` for more information.