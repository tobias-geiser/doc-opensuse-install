# Partitions

4GB EFI
~GB OS

# Full Disk Encryption

# Install Rescue System

# Configure Zypper

Change installRecommens to "no"

```
[solver]

## Install soft dependencies (recommended packages)
##
## CAUTION: The system wide default for all libzypp based applications (zypper,
## yast, pk,..) is defined in  /etc/zypp/zypp.conf(solver.onlyRequires)  and it
## will per default install recommended packages. It is NOT RECOMMENDED to define
## this value here for zypper exclusively, unless you are very certain that you
## want zypper to behave different than other libzypp based packagemanagement software
## on your system.
##
## Valid values: boolean
## Default value: follow zypp.conf(solver.onlyRequires)
##
installRecommends = no
```


# Install Packages

```
sudo zypper in git
```
