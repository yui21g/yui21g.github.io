---
layout: page
title: "Configuring Docker.*"
subtitle: "on Ubuntu 22.04 LTS"
date:	2024-10-09 10:52:00 +0900
categories: ["ubuntu"]
---

## Installing Docker
{% highlight sh %}
# 1. APT update && upgrade && install
sudo apt update -y && \
sudo apt upgrade -y && \
sudo apt install curl ca-certificates apt-transport-https software-properties-common -y && \

# 2. Add GPG Key and Docker Storage
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | gpg --dearmor | sudo tee /usr/share/keyrings/docker-archive-keyring.gpg > /dev/null && \
echo "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null && \

# 3. Install Docker
sudo apt update -y && \
sudo apt install docker-ce -y && \

# 4. Start Docker Service and Check Version
sudo systemctl start docker && \
sudo systemctl enable docker && \
sudo docker --version
{% endhighlight %}


## Installing docker-compose
{% highlight sh %}
# 1. Download docker-compose
sudo curl -L "https://github.com/docker/compose/releases/latest/download/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose && \

# 2. Grand execute permission and Check Version
sudo chmod +x /usr/local/bin/docker-compose && \
docker-compose --version
{% endhighlight %}


## Using Docker without sudo (Optional)
{% highlight sh %}
sudo usermod -aG docker $USER
sudo reboot
{% endhighlight %}

