
[eumaeus.github.io](https://eumaeus.github.io) 

# Furman Classics VM: Fall 2018

## Setup  

1. Download and install [VirtualBox](https://www.virtualbox.org).
	- Mac Users: Follow the download link on the home page and then choose [OS X Hosts](https://download.virtualbox.org/virtualbox/5.2.18/VirtualBox-5.2.18-124319-OSX.dmg).
	- Windows Users: Follow the download link and then choose [Windows Hosts](https://download.virtualbox.org/virtualbox/5.2.18/VirtualBox-5.2.18-124319-Win.exe).
1. Download and install [Vagrant](https://www.vagrantup.com). 
	- Mac Users download [MacOS (64 bit)](https://releases.hashicorp.com/vagrant/2.1.4/vagrant_2.1.4_x86_64.dmg). 
	- Windows users download [Windows (64 bit)](https://releases.hashicorp.com/vagrant/2.1.4/vagrant_2.1.4_x86_64.msi).

**N.b.** Vagrant is a Command-line application. When it installs, you will not see an icon for the application. This is normal.

### Windows Users

1. Download the [Git for Windows installer](https://gitforwindows.org).
1. Run the installer, accepting all defaults.

## Cloning

1. In a Terminal, navigate to a place where you want your VM directory to reside. E.g. `cd ~/Desktop`.
1. `git clone https://github.com/Eumaeus/fall2018vm.git`.

## Running

In a terminal (`Terminal.app` on MacOS, `Git-Bash` on Windows), after navigating into `fall2018vm` using `cd`:

1. [*E.g.*] `cd ~/Desktop/fall2018vm` to navigate into the VM directory.
1. `vagrant up` starts the virtual machine. It will take a long time the first time. **Do not close the Terminal or let your computer sleep until you are back to the Unix prompt.**
1. `vagrant ssh` connects your Terminal session to the virtual machine.
1. [ Do your work, starting with `cd /vagrant/` and then `ls` to see your working files. ]
	- See below for working with EZ-Morphology
	- See below for working with FYW Tools
1. When you are done: `logout` to exit the VM.
1. `vagrant halt` to shut down the VM.

The contents of `/vagrant/` in the VM are the same as the contents of `fall2018vm` on the host (your actual computer).

## Basic Stuff

Link: [A basic introduction to the Unix command line](https://eumaeus.github.io/2018/09/07/cli.html)

## Using EZ-Morphology

### Initial Setup of EZ-Morphology

- **In your host OS:** Navigate on the command-line to the VM directory, *e.g.*: `cd ~/Desktop/fall2018vm`
- `mkdir lexdata`
- Navigate into that new directory: `cd lexdata`
- Copy the data template files to the current location: 
    - `cp ../ez-morph/data/forms-template.cex forms.cex` 
    - `cp ../ez-morph/data/lexicon-template.cex lexicon.cex`

### Using EZ-Morphology

- `vagrant up`
- `vagrant ssh`
- `cd /vagrant/ez-morph`
- `git pull` (to see if there are any updates)
- `sbt console`
- `:load tools.sc` (note the colon!)
- `betaCode()` (to confirm that everything works)

Data entry and validation cycle:

- Edit the lexicon in `/vagrant/lexData/lexicon.cex`.
- Edit forms in `/vagrant/lexData/forms.cex`.
- Use the part-of-speech generator at <http://folio.furman.edu/pos/>.
- **Validate** the data in SBT with `validate()` **or** `refresh()`.

Creating a Worksheet:

- Create a new text-file in `/vagrant/ez-morph/documents/`:
	- `cd /vagrant/ez-morph/documents`
	- `touch unit1.txt`
	- Confirm with `ls`. 
- Edit `unit1.txt` in Atom.
- In SBT, reload your data with `refresh()`.
- Generate a worksheet with `analyzeFile("unit1")`
- Look for the file `unit1.docx` in `/vagrant/ez-morph/documents/`.

### Adding data

- Your work is in `.../fall2018vm/lexdata/`
- Add lexicon entries (vocabulary) to `lexicon.cex`; edit in a text-editor (*e.g.* [Atom](Atom.io))
- Add forms (morphology) to `forms.cex`; edit in a text-editor (*e.g.* [Atom](https://atom.io))
- To validate, **in the VM**, with `sbt console` running:
	- `:load validate.sc` (note the colon)
	- `validate()`

When done…

- `:quit` (exit SBT Console; note the colon)
- `logout` (exit the VM)
- `vagrant halt` (stop the VM)

## Using FYW Tools

- `vagrant up`
- `vagrant ssh`
- **Do this only once**: Setup your own writing directory:
	- `cd /vagrant`
	- `mkdir fyw`
	- `cd fyw`
	- `mkdir writing`
	- `cd writing; mkdir output`
	- `cp ../../fyw-scala/makeDoc.sh .`
- `cd /vagrant/fys-scala`
- `git pull` (to see if there are any updates)

Add Markdown files to the `writing` directory; you can edit them in Atom on your host machine. Name them with `.md` at the end.

To get into the programming environment:

- `cd /vagrant/fyw-scala` (if you haven't already).
- `sbt console`
- To quit, `:quit` (note the colon!)


## Misc. Links

- [Pandoc](http://pandoc.org): This VM is preconfigured with Pandoc, the incredibly powerful utility for converting among different textual file formats.
- [EZ-Morph](https://github.com/Eumaeus/ez-morph): A lightweight framework for working with ancient Greek morphology. Requires [pandoc](http://pandoc.org) and [sbt](https://www.scala-sbt.org/), both of which are preconfigured in this VM.

		