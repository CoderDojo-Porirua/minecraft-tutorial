# Creating Items
- Lets create some custom items in Minecraft - we're going to follow [MrCrayfish's](https://twitter.com/MrCraayfish) Minecraft 1.8 Modding tutorial - [Episode 3 - Custom Items](https://www.youtube.com/watch?v=2_qM-Z0IQ4k&index=3&list=PLy11IosblXIFDFAT3wz_5Nve05wIVKFSJ).

- We should have already [set up our development environment](dev-environment-setup.md).
- We should have [created our mod class](step1-mod-class.md)

- Create a new package
  - ````src/main/java/nz.cdr.minecrafttutorial```` - Right Click and New -> Package.
    - We'll use the name ````nz.cdr.minecrafttutorial```````.init```, or whatever you chose for the previous package name, with ````.init```` after it.
    - Click **Finish**.
- Create a new class
  - ````src/main/java/nz.cdr.minecrafttutorial.init```` - Right Click and New -> Class.
    - Give it the name ````TutorialItems````.
    - Click **Finish**.

- TO DESCRIBE:
- TutorialItems class
- Proxy package and classes
- ([:octocat:](https://github.com/CoderDojo-Porirua/minecraft-forge-1.8/commit/bd3abb5fd8a8cd6f10ed6d73de02117ca5e53461)
- Describe ```extends``` and ```@Override```.
- Client and Server proxies are to do different stuff on the client and the server.

- If it comes up with an *Organize Imports* dialogue when you press ````[Ctrl-Shift-O]````, choose ````net.minecraft.item.item````.

## Run the mod
- ```/give [tab] [our MOD_ID][tab]```
- ```/give Player123 tm:test_item```
- Item will appear as a purple and black block - we need to define some JSON files to tell Minecraft how the item should look!
- We need to create a 16x16 pixel image, and add to ```src/main/resources``` folder.
- Create a new ```assets``` folder, and within that another new folder named with your MOD_ID, e.g. ```tm```. ([:octocat:](https://github.com/CoderDojo-Porirua/minecraft-forge-1.8/commit/db296aafdc4a1280975aee58f669559e7d0c9ae1).
