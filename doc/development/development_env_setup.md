This doc is copy and edited from a project's notes.  
Might contains stuff for that project such as dependencies.  
Those can simply be ignored.  

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

## Application Dependencies
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
- Install Node (see `Install Node.js` below)
- `brew install yarn`
- `brew install openssl@1.1`
- `brew install cmake pkg-config`  
  (Required for installing some native gems)
- Install Ruby (see `Install Ruby` below)
- Install PostgreSQL (see `PostgreSQL Setup` below)
- Setup `Git` (see `Git Setup` below)
- Setup app to get it running (see `Spacious App Setup` below)

## Install Node.js
For **Intel Mac**:
- `brew install nvm` (and follow the instructions on screen)
- `nvm install --lts`
- `nvm use --lts`

For **Apple Silicon**:
https://github.com/nvm-sh/nvm/blob/master/README.md#macos-troubleshooting

People wanting to use a more universal runtime version manager can try:
- **asdf** - More universal runtime version manager
  - Go [Official website](https://asdf-vm.com) for core installation instruction
  - Go [Official plugin GH project for Node.js](https://github.com/asdf-vm/asdf-nodejs)


## Install Ruby

For **Intel Mac**, pick one of the following:
- **RVM** - Go [Official website](https://rvm.io/) for installation instruction  
  Older project but solid, works well for Mac with Intel chip
- **asdf** - More universal runtime version manager
  - Go [Official website](https://asdf-vm.com) for core installation instruction
  - Go [Official plugin GH project for Ruby](https://github.com/asdf-vm/asdf-ruby)  
  
  `asdf` is newer but seems less trouble in Ruby installation for Mac with M1 chip

For **Apple Silicon**:
- [Apple Silicon — M1 for Ruby developers](https://leonid.shevtsov.me/post/m1-for-ruby-developers/)

### Installation Method for Some Native Gems on Apple Silicon
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


## PostgreSQL Setup

### Install
- `brew install postgresql` (for PostgreSQL Client)
- [Postgres.app](https://postgresapp.com) (for PostgreSQL Server)  
  Using the one from Homebrew works too but not as convenient as this

### Potential Issues
Only read if any issue encountered

#### Set the default encoding to UTF-8
http://stackoverflow.com/questions/16736891/pgerror-error-new-encoding-utf8-is-incompatible

#### If you have `Role does not exist` error
http://stackoverflow.com/questions/8639424/role-does-not-exist-and-unable-to-create-database-when-using-postgresql


## Git Setup

### Global config
You can do these by CUI or GUI  
These are examples, don't brainlessly **copy & paste**  
- `$ git config --global user.name "username"`  
- `$ git config --global user.email "username@email.com"`  
You can only do this through CUI (with git from homebrew)  
- `$ git config --global credential.helper osxkeychain` (This is for https)


## Git Setup

### Global config
You can do these by CUI or GUI  
Use **your own** username and email address instead of **just copy & paste**  
- `$ git config --global user.name "username"`  
- `$ git config --global user.email "username@email.com"`  
You can only do this through CUI (with git from homebrew)  
- `$ git config --global credential.helper osxkeychain` (This is for https)

### GitHub
Follow [these steps](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token)  
to add personal access token(s) for each client & machine you use (probably need 1 only at the start)

Use GitHub personal access tokens(PAT) as password when using Git clients to authenticate

### Git GUI
**I recommend [SourceTree](http://www.sourcetreeapp.com/) for Git GUI**  
**You just need to register (Free) to use it forever**  

In case new version(s) got issue(s) you can [download older versions](https://www.sourcetreeapp.com/download-archives)  
Or even fall back to latest 3.x (`3.2.1`)

### More about Git & GitHub
See [Git and GitHub Notes](./git_and_github_notes) for more details  


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


