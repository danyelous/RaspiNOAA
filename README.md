# RaspiNOAA
# Here is how I manage to get my RaspiNoaa working

# Step 1: Raspberry Pi
I got a Raspberry Pi 3 Model B, and I wanted to used on something useful to me. So, investiganting and relatend to my TinyGS projects I came across the RaspiNoaa project: 
https://github.com/jekhokie/raspberry-noaa-v2
This project is to automatically capture NOAA images with a Raspberry Pi.

Right now I got the V2 running

With this project is possible to get NOAA weather images from satellites directly.

# Step 2: Get RaspiNOAA installed

You can follow the steps here: https://github.com/jekhokie/raspberry-noaa-v2
Basically, is an image to download and install on a SSD

# Step 3: RTL-SDR
You need a RTL-SDR and an antenna. I got this setup
https://es.aliexpress.com/item/1005005952566458.html?spm=a2g0o.productlist.main.9.73037Vv77Vv7un&algo_pvid=4378c0c9-e112-4920-8057-5393aff4fcd8&algo_exp_id=4378c0c9-e112-4920-8057-5393aff4fcd8-4&pdp_npi=4%40dis%21USD%2141.95%2141.95%21%21%2141.95%2141.95%21%402101fb1017140093522827229e77be%2112000035000699472%21sea%21AR%21196052428%21&curPageLogUid=H1YRA4YYzvUS&utparam-url=scene%3Asearch%7Cquery_from%3A

Be careful, there are imitations, I got it from the official store to avoid errors. RTLSDRBlog Store (https://www.aliexpress.com/store/4523039?spm=a2g0o.order_list.order_list_main.12.3c11194d50ugUD)
and installed the antenna on my roof.
The cable goes to the interior of my house where I got the raspberry pi installed.

# Step 4: Setup

Once you have the SSD with the RaspiNOAA installed and runnning on your Raspberry Pi, and the RTL-SDR plugged in on the USB with the antenna connected, run this setup on the Raspberry Pi
(as it is explained here https://github.com/jekhokie/raspberry-noaa-v2 )

# update os localisation settings like timezone, locale and WiFi country
sudo raspi-config

# install git
sudo apt install git -y

# clone repository
cd $HOME
git clone https://github.com/jekhokie/raspberry-noaa-v2.git
cd raspberry-noaa-v2/

# Edit settings to match your stations location, gain and other things
nano config/settings.yml

With no filter or LNA, i found 48 to be the better gain value

# perform install
./install_and_upgrade.sh

for evey change in the settings.yml a ./install_and_upgrade.sh and reboot is recommended.

At this point, if you access your Raspberry Pi IP with a browser inside you local network, (Ex: http://192.168.0.160/ ) you will be able to see the satellites tracking and image captures.
This is great, because the RaspiNOAA will automatically capture it for you.

There are a lot of channels and videos explaining how to do this. But, one of the most interesting I found is this one:
https://www.youtube.com/@saveitforparts (Save it for parts channel)

# Step 5: If needed, remote access
If you got a CloudFlare agent running on the same local network (check my other repository: https://github.com/danyelous/Proxmox ) be creating a tunnel you will be able to access your RaspiNOAA from Internet







