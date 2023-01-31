# Daily summary
I experienced some issues today regarding the VM handling.
- the | was configured on Win-Setup, it took me a while to recognize this,  didn't received   error-messages until I tried a different approach to set the packages
- had troubles with ssh-connection to the VMs, checked all configs, couldn't find the error
- it turns out, that I used the wrong syntax for connection, after trial and error I fixed that
- had trouble to add the needed repos, used different syntax, turns out didn't used | 

What have I done:
- I added the packages
- I installed the packages
- turned off swap
- worked out some errors I made, like discribed in the section before
- enabled Kernel Modules (overlay, br_netfilter)
- runtimes are installed, I decided for CRI-O, never used it before, wanted to try it out (used containerd on my own Lab and Docker is Docker)

All the Packages are installed now and the VMs are set to become part of a Cluster.

I decided to split my day, so I will continue tommorrow setting up the Cluster and will do some excercies after Lunch
