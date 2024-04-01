# Rice steps

## Enable/Install WSL2

In Powershell, installing the canoncial flavour (probably ubunutu)

```powershell
wsl --install
```

## Install zsh and oh-my-zsh

Requires manual reply.

Just for convience, can do without oh-my-zsh if there is push back.

In WSL,

```bash
sudo apt install zsh -y
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

## Install Neovim

I require a somewhat recent version that's not in the ubuntu/debian default repository.
Grabbing from GitHub release.

In WSL,

```bash
mkdir ~/apps
wget https://github.com/neovim/neovim/releases/download/v0.9.5/nvim-linux64.tar.gz
tar xzvf nvim-linux64.tar.gz
mv nvim-linux64 ~/apps
sudo ln -s /home/ryan/apps/nvim-linux64/bin/nvim /usr/local/bin/nvim
```

## Install kmonad

I require this for keyboard remapping that I am familiar with.
Alternative might be AutoHotkey which I am not 100% sure will fit my need.

(TODO: Confirm this can act as komorebi's invoker so one less software needs to be vetted)

Unfortunately have to build ourselves for version 0.4.2+ which contains a fix for key repeat in Windows. 

In Powershell, (instruction adapted from kmonad official repo, not sure how correct it is)

```powershell
# set required privileges to run scripts (required for scoop installer)
Set-ExecutionPolicy RemoteSigned -scope CurrentUser

# install scoop (no admin rights required)
iwr -useb get.scoop.sh | iex

# install stacka and git
scoop install stack git

# clone the KMonad repository
cd $HOME\Downloads
git clone https://github.com/kmonad/kmonad.git
cd kmonad

# compile KMonad (this will first download GHC and msys2, it takes a while)
stack build

# the new kmonad.exe will be in .\.stack-work\install\xxxxxxx\bin\

# install kmonad.exe (copies kmonad.exe to %APPDATA%\local\bin\)
stack install
```

## Clone this repo (WSL)

For grabbing dotfiles later.

In WSL,

```bash
git clone https://github.com/ryantam626/window-rice.git
```

## Clone this repo (Windows)

For grabbing dotfiles later.

Can't work out how to create a symlink that works without admin rights.

In Powershell,

```powershell
git clone https://github.com/ryantam626/window-rice.git
```

## Create kmonad shortcut

Just make a shortcut entry manually with the following command.

```powershell
C:\Windows\System32\cmd.exe /k C:\Users\ryant\AppData\Roaming\local\bin\kmonad.exe C:\Users\ryant\window-rice\dotfiles\kmonad\base.kbd
```

Using `cmd.exe` is necessary for some reason, otherwise if we just do `kmonad.exe <config>`, it will somehow fail due to permission issues (unless we run as admin).

## TODO
- Vim system clipboard
