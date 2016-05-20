# Let's start MODDING
- You're ready to start creating a mod - we're going to follow [MrCrayfish's](https://twitter.com/MrCraayfish) Minecraft 1.8 Modding tutorial - [Episode 2 - Mod Class](https://www.youtube.com/watch?v=S8Oy2Z5V2VU&index=2&list=PLy11IosblXIFDFAT3wz_5Nve05wIVKFSJ).

- We should have already [setup out development environment](dev-environment-setup.md).

- Delete the example mod
  - ````src/main/java/```` - ````com.example.examplemod```` - Right Click and delete.
- Create a new package
  - ````src/main/java/```` - Right Click and New -> Package.
    - In Java, packages often are often given a name of an organisation's website, but in reverse. So http://cdr.nz would become ````nz.cdr````.
    - Think of each dot being a new directory.
    - *Why do you think this might be?*
    - We'll use the name ````nz.cdr.minecrafttutorial```` for our package, or you can use your website, or minecraft username.
    - Click **Finish**.
- Create a new class
  - ````src/main/java/nz.cdr.minecrafttutorial```` - Right Click and New -> Class.
    - Give it the name ````TutorialMod````.
    - Click **Finish**.
