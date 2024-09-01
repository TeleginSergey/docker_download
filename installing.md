# Installation

It is **not recommended** to install docker using **apt** or **snap**. When installed using these methods, docker may encounter many issues that are difficult to resolve.

:::

## Installing docker using a bash script

```
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh ./get-docker.sh
```

## Checking the installed version

After installation, it is necessary to ensure that the correct versions of **docker** and **docker compose** have been installed.

- The **docker** version should be at least **25.0.0.**

```
docker --version
```

- The **docker compose** version should be at least **2.24.0**.

```
docker compose version
```

## Granting rights

**It is not recommended** to run **docker** commands with **root** privileges. **docker image** may contain both bugs and
malicious code, running which may lead to system malfunctions, corruption, and leakage of personal data.

```
sudo groupadd docker
```

```
sudo usermod -aG docker $USER
```

```
newgrp docker
```
don't forget reboot docker with this command
```
sudo systemctl restart docker
```

**RELOAD YOUR COMPUTER**
Then you need to restart and check that the following command is executed **WITHOUT root privileges**:

```
docker run --rm hello-world
```

## Network configuration

Only necessary on **linux**-based OS.  Not required on **Mac** and **Windows**.

Change the docker subnet to avoid conflicts with the Sirius Wi-Fi authentication server address. Otherwise, the internet will not work:

```
sudo mkdir /etc/docker &> /dev/null
```

```
echo '{
  "live-restore": true,
  "bip": "172.20.0.1/16",
  "default-address-pools": [{
    "base": "172.20.0.0/8",
    "size": 16
  }]
}
' | sudo tee /etc/docker/daemon.json
```

`"bip": "172.20.0.1/16"` - this changes the docker subnet

After that, restart the docker service and check the settings, the range `172.20.0.0/16` should appear there:

```
sudo service docker restart
docker network inspect bridge
```

## Troubleshooting

Issues may arise during installation on **linux** and **windows**.For example, if **docker** was installed via **apt** or **snap**.

### linux

Check if there are docker packages in snap:

```
snap list --all | grep docker
```

If there are packages, each of them needs to be removed:

```
snap remove docker
```

Then follow all the steps in the article
[completely uninstall docker](https://www.golinuxcloud.com/ubuntu-uninstall-docker/),
restart, and reinstall **docker** via the script.

### windows

Idk, do on linux (better - Ubuntu)
