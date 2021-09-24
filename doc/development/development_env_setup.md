## XCode
- You actually just need the **XCode Command Line Tools**  
But the easiest way to download it is by installing **XCode**  
- There might be some links for **Command Line Tools** only  
Google it, or just try http://developer.apple.com/downloads

### Install iTerm2 (Optional)
Install [iTerm2](https://www.iterm2.com/) for better CUI

### Install Zsh (Optional)
Install [Oh my zsh](https://github.com/robbyrussell/oh-my-zsh) for better shell  
And follow [`zsh_bash_config.md`](./zsh_bash_config.md)  

## Homebrew

### Install
http://brew.sh/

### run brew doctor as suggested

- `brew doctor`

- Fix problem(s)

- Run `brew doctor` again to ensure it's done!

## Use Homebrew to install things
- `brew update`
- `brew install imagemagick vips`  
  (Image processing)
- `brew install libmagic`  
  (File content type detection)  
- `brew install git`
- `brew install redis` (and follow the instructions on screen)  
  You might also want to change local Redis config  
  See [`change_local_redis_config/README.md`](development_env/change_local_redis_config/README.md)
- Install MongoDB following instructions on  
  https://docs.mongodb.com/manual/tutorial/install-mongodb-on-os-x/
- Install ElasticSearch (and follow the instructions on screen)  
  https://www.elastic.co/guide/en/elasticsearch/reference/current/brew.html
- `brew install yarn`
- Install Node (see `NVM` below)
- `brew install openssl@1.1`  
  If you haven't installed it already
- `brew install cmake pkg-config`  
  (Required for installing some native gems)
- Install Ruby (see `RVM` below)
- Install PostgreSQL (see `PG setup` below)
- Setup `Git` (see `Git Setup` below)
- Setup app to get it running (see `Get the app running` below)

## NVM
For Intel Mac:
- `brew install nvm` (and follow the instructions on screen)
- `nvm install --lts`
- `nvm use --lts`

For Apple Silicon:
https://github.com/nvm-sh/nvm/blob/master/README.md#macos-troubleshooting

## RVM
For Intel Mac:
- Go [Official website](https://rvm.io/) for installation instruction  

For Apple Silicon:
- [Apple Silicon — M1 for Ruby developers](https://leonid.shevtsov.me/post/m1-for-ruby-developers/)

### Gems
`pg`:
(From https://leonid.shevtsov.me/post/m1-for-ruby-developers/) 
```shell
gem install pg -- \
  --with-pg-lib=/Applications/Postgres.app/Contents/Versions/13/lib \
  --with-pg-include=/Applications/Postgres.app/Contents/Versions/13/include
```

`ruby-filemagic`:
```shell
arch -x86_64 /usr/local/bin/brew install libmagic

gem install ruby-filemagic -- \
  --with-magic-dir=/usr/local/opt/libmagic
```

## PG setup

### Install
`brew install postgresql`

### More info
Check `brew info postgresql`

### Set the default encoding to UTF-8
http://stackoverflow.com/questions/16736891/pgerror-error-new-encoding-utf8-is-incompatible

### If you have `Role does not exist` error
http://stackoverflow.com/questions/8639424/role-does-not-exist-and-unable-to-create-database-when-using-postgresql

## Git Setup

### Global config
You can do these by CUI or GUI  
These are examples, don't brainlessly **copy & paste**  
- `$ git config --global user.name "username"`  
- `$ git config --global user.email "username@email.com"`  
You can only do this through CUI (with git from homebrew)  
- `$ git config --global credential.helper osxkeychain` (This is for https)

### GitHub
**Follow [these steps](https://help.github.com/articles/generating-ssh-keys) to add SSH key, and add to GitHub**

### Git GUI
**I recommend [SourceTree](http://www.sourcetreeapp.com/) for Git GUI**  
**You just need to register (Free) to use it forever**  

### More about Git & GitHub
See [Git and GitHub Notes](./git_and_github_notes) for more details  


## Get the app running…

- `cd <path-to-project>`
- `cp .env.example .env.development.local` ([What other .env* files can I use?](https://github.com/bkeepers/dotenv#what-other-env-files-can-i-use))  
  For dev you change some values for better dev experience, such as:  
  - `RACK_TIMEOUT_SERVICE_TIMEOUT`: Set to a high value to avoid the need to refresh the page due to long running asset compilation  
  - `RAILS_CONFIG_EAGER_LOAD_ENABLED_IN_DEVELOPMENT`: Set to `true` for catching incorrect initialization, class declaration, etc.  
  - `RAILS_CONFIG_ACTION_CONTROLLER_PERFORM_CACHING_ENABLED_IN_DEVELOPMENT`: Set to `true` for testing caching  
- `cp config/database.yml.example config/database.yml`
- `cp Passengerfile.json.example Passengerfile.json` & change the paths within it to your project path
- Follow [`hostname.md`](hostname.md)
- `yarn install`
- `bundle install`
- `gem install foreman`
- `rake db:create`
- Ask a senior dev to give you a recent DB dump from staging (1st time only)  
  For senior dev see [`doc/deployment/amazon_aws/accounts.md`](../deployment/amazon_aws/accounts.md) to see how to login into AWS  
- Restore the dump (see instructions at [`doc/development/postgresql/backup_and_restore.md`](postgresql/backup_and_restore.md))  
- Optionally run **ElasticSearch Data Setup** following instructions at [`doc/development/elastic_search/data_setup.md`](elastic_search/data_setup.md)  
- `foreman s -f Procfile.dev` to run the app  
  Or you can run processes in different tabs/windows with `foreman s -f Procfile.dev [process_type]`  
  See `Procfile.dev` for available process types
- Visit `dev.spacious.hk:3000` / `https://dev.spacious.hk:3001` to confirm that there is no error

### Git Hooks
Automation for various checks when code change committed  
Refers to `Dev Quick Links` > `Git Hooks`


You might have issue running passenger  
since the enterprise version has overridden the open source version  
which always asks for a license file  
To fix this:  
```sh
gem install --force passenger
```
This should ensure the open source version is used  


To eliminate the local website SSL cert warning see [`.ssl/README.md`](../../.ssl/README.md)


## More Dev tools

- [SwitchHosts](https://swh.app) - Change hosts on OSX easily (MacOS App)
- [Gas Mask](https://github.com/2ndalpha/gasmask) - Change hosts on OSX easily (MacOS App)

- [Postman](https://www.getpostman.com/) - easier HTTP request debugging (MacOS App)

- [Overmind](https://github.com/DarthSim/overmind) - `foreman` like process manager for Procfile-based applications (MacOS CLI)

- [Dash](https://kapeli.com/dash) - MacOS documentation browser (MacOS App)

- [DevDocs](https://devdocs.io/) - Multiple API documentations interface (Website)
- [ruby api](https://rubyapi.org) - Search and Explore Ruby Documentation (Website)

- [mkcert](https://github.com/FiloSottile/mkcert) - making local certs (MacOS CLI)


## Integrations

### Rubocop (ruby code linter)
- https://www.botreetechnologies.com/blog/integrate-rubocop-gem-popular-ruby-text-editors

### TypeScript
- https://github.com/Microsoft/TypeScript/wiki/TypeScript-Editor-Support


## Using default ports for development website

[Relative Link to doc](development_env/dev_web_server_on_standard_ports/README.md)

