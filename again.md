# System performance over style
System -> Advanced system settings -> Performance settings -> Best performance + smooth edges of screen fonts

# Enable WSL
```powershell
wsl --install
```
then reboot.

# Compile kanata ourselves

## Getting rust

Download [rustup](https://rustup.rs).

Need to install Visual Studio as well for some build tooling in Windows.

## Download git for windows

[official site](https://git-scm.com/download/win) - standalone installer.


## Clone repo

```shell
git clone https://github.com/jtroo/kanata.git
```

## Compile and install

```shell
cd kanata
cargo build --release --features cmd
cargo install --features cmd --path .
```

