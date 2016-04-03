# Troubleshooting
## Development Environment Setup
### JDK Unpacking issues
If you see the following issue whilst unpacking the jdk, check the version of the jdk you downloaded matches your operating system.

````
This version of C:\Users\coderdojo\Downloads\jdk\jre\bin\unpack200.exe is not compatible with the version of Windows you're running. Check your computer's system information and then contact the software publisher.
````

### Memory issues

````
GC overhead limit exceeded
Execution failed for task ':decompileMc'.
> GC overhead limit exceeded

C:\Users\Administrator\Desktop\Minecraft>gradlew setupDecompWorkspace --refresh-
dependencies
This mapping 'stable_20' was designed for MC 1.8.8! Use at your own peril.
#################################################
         ForgeGradle 2.1-SNAPSHOT-9e8f067
  https://github.com/MinecraftForge/ForgeGradle
#################################################
               Powered by MCP unknown
             http://modcoderpack.com
         by: Searge, ProfMobius, Fesh0r,
         R4wk, ZeuX, IngisKahn, bspkrs
#################################################
:deobfCompileDummyTask
:deobfProvidedDummyTask
:getVersionJson
:extractUserdev UP-TO-DATE
:extractDependencyATs SKIPPED
:extractMcpData SKIPPED
:extractMcpMappings SKIPPED
:genSrgs SKIPPED
:downloadClient SKIPPED
:downloadServer SKIPPED
:splitServerJar SKIPPED
:mergeJars SKIPPED
:deobfMcSRG SKIPPED
:decompileMc FAILED

FAILURE: Build failed with an exception.

* What went wrong:
Execution failed for task ':decompileMc'.
> GC overhead limit exceeded

* Try:
Run with --stacktrace option to get the stack trace. Run with --info or --debug
option to get more log output.

BUILD FAILED

Total time: 4 mins 53.467 secs

C:\Users\Administrator\Desktop\Minecraft>
````


### Java heap space issue
#### What happened?

````
Applying SpecialSource...
Applying Exceptor...
:decompileMc FAILED

FAILURE: Build failed with an exception.

* What went wrong:
Execution failed for task ':decompileMc'.
> Java heap space

* Try:
Run with --stacktrace option to get the stack trace. Run with --info or --debug option to get more log output.

BUILD FAILED

Total time: 3 mins 53.98 secs
````
#### What caused it?
Java ran out of memory trying to perform the gradlew task.

#### How do we fix it?
Give Java more memory! :-)
- Add the following line to **%USERNAME%\\.gradle\\gradle.properties** (create the file if it doesn't exist) to allocate more RAM to Gradle. Here we're giving it 2GB.
  - ````org.gradle.jvmargs=-Xmx2G````
  - If you get an error about running out of memory, try one of these options - 1.5GB or 1GB:
  - ````org.gradle.jvmargs=-Xmx1500M````
  - ````org.gradle.jvmargs=-Xmx1000M````

### Eclipse run/debug error

````
Launching Client has encountered a problem.
Variable references empty selection: ${project_loc}
````
#### How do we fix it?
- Make sure you’ve got the project selected in the Package Explorer pane on the left. (Eclipse is stupid sometimes.)
