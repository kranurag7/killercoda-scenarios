- Install Arkade on the given system 

`curl -sLS https://get.arkade.dev | sudo sh` 

- Add the path in your *.bashrc*

`export PATH=$PATH:/usr/local/bin`

- Make sure arkade is installed. Run the command 
  
`arkade version`{{exec}}

### Install command line tool 

- Check what all command line tools you can install with the command `arkade get` 
- Let's Install `kubens` command line tool 

`arkade get kubens` 

- By default all the arkade binaries will get installed in `~/.arkade/bin` directory so put this in the path variable. Add the below line to your *.bashrc*

`export PATH=$PATH:$HOME/.arkade/bin/`

- Change the active namespace to *kube-system* by running the command 

`kubens kube-system` 

### Install kubernetes application 

- Check all the applications you can download with `arkade install --help` 
- Let's Install `kyverno` application in your cluster 

`arkade install kyverno` 

- Check if kyverno is installed or not

`kubectl get ns` 
- You should see the kyverno namespace. 

### Install system packages

- Let's install golang on the system now. 

`arkade system install go` 

- Add this to the *.bashrc* file.

`export PATH=$PATH:/usr/local/go/bin:$HOME/go/bin
export GOPATH=$HOME/go/`

- Check if go is installed correctly 
- Run the command `go version` 

- Try exploring more of Arkade. Install something else apart from what I have installed above and have fun. 