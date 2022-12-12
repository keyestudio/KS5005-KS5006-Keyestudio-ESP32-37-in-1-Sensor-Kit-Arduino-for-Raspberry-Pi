# Preparation before class for C(Raspberry Pi)

Raspberry Pi is a card computer whose official system is Raspberry Pi
OS, and can be installed on the Raspberry Pi, such as: ubuntu, Windows
IoT. Raspberry Pi can be used as a personal server, performing camera
monitoring and recognition, as well as voice interaction by connecting a
camera and a voice interactive assistant. Also, Raspberry Pi leads out
40Pin pins that can be connected to various sensors and control LEDs,
motors, etc. This can be used to make a robot with a Raspberry Pi.

## 1. Tools needed for the Raspberry Pi system

**Hardware Tool:**

  - Raspberry Pi 4B/3B/2B

  - Above 16G TFT Memory Card

  - Card Reader

  - Computer and other parts

**1.1 Install Software Tools**

**Windows System:**

1)  **Putty**
    
    Download
    link：[<span class="underline">https://www.chiark.greenend.org.uk/\~sgtatham/putty/</span>](https://www.chiark.greenend.org.uk/~sgtatham/putty/)
    
    ![](media/c26be4cd1f5543f20f275556ce5892c0.png)
    
    ![](media/d888918aa7bf9e5ea94597aad1ee4224.png)

<!-- end list -->

1.  After downloading the package file ![](media/e597704d7033c7c3c5da06d4f561822c.png),
    double-click it and tap “Next”.
    
    ![](media/01f1b2d98915be2be9c0c2a3d330dde2.png)

2.  Click “Next”.
    
    ![](media/bd698753a8eea7a2ff5c5e0e598cbd94.png)

3.  Choose“Install Putty files” and click “Install”.
    
    ![](media/071a0acc98bb2dc5cd45d85dec72d111.png)

4.  After a few seconds, click "Finish".
    
    ![](media/ec368c3a549c09edd70f9786456d5430.png)
    
    **(2) SSH Remote Login software -WinSCP**
    
    Link：[<span class="underline">https://winscp.net/eng/download.php</span>](https://winscp.net/eng/download.php)

<!-- end list -->

1.  After downloading the package file![](media/1719daa1002d7477ad4700e1df85d2df.png), click
    ![](media/e09e48a32781d08aabb06156efe1de49.png).
    
    ![](media/5ee80ade909fe3eb73dc9535704b4c0b.png)

2.  Click“Accept”.

![](media/9c652f54f6a7d53f6b2aedba40104a00.png)

![](media/f32891714d5966037d59d1812aa15686.png)

![](media/57d6139ba0aac9ca996bcbe6f6fd218f.png)

![](media/49ffed878ee84546b156af3a0bf5556e.png)

![](media/14ffa1e11243835d30ffb933219dcef5.png)

**(3）SD Card Formatter**

Download link:

[<span class="underline">http://www.canadiancontent.net/tech/download/SD\_Card\_Formatter.html</span>](http://www.canadiancontent.net/tech/download/SD_Card_Formatter.html)

![](media/fa229f4e063572ce1c59574c308bf452.png)

![](media/ac5d5eb9463805484b9239b99faf04eb.png)

1.  Unzip the SDCardFormatterv5\_WinEN package, double-click
    ![](media/8c6f8da97bf702080a8e302db2e9f982.png) to run it.
    
    ![](media/046c67e4072093ee3dad27e8088fcf9f.png)
    
    ![](media/384203e0b54ddfe37f18b65f70e786e5.png)
    
    ![](media/cf4e91eac0c0573cff282256a915a01a.png)

2.  Click“Next”and“Install”.
    
    ![](media/0af58ee3afb14005a884ca2dc941157f.png)
    
    ![](media/807623ddeea20c8b61503845d8aec9bc.png)

3.  After a few seconds, click "Finish".
    
    ![](media/df2deb7e04c25ee207e994f0d2808194.png)
    
    **(4) Win32DiskImager**
    
    Download：[<span class="underline">https://sourceforge.net/projects/win32diskimager/</span>](https://sourceforge.net/projects/win32diskimager/)
    
    ![](media/4ffb55fd466198ca9524afbde7806271.png)
    
    a. After downloading the package file ![](media/63c3eaf215c92c325f95613c9d8d49ce.png),
    double-click to run it.
    
    ![](media/0f86f055a814207b0b09e1a7e6cb20bc.png)
    
    b. Choose ![](media/5cdab33a0a7ddd4ab5b2ca8cb04670be.png)and click“Next”.

![](media/d70ecd0554cbdbd60997a2356b55dc0d.png)

c. Click“Browse...”and tap“Next”.

![](media/1cdc2638bc1e9fe214344429f5e97a13.png)

![](media/cc7949bb335b75000e77b18c85e4e07b.png)

d. Choose ![](media/99d088dd3f9e62d94fe8d56bd4638d1d.png), click“Next”and“Install”.

![](media/c03510a9961a0e7307945dff10de3550.png)

![](media/0c9c0d647479ee984fc29c3cedc72c79.png)

e. After a few seconds, click "Finish".

![](media/1d75c6dd9ea4a2c437a2b655b713a1db.png)

(5) WNetWatcher for scanning and searching IP addresses  

Download Link：http://www.nirsoft.net/utils/wnetwatcher.zip

**1.2 Raspberry Pi Imager**

Download link for the latest version:

[<span class="underline">https://www.raspberrypi.org/downloads/raspberry-pi-os/</span>](https://www.raspberrypi.org/downloads/raspberry-pi-os/)

Old Version:

Raspbian：https://downloads.raspberrypi.org/raspbian/images/

Raspbian
full：<span class="underline">https://downloads.raspberrypi.org/raspbian\_full/images/</span>

Raspbian lite：https://downloads.raspberrypi.org/raspbian\_lite/images/

We use the 2020.05.28 version in the tutorial and recommend you to use
this version

(Please download this version as shown in the picture below.)

<https://downloads.raspberrypi.org/raspios_full_armhf/images/raspios_full_armhf-2021-05-28/>

![](media/857946c171dd1f5617a0cbbdd2608baf.png)

## 2. Install Raspberry Pi OS on Raspberry Pi 4B

Interface the TFT memory card with a card reader, then plug the card
reader into a computer’s USB port.

Use the SD Card Formatter to format a TFT memory card, as illustrated
below.

![](media/79d747e6f00f857a593b3327397cc44f.png)

![](media/cbc55902de71ce984d873ca2cb67fffa.png)

![](media/82031b5354cc4edeccf2bfa7465b7c6c.png)

1)  **Burn system**
    
    Burn the Raspberry Pi OS to the TFT memory card using
    Win32DiskImager software.

![](media/80d236cae8bdf63d80dc65048ffb52b3.png)

![](media/243d1ef34211eafe1a92b67fc0ee85a2.png)

![](media/ea854c476e9a8d4f82dd4a7c714cd5af.png)

Don’t eject card reader after burning mirror system, build a file named
SSH, then delete .txt.

The SSH login function can be activated by copying SSH file to boot
category, as shown below.

![](media/ffb73310322accd671da373bb2e71945.png)

Eject card reader.

2)  **Log in system**
    
    (Raspberry and PC should be in the same local area network.)
    
    Insert TFT memory card into Raspberry Pi, connect internet cable and
    plug in power. If you have screen and HDMI cable of Raspberry Pi,
    you could view Raspberry Pi OS activating. If not, you can enter the
    desktop of Raspberry Pi via SSH remote login software---WinSCP and
    xrdp.
    
    **(3) Remote login**
    
    **Enter default user name, password and host name on WinSCP to log
    in. Only a Raspberry Pi is connected in the same network.**
    
    ![](media/0a41d5c629ec98afbc31dc47ff5c18ec.png)
    
    ![](media/ff64e71b9e30df60d0b099dbc2532587.png)
    
    **(4) Check IP and mac address**
    
    ![](media/a4285a452978026c9e60c31d35974315.png)
    
    Click to open terminal and input the password: raspberry, and
    press“Enter”on keyboard.
    
    ![](media/a433a9ee584c821a702d0250937e2ba8.png)
    
    ![](media/7fb10d842cc7fd824a325d30fc3ecdc7.png)
    
    Logging in successfully, open the terminal, input **ip a** and
    tap“Enter”to check IP and mac address.
    
    ![](media/132e9ab754a0f63e38b3e4cfbc3679f2.png)
    
    From the above figure, mac address of this Raspberry Pi is
    a6:32:17:61:9c, and IP address is 192.168.1.128(use IP address to
    finish xrdp remote login).
    
    Since mac address never changes, you could confirm IP via mac
    address when not sure which IP it is.
    
    **(5) Fix IP address of Raspberry Pi**
    
    IP address is changeable, therefore, we need to make IP address
    fixed for convenient use.
    
    Follow the below steps:
    
    Switch to root user
    
    If without root user’s password
    
    ① Set root password

Input password in the terminal: sudo passwd root to set password.

② Switch to root user

su root

③ Fix the configuration file of IP address

Firstly change IP address of the following configuration file.

（\#New IP address:：address 192.168.1.99）

Copy the above new address to terminal and press“Enter”.

Configuration File**:**

echo -e '

auto eth0

iface eth0 inet static

\#Change IP address

address 192.168.1.99

netmask 255.255.255.0

gateway 192.168.1.1

network 192.168.1.0

broadcast 192.168.1.255

dns-domain 119.29.29.29

dns-nameservers 119.29.29.29

metric 0

mtu 1492

'\>/etc/network/interfaces.d/eth0

As shown below:

![](media/a68a4f59d4d364efa28b6680a2c48d43.png)

④ Reboot the system to activate the configuration file.

Input the restart command in the terminal: sudo reboot

You could log in via fixed IP afterwards.

⑤ Check IP and insure IP address fixed well.

![](media/b4313e2d78a4289705c658a1ebbc962b.png)

(6) Log in desktop on Raspberry Pi wirelessly

In fact, we can log in desktop on Raspberry Pi wirelessly even without
screen and HDMI cable.

VNC and Xrdp are commonly used to log in desktop of Raspberry Pi
wirelessly. Let’s take an example of Xrdp.

Install Xrdp Service in the terminal

Installation commands:

Switch to Root User: su root

Installation: apt-get install xrdp

Enter y and press“Enter”.

As shown below:

![](media/aa59941ff4c1e582e8183c1dc3767fce.png)

Open the remote desktop connection on Windows

Press WIN+R on keyboard and enter mstsc.exe.

As shown below:

![](media/e5a66a3a1c998f8feb1c21c7a457ec4e.png)

Input IP address of Raspberry Pi, as shown below.

Click“Connect”and tap it again.

192.168.1.99 is the IP address we use, you could change into your IP
address.

![](media/c41c66bea61b30019e02a74b483af700.png)

Click“Yes”.

![](media/297813f1370ce5c158fac61511f61295.png)

Input user name: pi, default password: raspberry, as shown below.

![](media/251fddc1decc15d0b69f8a0c7467d5c1.png)

Click“OK”or“Enter”, you will view the desktop of Raspberry Pi OS, as
shown below.

![](media/56bd5693edd484c4433dc438b58c6130.png)

Now, we finish the basic configuration of the Raspberry Pi OS.

## 3. Preparations for C language

[C](C:/Users/NINGMEI/AppData/Local/youdao/dict/Application/8.10.7.0/resultui/html/index.html#/javascript:;) [language](C:/Users/NINGMEI/AppData/Local/youdao/dict/Application/8.10.7.0/resultui/html/index.html#/javascript:;)
is a programming language with a considerably fast running speed. There
are numerous software and system core code written in it, such as Linux
system. Notably, hardware MCU and embedded class are not exception.
Thereby, it makes sense to learn the
[C](C:/Users/NINGMEI/AppData/Local/youdao/dict/Application/8.10.7.0/resultui/html/index.html#/javascript:;) [language](C:/Users/NINGMEI/AppData/Local/youdao/dict/Application/8.10.7.0/resultui/html/index.html#/javascript:;)
to control hardware.

1)  **Hardware：**
    
    **Raspberry Pi 4B：**

<table>
<tbody>
<tr class="odd">
<td><strong>Raspberry Pi 4B</strong></td>
<td><strong>Raspberry Pi 4B Model</strong></td>
</tr>
<tr class="even">
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5005-KS5006-Keyestudio-ESP32-37-in-1-Sensor-Kit-Arduino-for-Raspberry-Pi/master/media/906942071bae7f818bf39db600c7eca2.png" style="width:2.30208in;height:3.42708in" /></td>
<td><img src="https://raw.githubusercontent.com/keyestudio/KS5005-KS5006-Keyestudio-ESP32-37-in-1-Sensor-Kit-Arduino-for-Raspberry-Pi/master/media/67ac8e458430628f26cef46f04be3979.png" style="width:2.36458in;height:3.45833in" /></td>
</tr>
</tbody>
</table>

**Hardware Interfaces：**

![](media/d232a87d73f7426894a6cafed80521a0.png)

## 4. ESP32 Expansion Board：
    
    ![](media/28c29f0137c08af2861799e6821a7d49.jpeg)
    
    Raspberry Pi+ESP32 mainboard+ESP32 Expansion Board+USB Cableare as
    follows：

![](media/ffb76852e9ab376ab2fe73d0dd1c8bef.jpeg)

![](media/9881a56f8435df9046c84b460a9aace6.jpeg)

2)  **Copy Example Code Folder to Raspberry Pi**

Place example code folder to the pi folder of Raspberry Pi. and extract
the example code from **2. ESP32\_C\_code.zip** file(the default is ZIP
file), as shown below:

![](media/e7b577a013d27250449f6a6062f2a692.png)

![](media/2c23642918c104cc098bd9a439c7f188.png)

![](media/6b0c6ea09c7467e12ff593b5e37d1cf7.png)

![](media/86ed5ebc5c517a7886e731269f429fa6.png)

Double-click **2.ESP32\_C\_code,**  as shown below.  

![](media/6072268384c416ece438cf3901b16156.png)

## Linux System（Raspberry Pi） 

**5.1 Download and install Arduino IDE**

（1）First, click on Raspberry Pi's browser.

![](media/027fa8703101b0c296fbc82f9f246a36.png)

（2）Download Arduino IDE from the Arduino official
website：[www.arduino.cc/en/software](http://www.arduino.cc/en/software),as
shown below:

![](media/64b964654fbdf403e42b61c753de120d.png)

![](media/e36e4d78ca3e5f57d51204d10be4b1a8.png)

(3) There are various versions of IDE for Arduino. Just download a
version compatible with your system. (install the lasted Arduino IDE)
and click “Linux ARM 32 bits”.

![](media/673eacbf2dd436181621cbf2dd901cdd.png)

You just need to click JUST DOWNLOAD.

![](media/83d707e7d53788a08e63bab812298b09.png)

After a few seconds, the lasted Arduino IDE（Arduino 1.8.19 version）zip
file can be directly downloaded

(4) Click ![](media/673b0d8e5e8fc594f1914418da8d74a9.png), then find the Downloads file from the
pi and tap it. Then we can see the downloaded
package“arduino-1.8.19-linuxarm.tar.xz”and unzip it.

![](media/8bfa85ec821d531fc042e4e2aa4c40ce.png)

![](media/7721714f317a56214f4c14bfbfb92eeb.png)

![](media/0137b14e0053855856de0ff859ea1161.png)

![](media/2e144aae66a787d7c30945b24072b144.png)

（5）Click![](media/b479804e1f9ae2cdfaa0aad8495523d4.png)file
and tap it，click“Execute” to install the Arduino IDE.

![](media/282a3e90f752066a10c69d75c58bc0be.png)

![](media/cc0f7b8a14fa5bdcb6560f51f6ffc917.png)

![](media/97bf23de0c9aa37db243d67d5e3f8670.png)

（6）Click ![](media/2ef5420fde334b93163b4a35e32e77dd.png)and click
![](media/cc7c9f3977d8da562ba2e98a6246c6b5.png) to open the Arduino IDE.

![](media/97f4118fc1f0d19aeb32a5af08812726.png)

![](media/f48690b0a3f56b9436ad4c56f0667af0.png)

**5.2 Install the ESP32 on Arduino IDE**

Note：you need to download Arduino IDE 1.8.5 or advanced version to
install the ESP32.

1.  > Click![](media/2ef5420fde334b93163b4a35e32e77dd.png) and
    > click ![](media/cc7c9f3977d8da562ba2e98a6246c6b5.png) to open the Arduino IDE.
    
    ![](media/6d61bd9f09f10763899e43a873b8bc75.png)
    
    (2） Click **“ File**” →**“Preferences”**，copy the website address
    <https://dl.espressif.com/dl/package_esp32_index.json> in
    the“**Additional Boards Manager URLs:**”and click“**OK**”
    
    ![](media/834b8fc35034df92b21b36956fb1b300.png)

![](media/e509e8aece551e449ccb6ab6fffa0dc1.png)

（3） Click“**Tools**”→“**Board:**”then click “**Boards Manager...**”to
enter“**Boards Manager**”. Enter **ESP32**”as follows, then click
**Install .**

![](media/ca9d80ba478d379d40afe119d60ec8cf.png)

![](media/b6d62e4c9cb8f530dc49b8ee92ecd76e.png)

![](media/1eaf35ef0b85b62a54733c2887bbced6.png)

(4) After installing, click“Close”

![](media/07d535a3532a58b15e79c9848ad8a019.png)

**5.3. Arduino IDE Setting**

Click![](media/2ef5420fde334b93163b4a35e32e77dd.png) and click
![](media/cc7c9f3977d8da562ba2e98a6246c6b5.png) to open the Arduino IDE.

![](media/8aca9b5378e794375f2c15d3b4e238ba.png)

When downloading the sketch to the board, you must select the correct
name of Arduino board that matches the board connected to your computer.
As shown below;

(Note: we use the ESP32 board in this tutorial; therefore, we select
ESP32**)**

![](media/973eb76d6528c9464b0f03db2c679a64.png)

![](media/20172f3be362482efa80c49c2603b888.png)

Then select the correct COM port (you can see the corresponding COM port
after the ESP32 is connected to the Raspberry Pi via a USB cable.).

![](media/fab5efb1aeaae7e6864f1286934c89d7.png)

![](media/e341c279be4e2d1a53389e1124e5128d.png)

![](media/d80f72747dd81a7c38022c057eaa6015.png)

A- Used to verify whether there is any compiling mistakes or not.

B- Used to upload the sketch to your Arduino board.

C- Used to create shortcut window of a new sketch.

D- Used to directly open an example sketch.

E- Used to save the sketch.

F- Used to send the serial data received from board to the serial
monitor.

**6. How to Add Libraries?**

**(1) What are Libraries ?**

[Libraries ](https://www.arduino.cc/en/Reference/Libraries)are a
collection of code that make it easy for you to connect
sensors,displays, modules, etc.

For example, the built-in LiquidCrystal library helps talk to LCD
displays. There are hundreds of additional libraries available on the
Internet for download.

The built-in libraries and some of these additional libraries are listed
in the reference. (https://www.arduino.cc/en/Reference/Libraries)

**(2) How to Install a Library ?**

Here we will introduce the most simple way to add libraries .

**Step 1:** Click ![](media/e927e911da6b964ab71f193c63403606.png)，tap“Downloads”file
![](media/83ad90890a4783af385a3dac7c0954a3.png)，and
click“arduino-1.8.19”file![](media/df44a04c4d9dc93465a56e4ff7c9d184.png)，then find and
click“libraries” file ![](media/630636db590e92c4969f89967124f96f.png)from the
“arduino-1.8.19”file.

![](media/8fd90361aa115003241352cad2d9072d.png)

![](media/52a6147ae9a153e322672a52f96a4c6d.png)

![](media/438dd551f77795e04c4c532374dc13cc.png)

![](media/fcdfbb335828776c4b8d4a56f3833958.png)

![](media/e63db82531b8923e77969bf95662e446.png)

**Step 2:** Copy and paste the Arduino C library ZIP file (default ZIP
file) from the provided Arduino Libraries folder into the Libraries file
opened in the first step（the route
is：/home/pi/Downloads/arduino-1.8.19/libraries）.

![](media/a5a59554330ad1cf0408bba19951185d.png)

![](media/f282e39800e13e13cea4282ab56f4bf5.png)

**Step 3:** Unzip the Arduino C package in the libraries folder（for
example：click “Adafruit\_NeoPixel.zip”file
![](media/32bc8a1807feb93288ab4b17104c2d20.png)，select and tap“Extract Here”to unzip the
“Adafruit\_NeoPixel.zip”file.

![](media/b83c834d0eea2ea81cbc6101d80e4714.png)

![](media/883a5a34cf52a300d5721e621b7ece66.png)

![](media/f48bad31121a68e1c3da169baf9bf673.png)
