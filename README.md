# Minecraft Modding Tutorial
A Minecraft modding tutorial for use on a locked down Windows machine.

We're going to try and set up a development environment on a locked down Windows machine. This tutorial has been tested on Windows 10, but should work on earlier versions too.

We're using *portable versions* of the Java Development Kit and Eclipse so that we can work on machines without needing administrative access, or installing anything on to the computer, for example in a school environment.

Folder paths below are arbitrary, but if you use the defaults, it will mean the steps are easier to follow.

Some of the downloads below depend on whether you're running 32 or 64 bit Windows - to find out which you're using, go to http://windows.microsoft.com/en-NZ/windows7/find-out-32-or-64-bit.

# Setting up our Development Environment

## What do we need to download?

*A copy of all the downloaded files can also be downloaded at https://mega.nz/#F!7h8jGKyQ!mhnwCgWJjzuY-bvKGCng0Q.*

### 7-Zip (portable edition)
- Browse to http://portableapps.com/apps/utilities/7-zip_portable
- Download, and run **7-ZipPortable_15.14.paf.exe**, which will extract into a folder. Accept the default (````C:\Users\<username>\Downloads\7-ZipPortable````)

### Git (portable edition)
- Browse to https://git-scm.com/download/win
- Download, and run **PortableGit-2.8.0-32-bit.7z.exe** or **PortableGit-2.8.0-64-bit.7z.exe**, which will extract into a folder. Accept the default (````C:\Users\<username>\Downloads\PortableGit````).

### The Java Development Kit 8 (JDK)
- This one is a bit involved, as we're going to take a normal JDK download, and create a portable version out of it.
- Browse to http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html
- Click **Accept License Agreement**
- Download the Java SE Development Kit 8u77 for your operating system - probably **jdk-8u77-windows-i586.exe** or **jdk-8u77-windows-x64.exe**.
- ***Don't run this file!***
- Open 7-Zip portable, and navigate to the ````jdk-8u77-windows-xxxxx.exe```` download. **Right click** and choose **7-zip->Open archive**.
- A new archive will appear, containing the file ````tools.zip````. Right click that file and choose **Open**.
- A new archive will appear, containing a number of directories and files. Press **Ctrl-A** to select all, and then click the Blue Extract tool. Specify ````c:\Users\<username>\Downloads\jdk````.
- We need to unpack some of the files using the command prompt.
  - Navigate to this new ````Downloads\jdk```` folder in Windows Explorer, and **Shift-Right click**, and select **Open command window here**.
  - In the command prompt, type the following lines and press <Enter> after each one.
    - ````for /r %x in (*.pack) do .\bin\unpack200 -r "%x" "%~dx%~px%~nx.jar````
    - ````bin\javac -version````
  - You should see something like the following:

````
C:\Users\coderdojo\Downloads\jdk>for /r %x in (*.pack) do .\bin\unpack200 -r "%x" "%~dx%~px%~nx.jar
C:\Users\coderdojo\Downloads\jdk>.\bin\unpack200 -r "C:\Users\coderdojo\Downloads\jdk\jre\lib\charsets.pack" "C:\Users\coderdojo\Downloads\jdk\jre\lib\charsets.jar
C:\Users\coderdojo\Downloads\jdk>.\bin\unpack200 -r "C:\Users\coderdojo\Downloads\jdk\jre\lib\deploy.pack" "C:\Users\coderdojo\Downloads\jdk\jre\lib\deploy.jar
...
...
C:\Users\coderdojo\Downloads\jdk>.\bin\unpack200 -r "C:\Users\coderdojo\Downloads\jdk\lib\tools.pack" "C:\Users\coderdojo\Downloads\jdk\lib\tools.jar
C:\Users\coderdojo\Downloads\jdk>bin\javac -version
javac 1.8.0_77

````

### Eclipse Classic Version 4.4 Portable Edition
- Browse to https://sourceforge.net/projects/eclipseportable/ and Download **EclipsePortable_4.4_Classic_Edition.paf.exe**
- Run the file, and extract into a folder. Accept the default (````C:\Users\<username>\Downloads\EclipsePortable````)
- Copy all files and folders from the **Downloads\jdk** folder to the **Downloads\EclipsePortable\App\Java**

### Minecraftforge
- Browse to http://files.minecraftforge.net/ and download the **Recommended MDK** file.
- **WARNING** There are annoying adverts on this download site - don't download anything other than the forge-xxxxx-mdk.zip file - look for a **SKIP** button, and ignore any adverts.
- Unzip the downloaded ````forge-1.8.9-11.15.1.1722-mdk.zip```` file to ````C:\Users\<username>\Downloads\forge````.
- In Windows Explorer, navigate to the new ````Downloads\forge```` directory, and again, hold down **Shift**, and **right click**, then select "Open command window here".
- Type the following:
  - ````PATH="%PATH%";"%USERPROFILE%\Downloads\EclipsePortable\App\Java\bin"````
  - ````gradlew setupDecompWorkspace --refresh-dependencies````
    - Might take 5-15 minutes
  - ````gradlew eclipse````


### Start Eclipse
- Browse to **EclipsePortable** folder, and start **EclipsePortable.exe**.
- When asked to choose a workspace, browse to eclipse folder in MDK download folder, e.g. ````C:\Users\<username>\Downloads\forge\eclipse````
- If not prompted to choose a workspace, go to **File->Switch Workspace... -> Other**.
- Select the MDKExample folder in the left hand pane.
- Click the Green Run button, or press **Ctrl-F11**.

# Let's start MODDING (well almost)
### WOW - you've got further than we have!
- You're ready to start creating a mod - but we haven't got that far here yet - check back in coming weeks for updates, or send us a pull request with some notes yourself!
- In the meantime, here are some additional resources for the next steps:
  - [Wuppy's modding tutorials on YouTube](https://www.youtube.com/user/wuppygaming/videos)
  - [MinecraftForge's Basic Modding tutorial](http://www.minecraftforge.net/wiki/Basic_Modding)

## Sources
- Tutorial video: https://www.youtube.com/watch?v=VhOSL7rGb10
- http://www.minecraftforge.net/wiki/Installation/Source
- http://mcforge.readthedocs.org/en/latest/gettingstarted/

## Troubleshooting
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
- Add ````org.gradle.jvmargs=-Xmx2G```` to **c:\users\<Username>\.gradle\gradle.properties** (create the file if it doesn't exist) to allocate more RAM to Gradle.
  - Alternatives if not enough memory:
  - ````org.gradle.jvmargs=-Xmx1500M````

### Eclipse run/debug error

````
Launching Client has encountered a problem.
Variable references empty selection: ${project_loc}
````
- Make sure you’ve got the project selected in the Package Explorer pane on the left.
