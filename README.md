<style>
.boxed {
  background: lightgrey;
  border: 5px dashed black;
  margin: 0px auto;
  width: 2em;
  padding: 1em;
  border-radius: 4em;
}
</style>

<!-- Tutorial URL: https://www.tutorialspoint.com/apache_storm/index.htm  -->
# Apache Storm Tutorial
Apache Storm is a data-processing system that analyzes real-time data. The following tutorial and guide will help explain and demostrate the capabilities of this system.

[Original Tutoral](https://www.tutorialspoint.com/apache_storm/index.htm)

----
## Quick Guide
### Base Terms:
- ***Fault Tolerant***: Ability of a system to continue operating without interruption when one or more of its components fail.<sup>[[1]](#faultTolerant)</sup>
- ***Real-Time Stream Processing***: Process of taking action on data at the time the data is generated or published.<sup>[[2]](#realTime)</sup>
- ***Operational Intelligence***: A data analytics philosophy that implements quick buisness decisions based on real-time data.<sup>[[3]](#operational)</sup>

### What is Storm?
***Apache Storm*** is a distributed real-time big data-processing system. 

- Processes ***fault-tolerant*** and ***horizontal scalable*** data
- Stateless system, however
  - Manages distributed enviroment and cluster state via ***Apache ZooKeeper***
- System guarentees every message with be processed through the topology ***at least*** once

### Benefits of Apache Storm
- Storm is ***open source***, ***robust***, and ***user friendly***
- Storm is ***fault tolerant***, ***flexible***, ***reliable***, and supports ***any*** programming language
- Permits real-time stream processing
- Extreamly fast data processing
- Maintains performance by adding resources linearly
  - Highly scaleable
- Utilizes Operational Intelligence
- Guarenteed data processing irregardless of nodes dieing or messages being lost

### Components of Apache Storm
Storm reads raw streams of real-time data and passes it through a series of small process unites to output processed / useful information. To understand how, both, Storm functions and processes its data, we must comprehend the individual components utilized:

* ***Tuple***: Also known as Storm's main data structure, it is a ***<u>ordered</u>*** list of elements that is modeled (displayed as) a set of comma-seperated values.
* ***Stream***: An ***<u>unordered</u>*** sequence of tuples.
* ***Spouts***: The source of the stream; typically can be fed raw data. Otherwise, spouts can be used to read data from data sources.
* ***Bolts***: Logical processing units that process and produce a new output stream.
* ***Topology***: The combination of both processing units (spouts & bolt). Please see [Topology]() for more information.

  ***Directed Graph***
  <div class="boxed">
    ***Verticies*** == ***Computation***
    ***Edges*** = ***Streams of data***
  </div>

----
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

## Footnotes
<a name="faultTolerant">[1]</a>: Definition grabbed from [imperva.com](https://www.imperva.com/learn/availability/fault-tolerance/)

<a name="realTime">[2]</a>: Definition grabbed from [hazelcast.com](https://hazelcast.com/glossary/real-time-stream-processing/)

<a name="operational">[3]</a>: Definition grabbed from [sisense.com](https://www.sisense.com/glossary/operational-intelligence/)