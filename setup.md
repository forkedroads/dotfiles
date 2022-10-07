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


## Java
If using intellij, download SDKs using intellij. It is easier. https://www.jetbrains.com/help/idea/sdk.html#jdk-from-ide

### Getting Java versions installed
To find out all the versions that are available, run the following command
```
/usr/libexec/java_home -V
```
The output will look like this

```
Matching Java Virtual Machines (3):
    19 (arm64) "Oracle Corporation" - "OpenJDK 19" /Users/xyz/Library/Java/JavaVirtualMachines/openjdk-19/Contents/Home
    1.8.333.02 (x86_64) "Oracle Corporation" - "Java" /Library/Internet Plug-Ins/JavaAppletPlugin.plugin/Contents/Home
    1.8.0_342 (x86_64) "Amazon" - "Amazon Corretto 8" /Users/xyz/Library/Java/JavaVirtualMachines/corretto-1.8.0_342/Contents/Home
/Users/xyz/Library/Java/JavaVirtualMachines/openjdk-19/Contents/Home
```
### Configuring a specific version to b e used
To set a specific version to be used, do the following (use the path from the previous step)

```
export JAVA_HOME=<path from the previous step>
```
where ```<path from the previous step>``` = ```/Library/Internet Plug-Ins/JavaAppletPlugin.plugin/Contents/Home```  for setting up *1.8.333.02* from the previous step

### Bash changes
Change bashrc to include the following
```
export JAVA_8_HOME=/Library/Internet\ Plug-Ins/JavaAppletPlugin.plugin/Contents/Home
export JAVA_8_AWS_HOME=/Users/xyz/Library/Java/JavaVirtualMachines/corretto-1.8.0_342/Contents/Home
export JAVA_19_HOME=/Users/xyz/Library/Java/JavaVirtualMachines/openjdk-19/Contents/Home
alias java8='export JAVA_HOME=$JAVA_8_HOME'
alias java19='export JAVA_HOME=$JAVA_19_HOME'

# Default to Java 19
java19
```
