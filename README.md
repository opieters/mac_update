mac_update
==========

Update command line programmes with just running one script.

**The use is fully responsible for any actions performed by the script. The repository owner, not it's contributors can be held responsible for any damage or file loss to your system.**

Installation
------------

1. Open Terminal (`CMD-SPACE` + terminal)
2. Go to the location you want the script to be installed (e.g. `~/Documents/mac_update`).
3. Download the files: `git clone https://github.com/opieters/mac_update.git`
4. Make script executable: `chmod +x mac_update.sh`
5. Print the current directory out: `pwd` (save this for later!)
6. Add the install location to your path:
    1. Go to Home directory: `cd ~`
    2. Open bash configuration file: `nano .bash_profile`
    3. Add to the bottom of the file: `export PATH="$PATH:<dir>"`, change `<dir>` to the directory your printed with `pwd` above.

Usage
-----

Update programmes: `mac_update.sh`

Arguments:

| CLI option                       | function                                                                |
|----------------------------------|-------------------------------------------------------------------------|
| `-a` or `--add-cmd` + command    | add an update command to the command file                               |
| `-c` or `--clear` + command-file | delete this command file                                                |
| `-q` or `--quiet`                | suppress any command line output of commands run                        |
| `-f` or `--cmdfile`              | specify the update-command-list file with : `mac_update -f no_sudo.cmd` |

For some programs (like `tlmgr`) you must run the script with administrator privileges. Add the `sudo` command before `mac_update` to run with administrator privileges.

License
-------

See LICENSE file.
