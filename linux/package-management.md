Introduction to Package Managers
For Debain/Ubuntu, it is apt/dpkg and for CentOs/Redhat, it is RPM

package-managers

Question : What is the difference between CentOS, RHEL and Ubuntu*?

There are hundreds of Linux distributions in use today
One of the common ways to catagorize linux distribution is by the package manager it uses.

For example: Distributions such as RHEL, Fedora and CentOS. are based on RPM. Hence they are known as RPM based distribution. The Debian family including Ubuntu, Debian and Linux Mint e.t.c. make use of Debian based package managers such as the DPKG.
deb-rpm

Now, Lets compare RHEL and CentOS Operating Systems.
rhel-centos

What is a package?
A package in its simplest defination is a compressed archieve that contains all the files that are required by a particular software to run.
For example: Lets consider an Ubuntu System, we want to install a simple editing system such as gimp which stands for  GNU Image Manipulation System. To do this, we can make use of the gimp.deb package which contains all the software binaries and files needed to for the image editor to run along with the metadata which provides the information about the software itself.
package

Thats seems to be a quite easy process, why don't we do all the time? download a package and install it on a linux servers. Wondering the need of package managers?
There are hundreds of linux distributions are there, these distributions runs different sets of tools and libraries, software and possibly even different linux kernels as a result of this a linux program may not run the same way from one system to another. To fix this problem packages include a manifest of dependencies or list of programs in versions that must be satified for the package software to run correctly on a given computer.

Take a look at the errors in the installation while attempting to install gimp.deb on this ubuntu 18.04 system, the dependencies failed as a result the installations failed. Bare in mind that each of these dependent packages may have dependencies of their own which makes package installation management a very tedious process. This is where a Package Manager comes into save the day.

package-errors

A package manager is a software in a linux system that provides the consistent and automated process in installing, upgrading, configuring and removing packages from the operating system.
pkg-mgr

Functions of Package Manager
functions-of-pkg

Types of Package Managers
A Linux distribution supports different types of package managers, some of the common ones are below

types-of-pkg

----------------------------------------------------------------------
In this section, we will take a look at RPM and YUM package managers in detail.

RPM
YUM
RPM (Redhat Package Manager)
This package manager is used in RHEL as well as other linux distributions but these are the most common ones. The File extensions for packages manage by RPM is .RPM

rpm

Working with RPM
RPM has five basic modes of operations. Each of these modes can be run using rpm command followed by a specific command options. Despite of this, RPM doesn't resolve dependencies on its own. This is why we make use of a higher level of package manager called YUM.

Installing

Uninstalling

Upgrade

Query

Verfiying

rpm-modes

YUM (Yellowdog Updater Modifier)
YUM is a free and opensource package manager.

Works on RPM based Linux systems

Works with Software repositories which are essentially a collection of packages and provides package independency management on RPM based distro. The repository information is stored in /etc/yum.repos.d/ and repository files will have the .repo extension.

Acts as a high level package manager but under the hood it still depeneds on RPM to manage packages on the linux systems.

Unlike RPM, YUM handles package dependencies very well (Automatic Dependency Resolution). It is able to install any dependencies packages to get the base package install on the linux system.

yum

Let us see how YUM installs a package.
yum-repo

Now, lets take a look at sequence of steps envolve while installing the package.
Once yum runs yum install command is issued YUM first runs transaction check, if the package is not installed in the system yum checks the configured repositories under /etc/yum.repos.d/ for the availability of the requested package.

It also checks if there are any dependent packages are already installed in the system or if it needs to be upgrade.

yum-cmd

After this step, transaction summary is displayed on the screen for the user to review, if we wish to proceed with the install enter the y button (this step can be skipped by providing the -y flag with the yum install command).

Yum will download and install necessary RPMs to linux system

yum-cmd1

If you want to update a single package, use yum update command. If the package is already in the latest version in the repository and hence no action will be taken

yum-update

Common Commands
To list all the repos added to your system. Run yum repolist

$ yum repolist
To check which package should be installed for specific command to work. Use yum provides command followed by name.

$ yum provides scp
To Install a package

