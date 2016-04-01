# Minecraft Modding Tutorial
A Minecraft modding tutorial for use on a locked down Windows machine.

We're going to try and set up a development environment on a locked down Windows machine. This tutorial has been tested on Windows 10, but should work on earlier versions too.

We're using *portable versions* of the Java Development Kit and Eclipse so that we can work on machines without needing administrative access, or installing anything on to the computer, for example in a school environment.

Folder paths below are arbitrary, but if you use the defaults, it will mean the steps are easier to follow.

## What do we need to download?
### 7-Zip (portable edition)
- Browse to http://portableapps.com/apps/utilities/7-zip_portable
- Download, and run **7-ZipPortable_15.14.paf.exe**, which will extract into a folder. Accept the default (````C:\Users\<username>\Downloads\7-ZipPortable````)

### Git (portable edition)
- Browse to https://git-scm.com/download/win
- Download, and run **PortableGit-2.8.0-32-bit.7z.exe**, which will extract into a folder. Accept the default (````C:\Users\<username>\Downloads\PortableGit````).

### The Java Development Kit 8 (JDK)
- This one is a bit involved, as we're going to take a normal JDK download, and create a portable version out of it.
- Browse to http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html
- Click **Accept License Agreement**
- Download the Java SE Development Kit 8u77 for your operating system - probably **jdk-8u77-windows-i586.exe** or **jdk-8u77-windows-x64.exe**, depending on whether you're running 32 or 64 bit Windows.
- Don't run this file!
- Open 7-Zip portable, and navigate to the ````jdk-8u77-windows-xxxxx.exe```` download. **Right click** and choose **7-zip->Open Archive**.
- A new archive will appear, called ````tools.zip````. Right click and choose **Open**.
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
- Unzip the downloaded ````forge-1.8.9-11.15.1.1722-mdk.zip```` file to ````C:\Users\<username>\Downloads\forge````.
- In Windows Explorer, navigate to the new ````Downloads\forge```` directory, and again, hold down **Shift**, and **right click**, then select "Open command window here".
- Type the following:
  - ````PATH="%PATH%";"%USERPROFILE%\Downloads\EclipsePortable\App\Java\bin"````
  - ````gradlew setupDecompWorkspace --refresh-dependencies````
    - Might take 5-15 minutes
  - ````gradlew eclipse````


### Start Eclipse

- Browse to EclipsePortable folder, and start **EclipsePortable.exe**.



### Mine

## Troubleshooting
### Unpacking issues
If you see the following issue whilst unpacking the jdk, check the version of the jdk you downloaded matches your operating system.

````
This version of C:\Users\coderdojo\Downloads\jdk\jre\bin\unpack200.exe is not compatible with the version of Windows you're running. Check your computer's system information and then contact the software publisher.
````
