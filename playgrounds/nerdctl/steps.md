- nerdctl is a command line tool for interacting with containerd. 
- This is a killercoda environment and you've docker installed alongwith containerd. 


- First let's run a script to get the version of the nerdctl. 

```
version=$(curl -sI https://github.com/containerd/nerdctl/releases/latest | grep -i "location:" | awk -F"/" '{ printf "%s", $NF }' | tr -d '\r')
```{{exec}}

- Check the version you're using. 
```
echo $version
```{{exec}}

- Now we will use curl to install the nerdctl command line tool. 

```
curl -LO https://github.com/containerd/nerdctl/releases/download/$version/nerdctl-${version:1}-linux-amd64.tar.gz
```{{exec}}

- Now extract this to `/usr/local/bin` 

```
sudo tar -xvf nerdctl-${version:1}-linux-amd64.tar.gz -C /usr/local/bin
```{{exec}}

- Alternatively you can also use arkade to install nerdctl. (preferred as per me)

```
curl -sLS https://get.arkade.dev | sudo sh
arkade get nerdctl 
sudo mv /root/.arkade/bin/nerdctl /usr/local/bin/
```{{copy}}

- You also need to use the CNI plugins for the proper functioning of nerdctl otherwise you will get errors. 

- Get the latest version of the CNI plugin. I'm storing the version with name `cniversion` 

```
cniversion=$(curl -sI https://github.com/containernetworking/plugins/releases/latest | grep -i "location:" | awk -F"/" '{ printf "%s", $NF }' | tr -d '\r')
```{{exec}}
- Now get the plugins by executing the command below 

```
curl -LO https://github.com/containernetworking/plugins/releases/download/v1.1.1/cni-plugins-linux-amd64-$cniversion.tgz
```{{exec}}

- Now extract the following in the `/usr/libexec/cni` directory. 

```
sudo tar -xvf cni-plugins-linux-amd64-$cniversion.tgz -C /usr/libexec/cni/
```{{exec}}

- Now let's try this out with my first container image. 

```
nerdctl run kranurag7/hello-world
```{{exec}}

- Let's try running nginx:alpine 

```
nerdctl run -d -p 8080:80 --name nginx nginx:alpine 
```{{exec}}

- Check the nginx page [here]({{TRAFFIC_HOST1_8080}})