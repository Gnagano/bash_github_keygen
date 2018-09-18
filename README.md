SSH Key generator for github
===

## Overview

Each GitHub repository requires each other ssh key, so better to create the keys in the easier way.
I write the shell script for easier github ssh key generator.

## Usage

### Command Usage

Use the script "github_keygen.sh" in the repository.
The usage of the script is

```
github_keygen [-C comment] <project>
```

Option -C is the same as option -c of ssh-keygen.
The argument "project" is required, it is used as keys' name and ssh host name. The details is below.

### What's happen by the script

After executing the script, rsa keys are generated to $HOME/.ssh/ whose name is the argument specified by <project>, like private key is project, public key is project.pub.

Then create the backup for $HOME/.ssh/config as $HOME/.ssh/backup/config_backup and edit $HOME/.ssh/config.
The lines are added to the ssh config file ..

```
Host <project>
  Port 22
  HostName github.com
  IdentityFile ~/.ssh/<project>
  TCPKeepAlive yes
  IdentitiesOnly yes
```

After this you should deploy the key to your github repository and you can access the repository by

```
git@<project>:<UserName>/<projectName>.git
```
