# FarcasterNode
## For running the node we willll need:

- A Farcaster account. Below you will find detailed instructions on how to create it;
- An Alchemy account. Below you will also find detailed instructions on how to create it;
- Server;
- Necessary software to interact with the server.
  
The total cost of the node is ~20$, of which you will spend 5$ to create an account. The cheapest server will cost 1400 rubles/month on hosting xorek.cloud

**Recommended server requirements from the official Farcaster documentation:**

- 4 CPU(CPU cores);
- 16 GB RAM(RAM);
- 200 GB of free storage on the server;
- Ubuntu 20.04 operating system

### Let's move on to creating an account on Farcaster.

1. Follow the link and click on the "Sign up" button : https://warpcast.com/
2. Next, scan the QR code to download the app to your mobile device. Further installation will be shown on iPhone, but I don't think the installation is much different on Android devices.
3. Once Warpcast is installed on your mobile device, open it and click on the "Create account" button.
4. Next, the creation of your account will begin. Please note that the account is linked to the generated seed phrase, which must be saved. Otherwise, you will lose access to your account.
5. Next you need to save the generated seed phrase and click on the button "I backed up my recovery phrase". On the next step enter your email to complete the registration.
6. You will receive an email with registration confirmation. Confirm registration by clicking on the link, and then pay for the account creation ($5).

Then you can return to your PC, as it is more convenient for further interaction. Open https://warpcast.com/ and click on the "Log in with email" button.

Next, we authorize and get to our profile. At this stage, the Farcster account registration is complete. Open a window with a notepad on your PC to write down the necessary data for setting up the node. We will need Farcaster ID (FID).  Get it by clicking on the buttons as on the screenshot.

Then copy the FID and paste it into notepad to keep it handy.

Let's move on to installing the necessary software to interact with the server. I will use MobaXterm. You can download it by clicking on the link and selecting the "Home Edition" version.

Then you will need to click on the "Download now" button, then on the next page select "Installer edition". This will start downloading the software. Once the download is complete, run the installer and install MobaXterm. I will not describe this in detail, as I already have MobaXterm on my PC + the installation is very simple.

Great, before ordering the server we need to set up an account in Alchemy to properly configure the node. Go to https://www.alchemy.com/ and click on the "Sign in" button. You will be redirected to the registration page

After registration you will be taken to the home page.

Click "Apps" on the left.

Create a new application.

Fill in the fields. Specify Ethereum Mainnet, and fill in the name and description fields as desired.

Let's save our RPC to notepad. To do this, click on "API key."

Copy the HTTP field and paste it into Notepad. 

Let's create Optimism App by analogy.

Click on "API key".

Save HTTP to Notepad.

**All the basic components are ready, let's move on to renting a server.**

I will be conducting a test installation of the node on the server from aeza.net hosting.

Open MobaXterm, click on the "Session" button.

You will see such a window as on the screenshot below. You need to click on the "SSH" button.

In the field "Remote host" enter the IP address of your server and click "OK".

This window will open. Click "Accept".

In the "login as: " field enter the login to your server. Usually it is always equal to "root" and is located in your personal cabinet on the hosting.

Press "Enter" and enter the password from the server, it is also specified in your personal cabinet on hosting. Important note: the password can not be inserted by the key combination "CTRL+V", it must be inserted by pressing the right mouse button. The password will not be displayed in your field, because it is hidden for security. If you have inserted everything correctly, then press "Enter" and get to the server, having previously pressed "No" in the opened window.

This is how your connection to the server looks like below. It may be different from mine.

Next will come the installation commands. Insert them also by clicking on the right mouse button.

```
sudo apt update -y
```

The server software will be updated.

Next, let's install screen. This is a utility that allows you to run processes in the background. To do this, enter the command below.

```
sudo apt install screen -y
```

Let's check the installation with the command below.

```
screen --version
```

The server will display the version of the utility.

Let's start a background process to install the script from Farcaster. Use the command below.

```
screen -S Hubble
```

You will see a blank page, don't be alarmed. That's the way it should be. You have just launched the Hubble background window. Let's move on to installing the script itself.

```
curl -sSL https://download.thehubble.xyz/bootstrap.sh | bash
```

It will start something similar to the screenshot below. Wait for the installation.

Once everything is installed, you will see this window with the input "Ethereum Mainnet RPC URL". Paste by right-clicking the HTTP from Ethereum App, which you copied into Notepad from Alchemy. Then press "Enter".

Insert Optimism RPC in the same way.

Then insert the FID and press "Enter". The installation will start.

Then the node synchronization will start. It will take about one hour and will finish when the value on the left is equal to the value on the right, as in the screenshot below. I'm going to go have a snack for now and I suggest you do the same :)

After getting the snapshot, another synchronization will start. Waiting.

Waiting for Hubble to launch.

As soon as Hubble launches, you will have logs going. They will run continuously. Don't worry, this is the way it should be. In the logs you can see two statuses - error and successful. This is the way it should be.

Once the synchronization is complete, go to the browser window and in the URL field type <IP address of the server:3000>. Example: "91.109.201.5:3000". This will open the Grafana monitoring panel.

In this panel you can monitor the status of your node.

### At this point, the Farcaster node installation is complete.


