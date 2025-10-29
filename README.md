# 📱 Installation Guide

## 🧩 1. Prerequisites

Before you begin, make sure you have these installed:

### 🖥️ For Development
- **Node.js** (v18 or higher)  
- **npm** or **yarn**  
- **Git**  
- **VS Code**  
- **Expo CLI**  
  ```bash
  npm install -g expo-cli
Android Studio (for emulator or USB debugging)

📱 For Testing on Android
Any Android phone (Android 8.0 or higher)

Enable Developer Options → USB Debugging

Install Expo Go (optional, for testing via QR code)

⚙️ 2. After Cloning the Repository and Installing Dependencies
Building a New APK
Option 1: Using Expo (Recommended)
bash
Copy code
npx expo run:android
It will build and install the app on the connected Android device.

Option 2: Generate APK Manually
bash
Copy code
cd android
./gradlew assembleDebug
The generated APK will be located at:

swift
Copy code
android/app/build/outputs/apk/debug/app-debug.apk
🧰 3. Installations (Java, CLI, Android Studio)
Install Expo CLI (Global)
Expo CLI lets you create, build, and run React Native apps easily.

bash
Copy code
npm install -g expo-cli
Verify installation:

bash
Copy code
expo --version
If you’re using the newer Expo Application Services (EAS) for builds:

bash
Copy code
npm install -g eas-cli
eas --version
💡 expo-cli = for local development
💡 eas-cli = for cloud builds (publishing or building APKs)

Install Java (Required by Android Studio & Gradle)
Android Studio and Gradle require Java 17 or higher:

     ```bash
      sudo apt install openjdk-17-jdk -y

java -version
You should see:

nginx
Copy code
openjdk version "17.0.x"
Install Android Studio via Terminal
Option 1: Install using Snap (simplest)
bash
Copy code
sudo snap install android-studio --classic
Wait for the installation to complete, then launch it:

bash
Copy code
android-studio
Option 2: Manual Installation (if Snap not available)
Download Android Studio:

bash
Copy code
wget https://redirector.gvt1.com/edgedl/android/studio/ide-zips/latest/android-studio-2024.2.1.10-linux.tar.gz
Extract it:

bash
Copy code
tar -xvzf android-studio-*-linux.tar.gz
Move it to /opt:

bash
Copy code
sudo mv android-studio /opt/
Run setup:

bash
Copy code
/opt/android-studio/bin/studio.sh
Follow the setup wizard (choose Standard installation).

⚙️ 4. Set Up Android SDK and Environment Variables
After Android Studio installs, open terminal and run:

bash
Copy code
sudo nano ~/.bashrc
At the bottom, add the following lines:

bash
Copy code
export ANDROID_HOME=$HOME/Android/Sdk
export PATH=$PATH:$ANDROID_HOME/emulator
export PATH=$PATH:$ANDROID_HOME/platform-tools
export PATH=$PATH:$ANDROID_HOME/tools
export PATH=$PATH:$ANDROID_HOME/tools/bin
Save and apply changes:

bash
Copy code
source ~/.bashrc
Confirm:

bash
Copy code
echo $ANDROID_HOME
🧩 5. Install Android SDK Tools (via Command Line)
If not already installed, run:

bash
Copy code
sdkmanager --install "platform-tools" "platforms;android-34" "build-tools;34.0.0"
💡 android-34 = Android 14 (adjust to your target SDK version)

🧪 6. Create a Virtual Device (Emulator)
Open Android Studio → Device Manager → Create Virtual Device
or via terminal:

bash
Copy code
avdmanager create avd -n myEmulator -k "system-images;android-34;google_apis;x86_64"
List available devices:

bash
Copy code
emulator -list-avds
Start emulator:

bash
Copy code
emulator -avd myEmulator
📲 7. Run an Expo App on Emulator
Navigate to your project folder:

bash
Copy code
cd ~/Pesa-Tracker
Start the Expo dev server:

bash
Copy code
npx expo start
When Metro Bundler opens:

Press a → it will automatically open your emulator and run the app.

🔗 8. Connect Real Android Device (Optional)
You can also test directly on your phone:

On your phone, enable:

Developer Options → USB Debugging

Connect your phone via USB.

Check connection:

bash
Copy code
adb devices
You should see your phone listed.

Then run:

bash
Copy code
npx expo run:android
It will install the app on your phone.

🧼 9. Optional — Clear Caches and Fix Errors
If you get any weird errors:

bash
Copy code
expo start -c
Or rebuild the app completely:

bash
Copy code
npx expo run:android
✅ Summary of Key Commands
Task	Command
Install Expo CLI	npm install -g expo-cli
Install Android Studio	sudo snap install android-studio --classic
Start Expo	npx expo start
Run on Device	npx expo run:android
View Devices	adb devices
Clear Cache	expo start -c

