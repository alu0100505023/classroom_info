## Hacking on Classroom for GitHub

### Get started
New to Ruby? No worries! You can follow these instructions to install a local server.

#### Installing a Local Server

First things first, you'll need to install Ruby 2.2.4. We recommend using the excellent [rbenv](https://github.com/sstephenson/rbenv),
and [ruby-build](https://github.com/sstephenson/ruby-build)

```bash
rbenv install 2.3.0
rbenv global 2.3.0
```

Next, you'll need to make sure that you have PostgreSQL, Redis, Memcached, and Elasticsearch installed. This can be
done easily on OSX using [Homebrew](http://brew.sh)

```bash
brew install postgresql redis memcached elasticsearch
```

You will want to set postgresql to autostart at login via launchctl, if not already. See `brew info postgresql`. Redis and memcached may be setup similarly via launchctl or setup project wide by using foreman, described below.

Make sure you had installed in your machine NodeJS
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

### Production environment variables
ENV Variable | Description |
:-------------------|:-----------------|
`AIRBRAKE_API_KEY` | the API key for airbrake.io, if set Airbrake will be enabled
`CANONICAL_HOST` | the preferred hostname for the application, if set requests served on other hostnames will be redirected
`GOOGLE_ANALYTICS_TRACKING_ID` | identifier for Google Analytics in the format `UA-.*`
`PINGLISH_ENABLED` | Enable the `/_ping` endpoint with relevant health checks
`MOTD` | Show the message of the day banner at the top of the site

### Development environment variables
These values must be present in your `.env` file (created by `script/setup`).

ENV Variable | Description |
:-------------------|:-----------------|
`GITHUB_CLIENT_ID`| the GitHub Application Client ID.
`GITHUB_CLIENT_SECRET`| the GitHub Application Client Secret.
`NON_STAFF_GITHUB_ADMIN_IDS` | GitHub `user_ids` of users to be granted staff level access.

