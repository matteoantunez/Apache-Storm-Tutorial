<!-- Tutorial URL: https://www.tutorialspoint.com/apache_storm/index.htm  -->
# Apache Storm Tutorial
Apache Storm is a Big Data Processing Framwork that allows users to analyze real-time data. This tutorial will be used for Mac users and help with the installation and utilization of this framework. 

[Original Tutoral](https://www.tutorialspoint.com/apache_storm/index.htm)

## Quick Guide

## Installation
Before we can begin to install Apache Storm, we need to make sure the following items are installed on our device:

1. Java
2. Zookeeper

For this part of the Tutorial, I will be using Homebrew and the assistance of [this](https://www.javahabit.com/2015/12/26/how-to-set-up-apache-storm-on-mac-using-brew/) article.

### Step 1: Verify Homebrew is Installed
Before starting, we must verify homebrew is installed on our device. Run the following code and analyze the output:

```Terminal
% which brew
```

Running the above code will give two possible outcomes:

* The location of the install
* "Brew not found"

If you aren't given the location of the install, follow the next set of steps.

#### Step 1.1: Install Homebrew
Running the following code will install Homebrew to your local device:

```Terminal
% /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

Homebrew is similar to Git Bash on Windows, to where it can be use to download software directly from Github repositories. This will allow an easy way to install and update our programs.

#### Step 1.2: Install Homebrew Cask
Use the following code to install and update Homebrew Cask

```Terminal
% brew tap homebrew/cask-versions
% brew update
% brew tap homebrew/cask
```

Homebrew Cask is used in conjuction with Homebrew to install all macOS assets needed for applications.

### Step 2: Verify Java is Installed
Before we can continue, we need to veify Java is installed on our device. To do this, open Terminal and enter the following piece of code:

```Terminal
% java --version
```

If you are able to locate your Java version number, Java is installed and your device is ready for Step 2. If you are unable to verify Java is installed, please follow the following steps.

<i>Note:</i> The following Java installation can be found at [this](https://devqa.io/brew-install-java/) link.

#### Step 2.1: Installing Java using Homebrew
To install Java, run the following code using Hombrew in Terminal:

```Terminal
% brew install java
```

Due to Java having some compatabilitiy issues with macOS, you may get the following ouptut after the download and install is complete.

```Terminal
openjdk is keg-only, which means it was not symlinked into /opt/homebrew,
because macOS provides similar software and installing this software in
parallel can cause all kinds of trouble.

If you need to have openjdk first in your PATH, run:
  echo 'export PATH="/opt/homebrew/opt/openjdk/bin:$PATH"' >> ~/.zshrc

For compilers to find openjdk you may need to set:
  export CPPFLAGS="-I/opt/homebrew/opt/openjdk/include"
```

#### Step 2.2: Set openJDK first in your PATH
To ensure openJDK is always used, run the following code to ensure it is the first file in your path 

```Terminal
% echo 'export PATH="/opt/homebrew/opt/openjdk/bin:$PATH"' >> ~/.zshrc
```

#### Step 2.3: Set Compilers to find openJDK
Before our compilers can use openJDK, we must link them using the following code:

```Terminal
% export CPPFLAGS="-I/opt/homebrew/opt/openjdk/include"
```

#### Step 2.4: Link JDK Install to Additional Location:
Since our Java install is "keg-only", we must run the following code to allow the creation of a symoblic link to another file location:

```Terminal
% sudo ln -sfn /usr/local/opt/openjdk/libexec/openjdk.jdk /Library/Java/JavaVirtualMachines/openjdk.jdk
```

[Source](https://mkyong.com/java/how-to-install-java-on-mac-osx/)

### Step 2: Verify Java 