### For BEAM Meetup

### Install Package Manager (Mac)
We will need Ruby to install Homebrew. Mac comes with Ruby preinstalled, so you can check for the Ruby Version here
- Check Ruby Version

` ruby -v `

If Ruby exists you will get the version details. If not you may have to install Ruby

#### Install Homebrew

`ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"`

#### Run Update
`brew update`


### Install dependencies

#### For Ubuntu

`sudo apt-get install automake autoconf libreadline-dev libncurses-dev libssl-dev libyaml-dev libxslt-dev libffi-dev libtool unixodbc-dev`

#### For Mac

`brew install automake autoconf openssl libyaml readline ncurses libxslt libtool unixodbc`

###  Install git

#### For Ubuntu

`sudo apt-get install git`

#### For Mac

`brew install git`

####  Installing Erlang, Elixir & Node through asdf package manager

asdf is a version package manager which supports Ruby, Nodejs, Erlang & Elixir. Basically it allow to install and mange multiple versions of each language easily. Ref: https://github.com/asdf-vm/asdf

`git clone https://github.com/asdf-vm/asdf.git ~/.asdf`

This creates a `.asdf` folder in your home directory.  All the versions are installed in the ~/.asdf/installs directory

Use asdf into the shell you are using

```
# For Ubuntu or other linux distros
echo '. $HOME/.asdf/asdf.sh' >> ~/.bashrc
echo '. $HOME/.asdf/completions/asdf.bash' >> ~/.bashrc

# OR for Max OSX
echo '. $HOME/.asdf/asdf.sh' >> ~/.bash_profile
echo '. $HOME/.asdf/completions/asdf.bash' >> ~/.bash_profile

# For Zsh & other Shells, copy it to appropriate profile files and reload your shell

# This command should give you options which are present in asdf

asdf

```

### Installing Erlang

We can now install Erlang by using asdf Erlang plugin - https://github.com/asdf-vm/asdf-erlang

`
asdf plugin-add erlang https://github.com/asdf-vm/asdf-erlang.git
`

To check if Erlang Plugin is installed

`
asdf plugin-list
`

You should see Erlang there

To see the Erlang versions which are available type

`
asdf list-all erlang
`

You will see different versions of Erlang which you can install, we will be using the latest version available (18.3 currently)

`
asdf install erlang 18.3
`

This will download & configure Erlang for you.

We need to tell `asdf` which version of erlang we want to use, for that we will use file `.tool-versions` in the home directory

`
nano ~/.tool-versions
`

put the following in the file

`
erlang 18.3
`

Now you can check whether installation is correct and the version number

`
erl
`
This will open a interactive command interface for Erlang, with Erlang version on the first line. You can exit this by typing ` ctrl + c ` (on both Mac & Ubuntu)

We can now install Elixir

### Installing Elixir

We will use `asdf` to install the Elixir plugin - https://github.com/asdf-vm/asdf-elixir

`
asdf plugin-add elixir https://github.com/asdf-vm/asdf-elixir.git
`

You can now see the elixir version which are available for elixir

`
asdf list-all elixir
`

We will be installing the latest elixir (v 1.2.3 currently)

`
asdf install elixir 1.2.3
`

Add this version number to `.tool-versions` file

`
nano ~/.tool-versions

erlang 18.3
elixir 1.2.3
`


You can check whether elixir is properly installed by starting its interactive shell, you can break out of it by tying `ctrl + c `

`
iex
`

Phoneix Framework uses Brunch to manage static assets - Javascripts, CSS etc. We will be needing nodejs also, and fortunately we can manage nodejs through asdf

### Installing Nodejs

First, we will add Nodejs asdf plugin - https://github.com/asdf-vm/asdf-nodejs

`
asdf plugin-add nodejs https://github.com/asdf-vm/asdf-nodejs.git

`

We can check which versions of Nodejs are available

`
asdf list-all nodejs
`

We will be installing the latest version of the nodejs, (6.3.0 currently)

`
asdf install nodejs 6.3.0
`

Add nodejs to the `~./tools-versions` file

`
nano ~/.tool-versions

erlang 18.3
elixir 1.2.3
nodejs 6.3.0
`

You can check the node installation by typing

`
node -v
`

This completes the basic setup required for Phoenix. We can now install Phoenix itself.

### Installing Phoenix

Elixir comes with its own package manager/build tool called `mix`. You can see what commands are available by

`
mix help
`

We have commands for dependency management `mix deps`, commands to compile `mix compile`,  commands to run tests `mix test`. All in all, a nice rounded tool.

We will install Phoenix now

`
mix archive.install https://github.com/phoenixframework/archives/raw/master/phoenix_new.ez
`

## Installing Editor Plugins

```
# For Vim

https://github.com/elixir-lang/vim-elixir

# For Sublime Text

ctrl  + P , add Elixir Plugin

```


------

### Phoenix App

`
mix phoenix.new my_app
`

This will create a directory `my_app` which is your new Phoenix Application with default database as PostgreSQl.

The command will also install some dependencies for Phoenix like Brunch etc. Accept those dependencies
