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