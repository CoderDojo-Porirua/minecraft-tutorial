
# Development Environment Setup

A development environment is a set of tools we use to develop and debug software. We could do much of this without one, but a development environment will make these tasks easier.

- The *Java Development Kit* is the *software development kit* we're going to use to build our mods. It give us a bunch of tools to develop using *Java*, the language Minecraft is programmed in.
- *Eclipse* is the  *integrated development environment* we're going to use to helps us build and debug the software.
- MinecraftForge is a set of libraries and package we use to build the mods for Minecraft, using Eclipse and the JDK.

We're going to try and set up a development environment on a locked down Windows machine - that's a machine running Windows, for which we don't have administrative access (like your school's computers). We're using *portable versions* of the Java Development Kit and Eclipse so that we can work on machines without needing to install anything on to the computer. If you have your own Windows computer, you can still follow this tutorial and it will work.

If you have a Linux or Mac computer, the steps are slightly different, and are (or will be) listed [here](dev-environment-setup-linux-mac.md).

. This tutorial has been tested on Windows 10, but should work on earlier versions too.


Folder paths below are arbitrary, but if you use the defaults, it will mean the steps are easier to follow.

Some of the downloads below depend on whether you're running 32 or 64 bit Windows - to find out which you're using, go to these links for [Windows Xp/7](http://windows.microsoft.com/en-NZ/windows7/find-out-32-or-64-bit), and [Windows 10](http://www.tenforums.com/tutorials/4399-system-type-32-bit-x86-64-bit-x64-windows-10-a.html).

- 32 bit is usually be listed as 32 bit, x86, or i586.
- 64 bit will usually be listed as x64.

When you see ````%USERPROFILE%\```` below this actually means your home directory, e.g. ````c:\users\coderdojo\````. If you type it into Windows Explorer, it will automatically be changed to your own home directory.

# Setting up our Development Environment

## What do we need to download?

*A copy of all the downloaded files can also be downloaded at https://mega.nz/#F!7h8jGKyQ!mhnwCgWJjzuY-bvKGCng0Q.*

### 7-Zip (portable edition)
- Browse to http://portableapps.com/apps/utilities/7-zip_portable
- *Make sure you don't download anything other than* ***Download Now sourceforge*** *link.*
- Download, and run **7-ZipPortable_15.14.paf.exe**, which will extract into a folder. Accept the default (````%USERPROFILE%\Downloads\7-ZipPortable````)

### Git (portable edition)
- Browse to https://git-scm.com/download/win
- Download, and run **PortableGit-2.8.0-32-bit.7z.exe** or **PortableGit-2.8.0-64-bit.7z.exe**, which will extract into a folder. Accept the default (````%USERNAME%\Downloads\PortableGit````).

### The Java Development Kit 8 (JDK)
- This one is a bit involved, as we're going to take a normal JDK download, and create a portable version out of it.
- Browse to http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html
- Click **Accept License Agreement**
- Download the Java SE Development Kit 8u77 for your operating system - probably **jdk-8u77-windows-i586.exe** or **jdk-8u77-windows-x64.exe**. (Don't download the demo and sample files.)
- ***Don't run this file!***
- Open **7-Zip portable.exe** from your previously extracted 7-Zip Portable directory, and navigate to the ````jdk-8u77-windows-xxxxx.exe```` download. **Right click** and choose **7-zip->Open archive**.
- A new archive will appear, containing the file ````tools.zip````. Right click that file and choose **Open**.
- A new archive will appear, containing a number of directories and files. Press **Ctrl-A** to select all, and then click the Blue Extract tool. Specify ````%USERNAME%\Downloads\jdk````.
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
- Run the file, and extract into a folder. Accept the default (````%USERNAME%\Downloads\EclipsePortable````)
- Copy all files and folders from the **Downloads\jdk** folder to the **Downloads\EclipsePortable\App\Java**

### Minecraftforge
- Browse to http://files.minecraftforge.net/ and download the **Recommended MDK** file.
- **WARNING** There are annoying adverts on this download site - don't download anything other than the forge-xxxxx-mdk.zip file - look for a **SKIP** button, and ignore any adverts.
- Unzip the downloaded ````forge-1.8.9-11.15.1.1722-mdk.zip```` file to ````%USERNAME%\Downloads\forge````.
- In Windows Explorer, navigate to the new ````Downloads\forge```` directory, and again, hold down **Shift**, and **right click**, then select "Open command window here".
- Type the following:
  - ````PATH="%PATH%";"%USERPROFILE%\Downloads\EclipsePortable\App\Java\bin"````
  - ````gradlew setupDecompWorkspace --refresh-dependencies````
    - Might take 5-15 minutes
  - ````gradlew eclipse````


### Start Eclipse
- Browse to **EclipsePortable** folder, and start **EclipsePortable.exe**.
- When asked to choose a workspace, browse to eclipse folder in MDK download folder, e.g. ````%USERNAME%\Downloads\forge\eclipse````
- If not prompted to choose a workspace, go to **File->Switch Workspace... -> Other**.
- Select the MDKExample folder in the left hand pane.
- Click the Green Run button, or press **Ctrl-F11**.

### Let's start Modding!
- Now go to [our first example mod](example1-mod.md).
