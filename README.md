## UWP For Windows Phone ##
Documentation for Windows Phone compilation.  
This guide will only cover Windows Phone 10, simply because I do not have a Windows 8 phone.

---

## Step 1.0: Prerequisites ##
So you've stumbled across a Windows Phone, and decided to start development. I'm here to help.
Here's some things you'll need:
1. **[Visual Studio *2017*](https://aka.ms/vs/15/release/vs_community.exe)** (Things like Visual Studio 2022 do not support working with UWP apps at a version of the SDK which we need.)  
    Don't worry about VS2017 deleting any VS2022 projects; they can both exist alongside each other.

2. The Windows SDK (Windows Phone 10 only works with SDKs of a certain version.)  
    I recommend the **[Build 16299](https://go.microsoft.com/fwlink/p/?linkid=864422)** version simply because it works.
3. A physical device to work with. (I have a Lumia 650 and there *is* an emulator for Windows Phone, but I haven't gotten it to work.)
4. **C# and XAML Knowledge**  
    (This is optional, I basically have no idea what I'm doing. VS2017 also comes with a version of Blend that works with Windows Phone so it makes it easier to design UIs.)
5. **Time and Patience**  
    Windows Phone is extremely temperamental, so I suggest having some sort of patience and willingness to work out bugs.


Congrats! That's all the stuff we'll need so far.

---

## Step 2.0: Setup ##
Alright, let's get this shit setup.  

1. Install the Windows SDK you downloaded earlier. (This takes fucking forever btw.)
2. Install VS2017.  
- Make sure none of the items circled in red are installed. (I don't know if this actually breaks anything but it works without them.)
    <img width="900" alt="Untitled" src="https://github.com/user-attachments/assets/bc3364cd-8c35-469a-9888-09f3c22b76ab" />

---

## Step 2.1: Windows Phone Setup ##
Now let's set up the phone for usage. (My phone has been hacked so mine might look a bit different but it should still work either way.)
1. Enable Developer Mode.  
   <img width="700" alt="enableDev" src="https://github.com/user-attachments/assets/abccc0a7-03f5-4c55-a629-8fda2290c6ca" />
2. Enable Remote Diagnostics. **This is critical for installing apps.**  
   <img width="300" alt="wp_ss_20250831_0004" src="https://github.com/user-attachments/assets/06d504fc-fab1-47ed-8ac9-a7173caef7d9" />
3. Check that the phone can be reached.  
   - Using the web address the phone gives you, access that in the computer's web browser.
   <img width="700" alt="image" src="https://github.com/user-attachments/assets/5e207376-7861-44c6-b6a8-8e622626e331" />

---
We're ready to start developing!

## Step 3.0: Developing Apps ##
Let's get started.  
The last version of Windows Phone to ship was build 10.0.15254.603 so that's what we'll be compiling to.

1. Open VS2017.  
   You should see this screen.  
   <img width="700" alt="image" src="https://github.com/user-attachments/assets/01eb7cc5-39b7-45df-8abc-4d748c2a0c04" />  
   - Under "New Project", select "Create New Project".  
2. Select Project Template.  
   <img width="700" alt="image" src="https://github.com/user-attachments/assets/4b7a3d6b-8499-4e78-8c37-5166466e1b73" />  
   - Under the "Visual C#" Category, select "Blank App (Universal Windows)"  
3. **Set correct SDK version. (CRITICAL)**   
   <img width="550" alt="image" src="https://github.com/user-attachments/assets/9df30fe4-09cf-4cae-9bb5-47012ab53920" />  
   - Set Target Version to "Windows 10 Fall Creators Update"
   - Minimum version should automatically become "Windows 10 November Update"  
       
   Correct Setup:  
   <img width="550" alt="image" src="https://github.com/user-attachments/assets/ddc6c2ac-d1ae-456f-87c9-8e48e2b32298" />  
**Note: If you don't see these options, you haven't installed the SDK correctly.**
---
Congrats, you can now start working on your app! Select MainPage.xaml to start working.

## Step 4.0: Compiling Apps ##
Almost there! Now we have to compile our app.  
Here's how:  
1. Right click the project. (Its name will be "*appName* (Universal Windows)" with a little green box around a C#.)  
   <img width="500" alt="image" src="https://github.com/user-attachments/assets/519a4978-954c-4a49-8046-eceaa302f665" />
2. In the menu, click "Store" and then "Create App Packages".  
   <img width="700"  alt="image" src="https://github.com/user-attachments/assets/5d276ed2-988a-4a85-95ef-5beb2c356e14" />
3. In the window that pops up, select "I want to create packages for sideloading." and click "Next".  
   <img width="600" alt="image" src="https://github.com/user-attachments/assets/0f6a13e5-c999-4d3f-a208-4b09155912d8" />
4. In the table, uncheck both "x86" and "x64".    
    - Make sure "ARM" (Not "ARM64") is checked.  
   <img width="600"  alt="image" src="https://github.com/user-attachments/assets/a9392756-ea48-463f-b0ec-6131b3ad7927" />
5. Hit create and wait for compilation.

---
We're now ready to install your brand new app!

## Step 5.0: Installing Apps ##
Final step! Let's get your app installed.  
1. After compilation is finished, your app will be in the project's folder. (Do step 4's first part but click on "Open folder in File Explorer" instead.)

2. Navigate in the "AppPackages" folder and there should only be one folder in there. Navigate into that folder.  
   <img width="700" alt="image" src="https://github.com/user-attachments/assets/b59f49e1-dc66-4e00-b141-7a16e550c1cb" />
3. Access the website from Step 2.1 and select the app manager column on the left.  
   <img width="700" alt="image" src="https://github.com/user-attachments/assets/5e207376-7861-44c6-b6a8-8e622626e331" />
4. Under "App Package" in the "Install App" column, select the appxbundle.  
   <img width="700" alt="image" src="https://github.com/user-attachments/assets/b257eb49-6208-49b6-98af-823e36019c83" />
5. Add dependancies by pressing "Add dependency" and navigating to the "Dependencies" subfolder and then the "ARM" subfolder.
   - Make sure it's the "ARM" folder and not the "ARM64" folder.
   - Do this for all packages in the "ARM" folder.  
   <img width="700" alt="image" src="https://github.com/user-attachments/assets/d5c39fcd-5de0-4b8c-978d-f45bbe55ac99" />
6. Select "Go".
   - If all goes to plan, it should install fine and you should see your new app.
   <img width="720" alt="wp_ss_20250831_0005" src="https://github.com/user-attachments/assets/fd7f540d-59ff-4758-bca8-3a887a8eb327" />
---
That's it! Your new app should run (assuming you haven't made any programming errors).
