# Useful Coursier Commands

Refer to the [official documentation](https://get-coursier.io/docs/cli-installation.html#native-launcher) for more details.

## JVM Setup Commands ##

Command | Description
--- | ---
./cs setup | Initial setup with default applications |
cs java --jvm 11 | Download/Install AdoptOpenJDK 11
cs java --jvm 11 --setup | Downlaod/Install AdoptOpenJDK 11 and set as default
cs java --jvm 11 --env | Download/Install AdoptOpenJDK 11 and print the export env statements
cs java --available | List all supported JVMs
cs java --installed | List all installed JVMs
cs java --jvm graalvm:20.0.0 --setup | Install and setup GraalVM 20.0.0 as the default version

