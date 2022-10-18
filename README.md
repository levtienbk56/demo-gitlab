# demo-gitlab

this tutorial is about to set up a gitlab server on Ubuntu EC2 (v20.04)


## 
```sh
sudo apt-get update
sudo apt-get install -y curl openssh-server ca-certificates tzdata perl
```

get gitlab repo and install some package
```sh
curl https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.deb.sh | sudo bash
```

install gitlab with https protocol (use Let’s Encrypt to get SSL certificate)
```sh
sudo EXTERNAL_URL="https://gitlab.xxx.com" apt-get install gitlab-ce
```

after finishing installation, access `https://gitlab.xxx.com` to confirm.
- username is root
- password is define at `/etc/gitlab/initial_root_password`
NOTE: This file will be automatically deleted in the first reconfigure run after 24 hours

gitlab's config file is located in `/etc/gitlab/gitlab.rb` , and check again `external_url` that is define our URL.
after any change on that config file:
```sh
sudo gitlab-ctl reconfigure
sudo gitlab-ctl restart
sudo gitlab-ctl status
```

