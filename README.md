# installation-Guide
🧩 1. Prerequisites

Before you begin, make sure you have these installed:

🖥️ For Development

Node.js
 (v18 or higher)

npm
 or yarn

Git

VS Code

Expo CLI

npm install -g expo-cli


Android Studio
 (for emulator or USB debugging)

📱 For Testing on Android

Any Android phone (Android 8.0 or higher)

Enable Developer Options → USB Debugging

Install Expo Go (optional, for testing via QR code)

AFTER CLONING THE RESPOSITORY AND ALL INSTALLATIONS:
Building a New APK
:

Option 1: Using Expo (Recommended)
npx expo run:android


It will build and install the app on the connected Android device.

Option 2: Generate APK manually
cd android
./gradlew assembleDebug


The generated APK will be at:

android/app/build/outputs/apk/debug/app-debug.apk




THIS ARE INSTRUCTIONS FOR INSTALLATION OF JAVA ,CLI,ANDROID STUDIO:

Install Expo CLI (Global)

Expo CLI lets you create, build, and run React Native apps easily.

npm install -g expo-cli


Verify installation:

expo --version


If you’re using the newer Expo Application Services (EAS) for builds:

npm install -g eas-cli
eas --version


💡 expo-cli = for local development
💡 eas-cli = for cloud builds (like publishing or building APKs)

Install Java (Required by Android Studio & Gradle)

Android Studio and Gradle require Java 17 or higher:

sudo apt install openjdk-17-jdk -y
java -version


You should see:

openjdk version "17.0.x"

Install Android Studio via Terminal
Option 1: Install using Snap (simplest way)
sudo snap install android-studio --classic


Wait for the installation to complete, then launch it:

android-studio

Option 2: Manual installation (if Snap not available)

Download Android Studio .tar.gz:

wget https://redirector.gvt1.com/edgedl/android/studio/ide-zips/latest/android-studio-2024.2.1.10-linux.tar.gz


Extract it:

tar -xvzf android-studio-*-linux.tar.gz


Move it to /opt:

sudo mv android-studio /opt/


Run the setup:

/opt/android-studio/bin/studio.sh


Follow the on-screen setup wizard (choose Standard installation).

⚙️ 7. Set Up Android SDK and Environment Variables

After Android Studio installs, open the terminal and run:

sudo nano ~/.bashrc


At the bottom, add the following lines:

export ANDROID_HOME=$HOME/Android/Sdk
export PATH=$PATH:$ANDROID_HOME/emulator
export PATH=$PATH:$ANDROID_HOME/platform-tools
export PATH=$PATH:$ANDROID_HOME/tools
export PATH=$PATH:$ANDROID_HOME/tools/bin


Save and apply changes:

source ~/.bashrc


Then confirm:

echo $ANDROID_HOME

🧩 8. Install Android SDK Tools (via Command Line)

If not already installed, run:

sdkmanager --install "platform-tools" "platforms;android-34" "build-tools;34.0.0"


💡 android-34 = Android 14 (you can adjust to your target SDK version)

🧪 9. Create a Virtual Device (Emulator)

Open Android Studio → Device Manager → Create Virtual Device
or do it via terminal:

avdmanager create avd -n myEmulator -k "system-images;android-34;google_apis;x86_64"


To list available devices:

emulator -list-avds


To start your emulator:

emulator -avd myEmulator

📲 10. Run an Expo App on Emulator

Once everything is installed, go to your project folder:

cd ~/Pesa-Tracker


Start the Expo dev server:

npx expo start


When the Metro Bundler opens:

Press a → it will automatically open your emulator and run the app.

🔗 11. Connect Real Android Device (Optional)

You can also test directly on your phone:

On your phone, enable:

Developer Options → USB Debugging

Connect your phone via USB.

Run:

adb devices


You should see your phone listed.

Then run:

npx expo run:android


It will install the app on your phone.

🧼 12. Optional — Clear Caches and Fix Errors

If you get any weird errors:

expo start -c


Or rebuild your app completely:

npx expo run:android

✅ Summary of Key Commands
Task	Command
Install Expo CLI   	npm install -g expo-cli
Install Android Studio   	sudo snap install android-studio --classic
Start Expo   	npx expo start

Run on Device  	npx expo run:android
View Devices	 adb devices
Clear Cache 	expo start -c

