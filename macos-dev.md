# MacOS dev setup
## XCODE
### remove old xcode
```
sudo rm -rf /Library/Developer/CommandLineTools
```
### install xcode
```
xcode-select --install
```
### update xcode
```
softwareupdate --all --install --force
```

## ZSH
### install zsh
```
sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```
### modify zsh config theme
```
open -a TextEdit ~/.zshrc
```
```
ZSH_THEME="miloshadzic"
```

## HOMEBREW
### install homebrew
```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```
### cure
```
brew doctor
```
### update
```
brew update
```
### upgrade packages and casks
```
brew upgrade
```
### uninstall old versions
```
brew cleanup
```

## GIT
### install openssl
```
brew install openssl
```
### install git
```
brew install git
```
### list files in .ssh directory
```
ls -la ~/.ssh
```
### create new SSH key using email as label
```
ssh-keygen -t id_12345 -C "email@address.com"
```
### start ssh-agent in background
```
eval "$(ssh-agent -s)"
```
### create ssh config
```
touch ~/.ssh/config
```
### modify ssh config
```
open -a TextEdit ~/.ssh/config
```
```
Host *
AddKeysToAgent yes
UseKeychain yes
IdentityFile ~/.ssh/id_12345

```
### add SSH private key to ssh-agent and store passphrase in keychain
```
ssh-add -K ~/.ssh/id_12345
```
### add SSH key to GitHub account
```
pbcopy < ~/.ssh/id_12345.pub
```

## PY
### install pyenv deps
```
brew install openssl readline sqlite3 xz zlib
```
### install pyenv
```
brew install pyenv
```
### configure shell env for pyenv
```
echo 'eval "$(pyenv init --path)"' >> ~/.zprofile
echo 'eval "$(pyenv init -)"' >> ~/.zshrc
```
### install py versions
```
pyenv install 3.10.0
```
### set global py version
```
pyenv global 3.10.0
```
### set local py version
```
cd ~/path/to/project
pyenv local 3.10.0
```
### install pipenv
```
brew install pipenv
```

## NODE
### install nvm
```
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.0/install.sh | bash
```
### install node versions
```
nvm install 16 17
```
### set global node version
```
nvm use node 16
```
### install yarn
```
brew install yarn
```

## MongoDB
### install mongo
```
brew tap mongodb/brew
brew install mongodb-community@6.0
```

### run, check & stop as a macOS service
```
brew services start mongodb-community@6.0
brew services list
brew services stop mongodb-community@6.0
```

### run & check manually as a background process
```
mongod --config /usr/local/etc/mongod.conf --fork
ps aux | grep -v grep | grep mongod
```

## Heroku
```
brew tap heroku/brew && brew install heroku
```