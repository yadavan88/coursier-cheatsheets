# Useful Coursier Commands - Cheatsheet

Coursier is a very useful tool for any Scala Developers. From installing JVMs and REPLs to identifying the transitive dependencies of libraries, I use it very often. 

Refer to the [official documentation](https://get-coursier.io/docs/cli-installation.html#native-launcher) for more details.

## Coursier Commands ##

Command | Description
--- | ---
cs list | List all installed applications
cs install scala | Install default Scala REPL
cs install ammonite | Install ammonite REPL
cs uninstall scala | Uninstall scala REPL
cs uninstall --all | Uninstall all apps installed by cs
cs update scala | Update Scala REPL to latest version

## JVM Setup Commands ##

**Note: Most of the times, simply restarting the terminal is enough to relfect the jvm(path changes). But sometimes, it is required to logout and login back to reflect it.**

Command | Description
--- | ---
./cs setup | Initial setup with default applications |
cs java --jvm 11 | Download/Install AdoptOpenJDK 11
cs java --jvm 11 --setup | Downlaod/Install AdoptOpenJDK 11 and set as default
cs java --jvm 11 --env | Download/Install AdoptOpenJDK 11 and print the export env statements
cs java --available | List all supported JVMs
cs java --installed | List all installed JVMs
cs java --jvm graalvm:20.0.0 --setup | Install and setup GraalVM 20.0.0 as the default version

## Scala Related Commands ##

Command | Description
--- | ---
cs install scala | Install latest Scala REPL
cs install scala:2.12.12 | Install Scala 2.12.12 REPL
cs launch scala:2.12.13 | Launches Scala REPL 2.12.13, but will NOT set as default REPL
cs launch scala --jvm 11 | Launch Scala REPL with JVM as AdoptOpenJDK 11
cs launch scala:2.13.4 --jvm 11 | Launch Scala REPL for version 2.13.4, and using JDK 11
cs launch ammonite --jvm 14 | Launch ammonite REPL with default Scala Version and using JVM version 14

## Artifacts related ##

Command | Description
--- | ---
cs complete com.typesafe.akka: | List all artifacts under com.typesafe.akka
cs complete com.typesafe.akka.akka-actor_ | List all artifacts for akka-actor for all scala versions
cs resolve com.typesafe.akka::akka-actor:2.6.14 | List all the transitive dependencies of akka-actor
cs resolve com.typesafe.akka::akka-actor:2.6.14 -t | List all the transitive dependencies of akka-actor in tree structure
cs fetch com.typesafe.akka::akka-actor:2.6.14 | Download the jar files for akka-actor



