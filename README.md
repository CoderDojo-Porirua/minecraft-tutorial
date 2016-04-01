# minecraft-tutorial
A Minecraft modding tutorial for use on a locked down Windows machine.

We're going to try and set up a development environment on a locked down Windows machine. This tutorial has been tested on Windows 10, but should work on earlier versions too.

We're using portable versions of the Java Development Kit and Eclipse so that we can work on machines without needing administrative access.

Folder paths below are arbitraty, but if you use the defaults, it will mean the steps are easier to follow.

## What do we need to download?
### 7-Zip (portable edition)
http://portableapps.com/apps/utilities/7-zip_portable
- Download, and run **7-ZipPortable_15.14.paf.exe**, which will extract into a folder. Accept the default (````C:\Users\<username>\Downloads\7-ZipPortable````)

### Git (portable edition)
https://git-scm.com/download/win
- Download, and run **PortableGit-2.8.0-32-bit.7z.exe**, which will extract into a folder. Accept the default (````C:\Users\<username>\Downloads\PortableGit````).

### The Java Development Kit 8 (JDK)
http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html
- Click **Accept License Agreement**
- Download the Java SE Development Kit 8u77 for your operating system - probably **jdk-8u77-windows-i586.exe** or **jdk-8u77-windows-x64.exe**, depending on whether you're running 32 or 64 bit Windows.
- Don't run this file!
- Open 7-Zip portable, and navigate to the ````jdk-8u77-windows-xxxxx.exe```` download. Right click and choose **7-zip->Open Archive**.
- A new archive will appear, called ````tools.zip````. Right click and choose **Open**.
- A new archive will appear, containing a number of directories and files. Press **Ctrl-A** to select all, and then click the Blue Extract tool. Specify ````c:\Users\<username>\Downloads\jdk````.
