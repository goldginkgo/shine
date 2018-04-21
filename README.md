# Rails, Angular, Postgres, and Bootstrap
## Ubuntu 14.04 LTS
## Install Ruby
## Install Postgres (Remove old Postgres first)
~~~
https://www.postgresql.org/download/linux/ubuntu/
$ sudo vi /etc/apt/sources.list.d/pgdg.list
deb http://apt.postgresql.org/pub/repos/apt/ trusty-pgdg main
$ wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo apt-key add -
$ sudo apt-get update
$ sudo apt-get install postgresql-9.6 
create user (password: shine)
$ sudo -u postgres createuser --createdb --login -P shine
$ sudo vi /etc/postgresql/9.6/main/pg_hba.conf
- local   all             all                                     peer 
+ local   all             all                                     md5 
$ sudo service postgresql restart
~~~

## Setup NodeJS (nvm not installed)
~~~
https://nodejs.org/en/download/package-manager/#debian-and-ubuntu-based-linux-distributions
$ curl -sL https://deb.nodesource.com/setup_8.x | sudo -E bash -
$ sudo apt-get install -y nodejs
~~~

## Setup Node (nvm installed)
~~~
$ nvm install 8
$ nvm use 8
~~~

## Yarn, Webpack
~~~
https://yarnpkg.com/en/docs/install#debian-stable
$ curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -
$ echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list
$ sudo apt-get update && sudo apt-get install yarn
~~~

## Deploy application
~~~
$ git clone https://github.com/goldginkgo/shine.git
$ cd shine
$ gem install bundle
$ bundle install
$ yarn install
$ rails db:create
$ rails db:migrate
$ foreman start
~~~
