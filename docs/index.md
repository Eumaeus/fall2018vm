# Furman Classics VM: Fall 2018

## Setup

1. Download and install [VirtualBox](https://www.virtualbox.org).
1. Download and install [Vagrant](https://www.vagrantup.com).

**N.b.** Vagrant is a Command-line application. When it installs, you will not see an icon for the application. This is normal.

### Windows Users

1. Download the [Git for Windows installer](https://gitforwindows.org).
1. Run the installer, accepting all defaults.

## Running

In a terminal (`Terminal.app` on MacOS, `Git-Bash` on Windows), after navigating into `fall2018vm` using `cd`:

1. `vagrant up` starts the virtual machine. It will take a long time the first time.
1. `vagrant ssh` connects your Terminal session to the virtual machine.
1. [ Do your work, starting with `cd /vagrant/` and then `ls` to see your working files. ]
1. `logout` to exit the VM.
1. `vagrant halt` to shut down the VM.

The contents of `/vagrant/` in the VM are the same as the contents of `fall2018vm` on the host (your actual computer).

## Using EZ-Morphology

- `vagrant up`
- `vagrant ssh`
- `cd /vagrant/ez-morph`
- `git pull` (to see if there are any updates)
- `sbt console`
- `:load tools.sc`
- `betaCode()` (to confirm that everything works)

When done…

- `:quit` (exit SBT Console)
- `logout` (exit the VM)
- `vagrant halt` (stop the VM)


		