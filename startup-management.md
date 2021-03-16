# Startup management  

In linux we have three ways to manage services: systemd , services and init.d  
First option is the recommended one, there are other daemons but systemd is the most used one, you can use it with sudo systemctl and pass certain arguments, for example if you do ``` sudo systemctl status ``` it will list you all the services and their status. If you need to check on the status of certain service you need to specify its name like ``` sudo systemctl status apache2 ``` also not only status we can use other commands like restart, stop, start, and to start a service on startup or disable it we use the commands enable and disable.  

To create a new service, you need to ``` cd /etc/systemd/system ``` and create a new file with the format newservice.service. In this file the syntax and needed blocks are the following:  

```c
[Unit] // this block is not requiered
Description=My service 
After=network.target // specify dependencies

[Service] // this is totally requiered
ExecStart=/home/ubuntu/script.sh
Restart=always
WorkingDirectory=/home/ubuntu/
User=ubuntu
Group=ubuntu
Environment=ENVVAR=envvalue

[Install]
WantedBy=multi-user.target // with this you also specify you want it to be available on startup by multi.user

```

After changing configurations always restart the configured service or if you do global changes you can do ``` sudo systemctl daemon-reload ```  
  
There is two more ways but the result will be almost the same and they are not as comfortable as this way in my opinion. One is ``` sudo services apache2 stop/restart/start/reload ``` and the other is directly in /etc/init.d/ having a file with the name of the service you need, for example apache2, and you interact with it like an executable, for example ``` sudo /etc/init.d/apache2 stop ``` and so on.  
