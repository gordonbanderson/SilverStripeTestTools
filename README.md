# SilverStripe Testing and Continuous Integration Tools
## Maintainers

* Gordon Anderson (Nickname: nontgor)
	<gordon.b.anderson@gmail.com>

##Introduction

This project contains a couple of Ruby scripts to get up and running with testing
and continuous integration with SilverStripe quickly.  It is intended for
modules lacking any kind of testing.

##Installation
* Install Ruby on your system if it is not already available.
* Clone this project and copy addnewciSS and maketests into the system path.
 
```
git clone https://github.com/gordonbanderson/SilverStripeTestTools.git sstools
cd sstools
cp addnewciSS ~/bin
cp maketests ~/bin
chmod 700 ~/bin/addnewciSS
chmod 700 ~/bin/maketests
```

Note that Badger must also be installed, see
https://github.com/gordonbanderson/Badger

##Usage
Please note that both of the following scripts are destructive, and that your
code should be backed up on GitHub prior to running them.

###Create a Skeleton Test Suite
Running the command `maketests <module_name>` from the root of your SilverStripe
install will add a test marked as skipped for every function grepped out of the
non test codebase.  It's not 100% perfect, so check for any syntax errors in the
tests by running `php -l <module_name>/tests/*.php`

###Add Continous Integration
Running the command `cd <module_path> && addnewciSS` will do the following:
* Add a .travis.yml file ready for integration with Travis
* Add a .scrutinizer file, ready for integration with Scrutinizer
* Add a .editorconfig and .gitattributes file
* Add badges to the README file suitable for the master branch
* Echo instructions how to enable continous integration for both Scrutinizer and
Travis for the module in question.
All of these changes are made on a branch called continuousintegration.  Changes
can then be applied by merging into the master branch, cherry-picking relevant
commits, or rebasing the continousintegration branch prior to merging.