# Fix Gradle

### Fix Project Name

The original Udacity code does not set the project name for Gradle.
This makes Gradle use the current folder name as project name, which, by
default, contains characters that are deprecated and will be disallowed:

```
$ gradle build
The project name 'Project 1 - TicTacToe' contains at least one of the following characters: [ , /, \, :, <, >, ", ?, *, |].
This has been deprecated and is scheduled to be removed in Gradle 5.0.
Set the 'rootProject.name' or adjust the 'include' statement (see https://docs.gradle.org/4.4.1/dsl/org.gradle.api.initialization.Settings.html#org.gradle.api.initialization.Settings:include(java.lang.String[]) for more details).
```


To resolve this, either rename your project directory or create file named ```settings.gradle```, and put the following line into it:
```
rootProject.name = "TicTacToe"
```


Now our build should complete without warnings:
```
$ gradle build

> Task :test 

com.udacity.GameTest > no_winner_case1 PASSED

(...)
----------------------------------------------------------------------
|  Results: SUCCESS (23 tests, 23 successes, 0 failures, 0 skipped)  |
----------------------------------------------------------------------

BUILD SUCCESSFUL in 0s
```


### Add Missing Entry Point for Java Program

The default ```build.gradle``` that comes with the project does not contain the application entry point.
This means that running our game alone (without IntelliJ) is problematic:

```
8 actionable tasks: 8 executed
$ java -jar build/libs/TicTacToe.jar 
no main manifest attribute, in build/libs/TicTacToe.jar
```

 Let's fix that!

1. Open ```build.gradle``` in IntelliJ
1. Add the following section to it:
    ```
    jar {
        manifest {
            attributes(
                    'Main-Class': "${mainClassName}"
            )
        }
    }
    ```

Your build.gradle should look like this:

```
apply plugin: 'java'
apply plugin: 'application'

mainClassName = "com.udacity.Game"

repositories {
    mavenCentral()
}

dependencies {
    testCompile group: 'junit', name: 'junit', version: '4.+'
}

jar {
    manifest {
        attributes(
                'Main-Class': "${mainClassName}"
        )
    }
}
```


Now you should be able to run your program from command line:
```
$ gradle build
(...)
$ java -jar build/libs/TicTacToe.jar 
```

