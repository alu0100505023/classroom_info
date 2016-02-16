## Hacking on Classroom for GitHub

### Get started
New to Ruby? No worries! You can follow these instructions to install a local server.

#### Installing a Local Server

First things first, you'll need to install Ruby 2.3.0. We recommend using the excellent [rbenv](https://github.com/sstephenson/rbenv),
and [ruby-build](https://github.com/sstephenson/ruby-build)

```bash
rbenv install 2.3.0
rbenv global 2.3.0
```
Watch this tutorial if you want to use [rvm](https://rvm.io/rvm/install) instead of rbenv

Next, you'll need to make sure that you have PostgreSQL, Redis, Memcached, and Elasticsearch installed. This can be
done easily on OSX using [Homebrew](http://brew.sh)

```bash
brew install postgresql redis memcached elasticsearch
```
Or install each component using apt-get.

You will want to set postgresql to autostart at login via launchctl, if not already. See `brew info postgresql`. Redis and memcached may be setup similarly via launchctl or setup project wide by using foreman, described below.

Make sure you had installed NodeJS in your machine .
```
apt-get install nodejs
```

Now, let's install the gems from the `Gemfile` ("Gems" are synonymous with libraries in other
languages).

```bash
gem install bundler && rbenv rehash
```
Or if you want to install it with bundle

```bash
bundle install classroom
```


### Setup Classroom for GitHub
Once bundler is installed go ahead and run the `setup` script
```
script/setup
```
### Running the application

Foreman is setup to manage redis, memcached, sidekiq, and elasticsearch in development mode. Postgresql must be running prior executing foreman. It assumes that redis, memcached, and elasticsearch are not already running on the system. Alternatively, you may run `script/sidekiq`, if you have to have redis, memcached, and elasticsearch always running system wide. To execute foreman, and this application's dependencies, run:

```bash
script/workers
```

After that, you may start the rails server in a separate terminal with:

```bash
script/server
```