$ yum install httpd
To Install a package to automatically answer "yes" to any question prompt during the operation. Use -y flag with the yum install command.

$ yum install httpd -y
To remove a package

$ yum remove httpd
To update a package

$ yum update telnet
To update all packages in the system, use the yum update command without any arguments.

$ yum update
--------------------------------------------------------------
Which package managers would you use on centos machine

Centos makes use of RPM and YUM
Use an rpm command and find out the exact package name for wget installed in this server

$ rpm -qa |grep wget
To install a package for firefox browser that has been downloaded under /home/bob in the system. Caution: It might fail due to failed dependencies

$ sudo rpm -ivh /home/bob/firefox-68.6.0-1.el7.centos.x86_64.rpm
To install a package for firefox browser along with its dependencies

$ sudo yum install firefox -y
To check how many software repositories are configured for YUM in the system

$ sudo yum repolist
To check which package provides tcpdump command

$ sudo yum provides tcpdump
------------------------------------------------------------------------
In this section, we will look at debian package managers for distributions like Ubuntu, Debian and PureOS.

DPKG
APT
DPKG Utility
DPKG stands for Debian Package Manager
It is a low level package manager
dpkg

Working with DPKG
Similar to RPM, DPKG can be used for the below. The package extension is .deb.

Installing

Uninstalling

Upgrade

List

Status

Verfiying

dpkg-modes

APT and APT-GET
Similar to RPM, DPKG doesnt resolve the dependencies when it comes to package management.

Install may fail due to dependencies issues. This is the reason why we use higher level debian package managers such as APT and APT-GET.

dpkg-fail

Instead of relying on DPKG, you can install software along with its dependencies using APT or APT-GET.

APT or APT-GET although sounds similar, but they do not depend on each other.

APT stands for advanced package managers, it is more user friendly and overall better tool compared to APT-GET.

$sudo apt install gimp
$sudo apt-get install gimp
APT act as a frontend package manager that relies on DPKG utility. In similar to YUM, APT relies on software repository that contains packages that would eventually be installed on a system.

The software repository for APT is defined in /etc/apt/sources.list file.

apt

Let us know see some common commands
To refresh a repository. Run apt update command.

$ sudo apt update
To install available upgrades of all packages currently installed on the system from the sources configured.

$ sudo apt upgrade
Another way to update the repository is to use apt edit-sources command. This opens up the /etc/apt/sources.list file in the text editor of your choice.

$ sudo apt edit-sources
To install the package

$ sudo apt install telnet
To remove the package

$ sudo apt remove telnet
To search or look for a package in the repository.

$ sudo apt search telnet 
To list all the available packages

$ sudo apt list |grep telnet
------------------------------------------------------------------


Difference between APT vs APT-GET
APT is a more user friendly tool when compared to APT-GET
In all the latest debian based distros APT is already installed by default.
Lets take a look why APT is better when compare to APT-GET
Lets try to install firefox package using both APT and APT-GET

You will notice APT does easy on the eyes, you get just enough information and also a nice little progress bar

APT-GET is just effective and doesn't provide the output in user-friendly format.

apt-vs-apt-get

Lets try another comparision by search a telent package.

You will notice with apt, all its options are located in one place. You can search with apt search telnet command.

On the other hand, you cannot use search command with apt-get command. Instead, you have to use another tool called apt-cache search telnet.

If you compare the results of the two commands, you will also see the apt-cache throws in a lot of extra information in the search result, which may not be really useful for the end user.

apt-vs-apt-get1

------------------------------------------------------------------------
Package managers that you use on a debian based distro

Debain distros use dpkg.
To install a package for firefox browser which has been downloaded at /root/firefox.deb. The dependencies might fail.

$ sudo dpkg -i /root/firefox.deb
To install a package using APT

$ sudo apt install firefox
Lets now locate the package to install Chromium browser in the system. Use apt search functionality to locate the correct package name. The browser has the description of: Chromium web browser, open-source version of Chrome

$ sudo apt search chromium-browser
To install the chromium-browser

sudo apt install -y chromium-browser
To remove the firefox browser from the system.

$ sudo apt remove firefox
--------------------------------------------------------------------


