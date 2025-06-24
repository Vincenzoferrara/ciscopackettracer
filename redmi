#create distrobox container debian with systemd and network separate network

distrobox-create \
  --name cisco-packet-tracer \
  --image debian:12 \
  --init \
  --unshare-netns \
  --additional-packages systemd

#enter on terminal systemd
distrobox enter cisco-packet-tracer

##install dipendece cisco:
sudo apt update && sudo apt dist-upgrade -y
sudo apt install libqt5multimedia5 libqt5xml5 libqt5script5 libqt5scripttools5 libqt5sql5 \
xdg-utils libnss3 libxss1 libasound2 libxslt1.1 libxcb-xinerama0-dev -y

#dowload deb file on site cisc

#install file deb (the file name must be exactly Packet_Tracer.deb if not and rename it)
sudo dpkg --install Packet_Tracer.deb

#tested program
packettracer

#if the file does not open or gives packetti error use
sudo apt --fix-broken install
#and reinstall aket tracer
sudo dpkg --install Packet_Tracer.deb

#to start packet tracer directly from the application menu without having to enter the doker cli
#this will create an entry in the application menu with the name cisco packet tracer that will start the container and start the program
distrobox-export --app packettracer


#to avoid future errors of incompatible dependencies, i recommend creating a systemd file to disable internet. so as not to have problems updating.

#find the name of your network card in my case enp4s0, it could also be called eth0
ip -a


#create file systemd
sudo nano /etc/systemd/system/disable-internet.service

#copy and paste (replace enp4s0 with the name of your network card)

[Unit]
Description=Disable network interface at boot
After=network.target

[Service]
Type=oneshot
ExecStart=/sbin/ip link set enp4s0 down
RemainAfterExit=yes

[Install]
WantedBy=multi-user.target

# exit with ctrl + x 

#activate systemd at boot
sudo systemctl daemon-reload
sudo systemctl enable disable-internet.service
sudo systemctl start disable-internet.service


#now everything should be complete. restart your pc and check if when you start the program it starts without errors.

#This guide was written with Google Translate from Italian to English, if you want to improve the translation open an issue, report any errors you find


