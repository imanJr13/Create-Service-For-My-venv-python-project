# Create-Service-For-My-venv-python-project
# Here is how to make service for my project in python venv

# for this go to make a service file in your linux

```
vim /etc/systemd/system/my-python-project.services

```
and put below confis in file 

```
Description=generate-log
Wants=network-online.target
After=network-online.target

[Service]
Type=simple
WorkingDirectory=/data/users/appuser/generate-log
Environment=VENV_PATH=/data/users/appuser/generate-log/venv/bin
ExecStart=/bin/sh -c 'cd /data/users/appuser/generate-log && source venv/bin/activate &&  python -u run_generate_log.py'
ExecStop=/bin/kill -TERM ${MAINPID}
Restart=always


[Install]
WantedBy=multi-user.target
```

next type below command to enable and start service

```
systemctl enable generate-log

systemctl start generate-log
```
