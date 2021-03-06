# PyLizard Gradle Plugin
[ ![Download](https://api.bintray.com/packages/amnl/gradle/gradle-pylizard/images/download.svg) ](https://bintray.com/amnl/gradle/gradle-pylizard/_latestVersion)
[ ![MIT License](http://img.shields.io/badge/license-MIT-blue.svg?style=flat-square) ](https://github.com/itavero/gradle-pylizard/blob/master/LICENSE)
[ ![Build Status](http://img.shields.io/travis/itavero/gradle-pylizard.svg?style=flat-square) ](https://travis-ci.org/itavero/gradle-pylizard)
[ ![Test Code Coverage](http://img.shields.io/codecov/c/github/itavero/gradle-pylizard.svg?style=flat-square) ](https://codecov.io/github/itavero/gradle-pylizard)
[ ![Issues](http://img.shields.io/github/issues/itavero/gradle-pylizard.svg?style=flat-square) ](https://github.com/itavero/gradle-pylizard/issues)

Adds tasks for running the [Lizard code complexity](http://www.lizard.ws/) tool from Gradle.

## Requirements
To use this plugin you need to have Python and Lizard installed.
```bash
# Install PIP if you don't have it already
python < <(curl -s https://bootstrap.pypa.io/get-pip.py)

# Install Lizard using PIP
pip install lizard
```

## Configuration
Just add the plugin to your `build.gradle` and your good to go.
Installation instructions can be found on [plugins.gradle.org](http://plugins.gradle.org/plugin/amnl.pylizard).

If no directories or source sets are configured, the plugin adds the `src` directory by default.
However, if you do wish to configure Lizard, have a look at the example below.

```groovy
lizard {
    // Path where lizard.xml is stored
    // Relative to your projects build directory
    reportsDir = "reports"
    
    // The paths you wish to include
    // These are relative to your project folder
    includes = ["src"]
   
    // The paths you wish to exclude
    // These are relative to your project folder
    excludes = ["src/test/*"]
    
    // Simply add some SourceSet instances if you want
    sourceSets = [android.sourceSets.main, android.sourceSets.debug]
    
    // Set the number of threads Lizard may use
    // This defaults to the number of available processors found by the JVM
    numberOfThreads = 2
}
```

Please note, that I have not explicitly verified these examples, but I am pretty confident that they should work.

## Usage
The plug-in adds two tasks:
+ `lizardVersion` simply runs Lizard and shows you which version is installed.
+ `lizard` calls Lizard with arguments based on your Gradle configuration.

If your projects has a `check` task, the plug-in adds a dependency for the `lizard` task to it.

## Found a bug? Got a cool suggestion?
Let me know by creating an issue or, even better, fork this repository and DIY!
I'm always willing to accept a Pull-Request, if the code is written nicely and it is tested.