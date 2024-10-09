---
layout: page
title: "Configuring Docker.*"
subtitle: "on Ubuntu 22.04 LTS"
date:	2024-10-09 10:52:00 +0900
categories: ["ubuntu"]
---

## Installing Docker

### 1. APT update && upgrade && install
{% highlight sh %}
sudo apt update -y && sudo apt upgrade -y
sudo apt install curl ca-certificates apt-transport-https software-properties-common
{% endhighlight %}

### 2. Add GPG Key and Docker Storage
{% highlight sh %}
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | gpg --dearmor | sudo tee /usr/share/keyrings/docker-archive-keyring.gpg > /dev/null
echo "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
{% endhighlight %}

### 3. Install Docker
{% hightlight sh %}
sudo apt update
sudo apt install docker-ce
{% endhighlight %}

### 4. Start Docker Service and Check Version
{% hightlight sh %}
sudo systemctl start docker
sudo systemctl enable docker
sudo docker --version
{% endhighlight %}


## Installing docker-compose

### 1. Download docker-compose
{% highlight sh %}
sudo curl -L "https://github.com/docker/compose/releases/latest/download/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
{% endhighlight %}

### 2. Grant execute permission
{% highlight sh %}
sudo chmod +x /usr/local/bin/docker-compose
{% endhighlight %}

### 3. Check Version
{% hightlight sh %}
docker-compose --version
{% endhighlight %}



## Using Docker without sudo
{% hightlight sh %}
sudo usermod -aG docker $USER
sudo reboot
{% endhighlight %}

