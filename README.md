# zls-git

This PKGBUILD allows you to easily install the latest development version of Zig Language Server (zls).

## About Zls

The Zig Language Server (zls) is a tool that implements Microsoft's Language Server Protocol for Zig in Zig. In simpler terms: it'll provide you with completions, go-to definition, etc. when you write Zig code!

The following links provide information and resources related to zls :

- [Source](https://github.com/zigtools/zls) :  The source code for the Zig programming language, hosted on GitHub.
- [Official Site](https://install.zigtools.org/) :The main website for the The Zig Language Server (zls).

## Installation

1. Clone the `zls-git` repository from Github using the following command:

```
git clone https://github.com/Thoxy67/zls-git.git
```

2. Change your current working directory to the `zls-git` folder:

```
cd zls-git
```

3. You can now build and install the package via makepkg:

```
makepkg -si
```

After installation, you can start using Zig Language Server by running the `zls` command in your
terminal.

## Update

To update zls, run the `makepkg -si` script again. It will check for updates and
build the new PKGBUILD to proceed with the installation.


## License

This repository is licensed under the MIT License. For more information, see the
[LICENSE](LICENSE) file.
