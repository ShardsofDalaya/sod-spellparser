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
# To run in production mode:
`EDITOR="mate --wait" rails credentials:edit` (only have to do this once)
`rails s -e production`