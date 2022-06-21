## How to run jenkins as different user on ubuntu


### Update below two lines in /etc/default/jenkins file
```
    - replace your username with $USERNAME  
    - In our case we set user as ubuntu.
    
        # default 
        JENKINS_USER=$USERNAME
        JENKINS_GROUP=$NAME

        # updated
        JENKINS_USER="ubuntu"
        JENKINS_GROUP="ubuntu"
```

### Update below two lines in /lib/systemd/system/jenkins.service file

```
    - replace your username with jenkins  
    - In our case we set user as ubuntu.

        # default 
        User=jenkins
        Group=jenkins

        # updated
        User=ubuntu
        Group=ubuntu

```
### Change file ownership of jenkins owned folders.

```
    sudo chown -R ubuntu:ubuntu /var/lib/jenkins
    sudo chown -R ubuntu:ubuntu /var/cache/jenkins
    sudo chown -R ubuntu:ubuntu /var/log/jenkins

```

### After above changes run below command to reload systemctl

```
sudo systemctl daemon-reload

```

### Now you can restart jenkins
```
sudo systemctl restart jenkins.service

```