How To install:
Part 1: Compile Java Files into a DEX File
Step 1: Set Up Your Environment

    Install the Java Development Kit (JDK):
        Ensure you have the JDK installed. You can download it from the Oracle website or OpenJDK.

    Install Android SDK:
        Make sure you have the Android SDK installed, including build tools. You can download it from the Android Studio or install just the command-line tools.

    Locate the Build Tools:
        Find the directory where your Android SDK is installed. Look for the build-tools folder (e.g., C:\Users\<YourUserName>\AppData\Local\Android\Sdk\build-tools\<version>\).

Step 2: Compile Java Files

    Open Command Prompt:
        Press Win + R, type cmd, and hit Enter.

    Navigate to Your Java Files:


cd path\to\your\java\files

Compile All Java Files:

    For Windows:


for /R %f in (*.java) do javac -d out "%f"

    For Unix/Linux/macOS:

    javac -d out $(find . -name "*.java")

    This will compile all .java files in the current directory and all its subdirectories into .class files placed in the out directory.

Step 3: Convert Class Files to DEX

    Navigate to the Build Tools Directory:

    

cd path\to\android\sdk\build-tools\<version>\

Run the dx Tool:



    dx --dex --output=output.dex path\to\your\java\files\out\

Part 2: Add DEX to Game Files
Step 1: Locate Game Files

    Find the Game Directory:
        Locate the directory where the game’s APK file and assets are stored.

Step 2: Add the DEX File

    Navigate to the Game’s OBB or Data Folder:
        This might be located in a folder named data, obb, or similar, depending on the game.

    Copy the DEX File:
        Copy your output.dex file to the appropriate folder where the game looks for executable files (often in a folder like lib or classes.dex).

Part 3: Rebuild into an APK
Step 1: Create a New APK Structure

    Create a New Folder:
        Create a new folder for your APK project (e.g., MyGameAPK).

    Create Required Folders:
        Inside MyGameAPK, create the following structure:

        MyGameAPK/
        ├── res/
        ├── AndroidManifest.xml
        ├── classes.dex
        └── assets/

Step 2: Prepare the AndroidManifest.xml

    Create or Edit the AndroidManifest.xml:
        This file defines your app's properties. Use the original APK's manifest as a reference, modifying it if necessary.

Step 3: Build the APK

    Use APKTool:
        Download APKTool. It allows you to rebuild APKs easily.

    Open Command Prompt:
        Navigate to where you downloaded apktool.jar.

    Run APKTool to Build APK:

   

    java -jar apktool.jar b MyGameAPK

    Locate the New APK:
        After building, the APK will be found in the dist folder inside your MyGameAPK folder.

Part 4: Sign the APK

    Sign the APK:
        You need to sign your APK to install it on a device. You can use jarsigner or apksigner (part of the Android SDK).

    Using apksigner:
        Open a command prompt and navigate to your APK directory.
        Use the following command to sign the APK:

    

    apksigner sign --ks my-release-key.jks --out my-app-release-signed.apk my-app.apk

        Make sure to create a keystore file if you don’t have one.

Part 5: Install the APK on Your Device

    Transfer the APK:
        Transfer the signed APK to your Android device.

    Install the APK:
        Open the APK file on your device to install it.
