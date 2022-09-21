# Setting up the dev shell

## Changing default shell
Run this command to default to bash
```
chsh -s bin/bash
```

## HomeBrew
Install HomeBrew from https://brew.sh/ and update the ```bash_profile``` to include the follwoing line
```
eval "$(/opt/homebrew/bin/brew shellenv)"
```

## Pyenv
### Setting up the bash shell for pyenv
Run the commands to setup the bashrc script (Also see in the link : https://github.com/pyenv/pyenv#set-up-your-shell-environment-for-pyenv)
```
echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.bashrc
echo 'command -v pyenv >/dev/null || export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.bashrc
echo 'eval "$(pyenv init -)"' >> ~/.bashrc
```


## Git settings
### Setting up P4Merge
Follow steps here : https://gist.github.com/tony4d/3454372
```
$ git config --global merge.tool p4mergetool
$ git config --global mergetool.p4mergetool.cmd \
"/Applications/p4merge.app/Contents/Resources/launchp4merge \$PWD/\$BASE \$PWD/\$REMOTE \$PWD/\$LOCAL \$PWD/\$MERGED"
$ git config --global mergetool.p4mergetool.trustExitCode false
$ git config --global mergetool.keepBackup false
```

### Git Prompt
To have a more useful git prompt with the branch and other info, use this link and follow the steps : https://github.com/magicmonty/bash-git-prompt#installation
