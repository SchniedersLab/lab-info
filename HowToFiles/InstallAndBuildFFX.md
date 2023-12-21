# Install and Build Force Field X

## Install
Instructions for installing Force Field X on Linux, Mac OS X and Microsoft Windows are given below. For all operating systems, the Java Runtime Environment must be present.

## Prerequisite: Install Java
Please install version 10 or later of the Java Runtime Environment from [Oracle](https://www.oracle.com/java/technologies/downloads/). Detailed Java installation instructions for [Linux, Mac OS, and Microsoft Windows are available](https://docs.oracle.com/en/java/javase/16/install/overview-jdk-installation.html#GUID-8677A77F-231A-40F7-98B9-1FD0B48C346A).

## Clone Force Field X
To clone the Force Field X source using GIT:
    `git clone git@github.com:SchniedersLab/forcefieldx.git forcefieldx`

In the future, your clone of Force Field X can be updated to the latest version using the command:
    `git pull origin master`

Updates that have been pushed to SchniedersLab can be obtained with the following commands:
    `git remote add SchniedersLab https://github.com/SchniedersLab/forcefieldx.git` (Remote repository only needs to be added once)
    `git fetch SchniedersLab`
    `git pull SchniedersLab master`

## Build Using Maven
A Maven project file (pom.xml) is provided to build Force Field X on any platform. After cloing the Force Field X git repository, change directoies into the base project directory. Then execute:
    `mvn`

This requires Maven v. 3.2 or later to be installed with its bin directory included in your $PATH environment variable. The first time this command is executed, Maven will download build dependencies and Force Field X runtime dependecies. Future executions are quicker. Force Field X will self-test its modules and report failures. Only code that passes all testing should be pushed to the GitHub repository, so if any test fails it may be due to a local configuration issue. To execute the tests:
    `mvn -DskipTests=false`

Additional tests, ordinarily skipped due to length of running them (~15 minutes on a single core of a 2013 CPU) can be accessed via the **ffx.ci** property, as such:
    `mvn -DskipTests=false -**Dffx.ci**=true`

Currently, JDKs 1.8, 9, 10, 11, and 12 are supported. After installing a supported JDK, point the JAVA_HOME environment variable to the JDK directory, and then add the JDK bin directory to your path.

## Execute Force Field X
Once the Maven build succeeds, Force Field X can be executed using platform dependent start-up scripts located in the bin. On Mac OS X or Linux:
    `bin/ffxc Energy examples/alamet.xyz`
On Windows:
    `bin/ffxc.bat Energy examples/alamet.xyz`
The ffx/bin directory should be appended to your $PATH environment variable. The "Energy" command refers to an internal version of the Energy.groovy script that can be found in the ffx/scripts directory. To embed your own script within FFX, place it into the scripts directory and rebuild FFX.
