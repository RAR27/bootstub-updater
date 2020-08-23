# bootstub-updater

![GitHub](https://img.shields.io/github/license/RAR27/bootstub-updater)
[![GitHub release (latest by date)](https://img.shields.io/github/v/release/RAR27/bootstub-updater)](https://github.com/RAR27/dyn-wall-rs)
[![Crates.io](https://img.shields.io/crates/v/bootstub-updater)](https://crates.io/crates/bootstub-updater)
[![AUR](https://img.shields.io/aur/version/bootstub-updater)](https://aur.archlinux.org/packages/bootstub-updater/)

A utility to allow you to very easily maintain your EFI bootstub\
 Written in rust.
## Introduction
The aim of bootstub-updater is to simplify the process of maintaining a bootstub entry. After figuring out the command that creates a bootstub, you pretty much set it and forget it!

## Installation
bootstub-updater can be installed through one of the methods listed below.

### Cargo
First, install rust, and then run the following command:
```
cargo install bootstub-updater
```
To update after installation, run:
```
cargo install bootstub-updater --force
```

### Manual
  1. Download the latest binary from the [releases](RELEASES) page
  2. (**Optional**) To ensure the file you downloaded is correct and was not tampered with, do the following:
      1. Download the respective `.sha256` file
      2. Run `sha256sum` on the `.tar.gz` file
      3. Compare the output of the command with the contents of the `.sha256` file. If they are the same, then your file has not been tampered with
  3. Unpack the `.tar.gz file` by running\
`tar -zxvf bootstub-updater.tar.gz`
  4. You can now run it by running `./bootstub-updater` in the directory the binary was unpacked. It is recommended to place the binary in your $PATH (ex. `/usr/bin`, which is commonly used), so you can use it from anywhere

## Usage
Before anything, figure out the command to create an efibootstub that boots your current kernel. Instructions can be found [here](https://wiki.archlinux.org/index.php/EFISTUB).

### Command Line
  * **-c, --command \<COMMAND>**\
    Enter full efibootmgr command to be run when kernel is updated, replacing the kernel version number with `%v`. Surround command with quotation marks.
    
  * **-b, --bootnum \<NUM>**\
    Entry number of current entry in efibootmgr. Will be removed and replaced with the new one.

  * **-f, --format**\<FILENAME>**\
    Example of naming convention of kernel for your current distro. Replace version number with `%v`.\
    ex. `vmlinuz-%v`
    
  * **-p, --path \<FILEPATH>**\
    Specify the location of a TOML file to configure the program through a config file. An example can be found [here](https://github.com/RAR27/bootstub-updater/blob/master/examples/config.toml).
  
### Config File
bootstub-updater can also be configured through a config file. You can specify the location of the config file through the `--path` option.

Through this config file, you can use the same configuration options as through the command line.