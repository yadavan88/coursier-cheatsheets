# Useful Coursier Commands - Cheatsheet

Coursier is a very useful tool for any Scala Developers. From installing JVMs and REPLs to identifying the transitive dependencies of libraries, I use it very often. 

Refer to the [official documentation](https://get-coursier.io/docs/cli-installation.html#native-launcher) for more details. You can also refer to my [Baeldung article](https://www.baeldung.com/scala/coursier-env-setup) which briefly explains coursier.

Coursier is used by [Scala-CLI](https://yadukrishnan.live/scala-made-simple-for-beginners-a-gentle-introduction-to-kickstarting-your-scala-learning) under the hood. I have also created a [Scala-CLI cheatsheet](https://github.com/yadavan88/ScalaCLI-Cheatsheet).

## Coursier Commands ##

Command | Description
--- | ---
cs list | List all installed applications
cs update | Update coursier and all apps
cs install scala | Install default Scala REPL
cs install ammonite | Install ammonite REPL
cs uninstall scala | Uninstall scala REPL
cs uninstall --all | Uninstall all apps installed by cs
cs update scala | Update Scala REPL to latest version

## JVM Setup Commands ##

**Note: Most of the times, simply restarting the terminal is enough to relfect the jvm(path changes). But sometimes, it is required to logout and login back to reflect it.**


_**Note:** Recently, coursier changed the default JDK for ARM based machines. In Mac ARM, it uses Zulu by default, in Windows ARM liberica JDK is used. In others, it uses Temurin._

Command | Description
--- | ---
./cs setup | Initial setup with default applications |
cs java --jvm 11 | Download/Install default JDK(based on arch) 11
cs java --jvm 11 --setup | Downlaod/Install default JDK(based on arch) 11 and set as default
cs java --jvm 11 --env | Download/Install default JDK(based on arch) 11 and print the export env statements
cs java --available | List all supported JVMs
cs java --installed | List all installed JVMs
cs java --jvm graalvm:20.0.0 --setup | Install and setup GraalVM 20.0.0 as the default version

## Scala Related Commands ##

Command | Description
--- | ---
cs install scala | Install latest Scala REPL
cs install scala:2.12.12 | Install Scala 2.12.12 REPL
cs launch scala:2.12.13 | Launches Scala REPL 2.12.13, but will NOT set as default REPL
cs launch scala --jvm 11 | Launch Scala REPL with JVM as JDK 11
cs launch scala:2.13.4 --jvm 11 | Launch Scala REPL for version 2.13.4, and using JDK 11
cs launch ammonite --jvm 14 | Launch ammonite REPL with default Scala Version and using JVM version 14
cs install zookeeper --contrib | Install apps from contrib section

## Artifacts related ##

Command | Description
--- | ---
cs complete com.typesafe.akka: | List all artifacts under com.typesafe.akka
cs complete com.typesafe.akka.akka-actor_ | List all artifacts for akka-actor for all scala versions
cs resolve com.typesafe.akka::akka-actor:2.6.14 | List all the transitive dependencies of akka-actor
cs resolve com.typesafe.akka::akka-actor:2.6.14 -t | List all the transitive dependencies of akka-actor in tree structure
cs fetch com.typesafe.akka::akka-actor:2.6.14 | Download the jar files for akka-actor


## How to distribute custom apps using Coursier? ##

- Publish the custom apps to a central location, for e.g: local artifactory
- Credentials for the artifactory/repository may be configured using [credentials.properties](https://get-coursier.io/docs/other-credentials)
- Package the application and create a launcher using the bootstrap command:
  - cs bootstrap -r https://central_repo/repository groupId:artifactId:version -o app_name
- Create a [descriptor](https://get-coursier.io/docs/cli-install.html#create-an-application-descriptor) and publish it to a central location.
- Install using the cs install command:
  - cs install --channel https://app.descriptor.com/app_name.json app_name
