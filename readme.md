# Script auto run every 1 second

```
#!/bin/bash
  while [ "true" ]
   do
        $command
        sleep 30
   done
```
- $command: Your command
- Sleep: time

### *Note* : The script must have the execute privilege 
 ```
 sudo chmod +x script.sh
 ```


# Use script as service

Use the script "script.sh" as a service

```
sudo vi /lib/systemd/system/script_service.service
```

Paste this 
```
[Unit]
Description=My Shell Script

[Service]
ExecStart=/$your_path/script.sh

[Install]
WantedBy=multi-user.target
```

Reload Systemd

```
sudo systemctl daemon-reload 
```

Start service
```
sudo systemctl start script_service.service
```

Enable service to auto run on boot

```
sudo systemctl enable script_service.service
```

Check service

```
sudo systemctl status script_service.service
```
