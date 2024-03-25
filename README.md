# jenkins-android
Installation:
----------
```
sudo apt-get update

sudo apt install openjdk-17-jdk

sudo apt install android-sdk

sudo mkdir /usr/lib/android-sdk/cmdline-tools

cd /usr/lib/android-sdk/cmdline-tools

sudo  wget https://dl.google.com/android/repository/commandlinetools-linux-11076708_latest.zip

sudo unzip commandlinetools-linux-11076708_latest.zip 

sudo rm commandlinetools-linux-11076708_latest.zip  

export ANDROID_HOME=/usr/lib/android-sdk/

export PATH=$PATH:$ANDROID_HOME/cmdline-tools/tools/bin

export PATH=$PATH:$ANDROID_HOME/platform-tools

sdkmanager --version

./sdkmanager --list

sudo chmod 777 $ANDROID_HOME -R

cd /usr/lib/android-sdk/cmdline-tools/bin/

yes | ./sdkmanager --licenses

yes | ./sdkmanager "platform-tools" "platforms;android-29"
```
```
./sdkmanager --list

./sdkmanager --install "<package>"

#install x86 image

./avdmanager create avd --name <avd_name> --package <system_image_package> --abi <cpu_abi>

ex: ./avdmanager create avd --name MyAVD --package "system-images;android-30;google_apis;x86_64" --abi x86_64 --device "pixel" --sdcard 512M --force
```
```
cd /usr/lib/android-sdk/emulator/

./emulator -list-avds

./emulator --avd <avd name>
```
emulator will start

Install Jenkins, And setup android-sdk path in jenkins

Go to manage jenkins > system > Golbal properties > environment variable 
![android-jenkins](https://github.com/beeru405/jenkins-android/assets/101712802/49784a3b-dd2d-4fd4-ad16-f870e9474d91)

setup gradle in manage jenkins > tools

now create a free style job

give gradle commands 

```
clean
assembleDebug
```
execute shell give adb command 

give path of adb and apk file located
```
/usr/lib/tools/android-sdk/platform-tools/adb install /var/lib/jenkins/workspace/android-cicd/app/build/outputs/apk/debug/app-debug.apk
```





