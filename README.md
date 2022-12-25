# Lock-light-dm-after-suspend
This will help you trigger light-dm just before suspend, hibernate or hybrid-sleep. Thanks to this, after awakening the computer again, the session will be locked.  

# 1.Create dmlock.service at /etc/systemd/system  
~ cd /etc/systemd/system  
~ sudo nano dmlock.service  

# 2.Paste this to the file

---------------------------------------------------------
[Unit]  
Description=DM Lock before suspend/hibernate/hybrid-sleep
Before=suspend.target  
Before=hibernate.target  
Before=hybrid-sleep.target  

[Service]  
ExecStart=/home/ho0lig4n/Scripts/lockscreen.sh  

[Install]  
WantedBy=suspend.target  
WantedBy=hibernate.target  
WantedBy=hybrid-sleep.target  

---------------------------------------------------------  

# 3.Create lockscreen.sh at ~/Scripts  
~ cd /home/user  
~ mkdir Scripts  
~ cd Scripts  
~ sudo nano lockscreen.sh  

# 4.Paste this to the file  

------------------------------------------------------------------
#!/bin/sh  
XDG_SEAT_PATH="/org/freedesktop/DisplayManager/Seat0" dm-tool lock

------------------------------------------------------------------

# 5.Make the script executable  
~ cd ~/Scripts  
~ sudo chmod +x lockscreen.sh  

# 6.Enjoy
