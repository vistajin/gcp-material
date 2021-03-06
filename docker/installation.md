

### Install
https://docs.docker.com/install/linux/docker-ce/ubuntu/#install-docker-ce-1

~~~sh
sudo apt-get update

sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    software-properties-common
    
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

sudo apt-key fingerprint 0EBFCD88

sudo add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
   $(lsb_release -cs) \
   stable"
   
sudo apt-get update

sudo apt-get install docker-ce

[i forgot to run]apt-cache madison docker-ce

sudo apt-get install docker-ce=18.06.1~ce~3-0~ubuntu

sudo docker run hello-world
~~~

### Uninstall
~~~sh
sudo apt-get remove docker-ce
~~~

### Proxy
sudo nano /etc/systemd/system/docker.service.d/http-proxy.conf
~~~sh
[Service]
#Environment="HTTP_PROXY=http://127.0.0.1:8119/"
#Environment="HTTPS_PROXY=http://127.0.0.1:8119/"
Environment="HTTP_PROXY=socks5://127.0.0.1:1080"
Environment="HTTPS_PROXY=socks5://127.0.0.1:1080"
#Environment="NO_PROXY=localhost,127.0.0.1,m1empwb1.mirror.aliyuncs.com,docker.$
~~~

systemctl daemon-reload
systemctl restart docker
