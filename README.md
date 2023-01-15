# Step #01: Server update and upgrade then add repo.

```bash
root@gitlab-ce:~# lsb_release -d && ip r
```

```bash
root@gitlab-ce:~# apt update && apt upgrade -y
```

```bash
root@gitlab-ce:~# apt install -y ca-certificates curl openssh-server tzdata
```

```bash
root@gitlab-ce:~# curl -fsSL https://packages.gitlab.com/gitlab/gitlab-ce/gpgkey| sudo gpg --dearmor -o /etc/apt/trusted.gpg.d/gitlab.gpg
```

```bash
root@gitlab-ce:~# vi /etc/apt/sources.list.d/gitlab_gitlab-ce.list
```

- Add below line into source list file.

```bash
deb https://packages.gitlab.com/gitlab/gitlab-ce/ubuntu/ focal main
deb-src https://packages.gitlab.com/gitlab/gitlab-ce/ubuntu/ focal main
```

# Step #02: Then run main command.

```bash
root@gitlab-ce:~# apt update
root@gitlab-ce:~# apt install gitlab-ce
root@gitlab-ce:~# vi /etc/gitlab/gitlab.rb
```

- Add your server ip address into rb file.

#### external_url '192.168.1.5'

# Step #03: Then configure gitlab-cli

```bash
root@gitlab-ce:~# sudo gitlab-ctl reconfigure
```

- Check status using below command.

```bash
root@gitlab-ce:~# gitlab-ctl status
```

- Collect root password from below command.

```bash
root@gitlab-ce:~# cat /etc/gitlab/initial_root_password
```

- Check below command for manage GitLab.

```bash
root@gitlab-ce:~# gitlab-rake gitlab:check
root@gitlab-ce:~# gitlab-ctl status
root@gitlab-ce:~# gitlab-ctl stop
root@gitlab-ce:~# gitlab-ctl start
root@gitlab-ce:~# gitlab-ctl restart logrotate
```

## Create SSH Key

```bash
ssh-keygen -t ed25519 -C "Gitlab Key Pair"
cat ~/.ssh/
cat ~/.ssh/id_ed25519.pub
ssh -T git@gitlab.com
```

### GitLab Runner Linux

```bash
sudo curl -L --output /usr/local/bin/gitlab-runner "https://gitlab-runner-downloads.s3.amazonaws.com/latest/binaries/gitlab-runner-linux-amd64"
```

```bash
cd  /usr/local/bin
ls
```

```bash
sudo chmod +x /usr/local/bin/gitlab-runner
ls
```

```bash
sudo useradd --comment 'GitLab Runner' --create-home gitlab-runner --shell /bin/bash
```

```bash
sudo ./gitlab-runner install --user=gitlab-runner --working-directory=/home/gitlab-runner
```

```bash
sudo ./gitlab-runner start
```

```bash
sudo ./gitlab-runner status
```

```bash
sudo cat /etc/systemd/system/gitlab-runner.service
```

```bash
sudo ./gitlab-runner register
```

```bash
sudo ./gitlab-runner verify
```

### Container Registry

```bash
docker login registry.gitlab.com
```

```bash
docker login registry.gitlab.com -u name -p mypassword
```

```bash
docker build -t registry.gitlab.com/gitlab-container-register-example/alpinegitlab:test
```

```bash
docker push registry.gitlab.com/gitlab-container-register-example/alpinegitlab:test
```

## Other resources

- [Install GitLab Runner manually on GNU/Linux](https://docs.gitlab.com/runner/install/linux-manually.html)
- [Registering runners](https://docs.gitlab.com/runner/register/index.html)