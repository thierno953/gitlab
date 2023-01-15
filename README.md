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
