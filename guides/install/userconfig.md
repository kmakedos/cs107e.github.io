---
title: Home/user config for CS107E
toc: true
---


After you have installed the development tools, follow the steps below to configure your user environment.

{% include callout.html type="warning" %}
Note: For those running WSL on Windows, be sure that you are in the linux shell when following these instructions.
</div>

### Set up cs107e_home
1. Create a new directory named `cs107e_home` to store course materials. The tilde character `~` is shorthand for home directory, so the path `~/cs107e_home` creates the directory within your home. 

    ```
    $ mkdir ~/cs107e_home
    ```

2. Change to the new directory and clone the courseware repository here. This repo is used to distribute code and materials for lectures, labs, and assignments. 

    ```
    $ cd ~/cs107e_home
    $ git clone https://github.com/cs107e/cs107e.github.io
    Cloning into 'cs107e.github.io'...
    ```

✔️__Check:__ confirm with the following command:

```
$ ls ~/cs107e_home/cs107e.github.io/cs107e/
bin/     etc/     extras/  include/ lib/     src/
```

### Edit shell configuration file
Now you must edit your shell configuration to indicate where your cs107e home is.

When opening a new shell, the environment is initialized by reading a configuration file in your home directory. Editing the configuration file allows you to set the initial state of your shell. 

The name of the configuration file depends on which shell you are using. Use the command `echo $SHELL` to see your shell. Your shell is likely `bash`, although it might be `zsh`.

```
$ echo $SHELL
/bin/bash
```

If your shell is `bash`, the file is named `.bashrc`.  If your shell is `zsh`, the file is named `.zshrc`.  For any other shell, please contact a CA for help.

Change to your home directory and find the configuration file for your shell. Note that filenames starting with a dot are hidden in the directory listing by default. Use the command `ls -a` to list all files, including hidden ones:

```
$ cd ~
$ ls -a
.    .bash_history   .bashrc     cs107e_home     .python_history 
..   .bash_logout    .config     .profile        .viminfo
```

Open the appropriate configuration file for your shell in a text editor, and append the following two lines verbatim:

```
export CS107E=~/cs107e_home/cs107e.github.io/cs107e
export PATH=$PATH:$CS107E/bin
```

The first line sets the environment variable `CS107E` to the path to where the class files are stored. The second line adds our `bin` subdirectory to your executable path.
  
✔️__Check:__ Open a new shell and confirm the configuration with the following commands:

```
$ echo $CS107E
/Users/student/cs107e_home/cs107e.github.io/cs107e
$ ls $CS107E/lib/libpi.a
/Users/student/cs107e_home/cs107e.github.io/cs107e/lib/libpi.a

$ which pinout
/Users/student/cs107e_home/cs107e.github.io/cs107e/bin/pinout
```

### Configure git user
Execute the following two commands so that your identity will be properly recorded for your git actions.

(Replace `My Name` and `myemail@stanford.edu` with your own.)

```
$ git config --global user.name "My Name"
$ git config --global user.email myemail@stanford.edu
```

✔️__Check:__ confirm your git configuration with the following command:

```
$ git config --get-regexp user
user.name My Name
user.email myemail@stanford.edu
```

