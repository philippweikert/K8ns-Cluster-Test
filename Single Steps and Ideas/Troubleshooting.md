- I have checked the ports and ips
- I tried different syntactical paterns in ssh
- the Options at kubeadm init have been checked
- configs are checked
- I have tried to establish a ssh-server to connect with it, same problem

I have set up a small vm in my home lab, to check if there is a general problem, since today, can't connect to my homelab from mac-terminal??

I have tried to set up a light-weight at home, ressource-problem, unfortuanetly

I've read in the Kubernetes Docu about services and checked study-material, googled my problem, didn't found a proper solution, even Stack Over Flow let me down

I have to admit, I have no real idea, just a uncertain feeling, what is wrong, need help

update: got an idea, checked routing table (how could I forgot these!) Default-Gateway is set to 0.0.0.0, that doesn't look right, will dig depper tomorrow. Just said, it could be any IP, seems not a big of a deal.

I found with hints from Marco and some try and error the problem with pod connectivity.

Marco gave me some advice to handle the ssh topic, which is still not solved

I have a hintch, but not quite certain what it means, and how to handle it in a proper way. Need to dive deeper.

After digging and not finding anything, I can tell, the best way to fix things is a proper reboot...

I was a bit lazy lately to write down my trouble-shooting-attempts, but I just read things and tried them over and over again and asked for help. I am still not sure what causes the major issue here, so maybe I need help again. 

Velero: I had a problem with the right version of the AWS-Plugin Version, could figure it out, ability to read is 10 of 10 in a modern working environment.

Update to 1.26.2: The problem was, that the config-file wasn't there, so no `kubectl`-commands worked and no contexts. Copied the admin.conf and all was nice. Made a misstake with copy and so it took me longer than assumed. 