# Steps I made
To be frankly honest with you, I took the lazy way and looked up a [guide](https://computingforgeeks.com/deploy-kubernetes-cluster-on-ubuntu-with-kubeadm/) the Internet. <br>
The majority of the steps I made for setting up the Cluster with kubeadm, followed this Guide. For additional Infos I used the Kubernetes Docu.

<p>But at first I set up the machines, which was a bit of a trip, you can read about in the Monday-Section. </p>

<p>After getting the machines ready, I started to follow the guide. Until the point I reached the kube-init-zone. There I took a break and checked the Documentation and reviewed the Kode Kloud Course for further input.</p>

This is it! The last step. I decided to set a static IP for the API-Server, because Mummshad adviced it in his Course:
 ![picture1](/Images/Bildschirm%C2%ADfoto%202023-02-01%20um%2011.22.10.png)

 I did it!! I started the Master, but unfortunately I killed somehow the ssh-connection to the master:

 ![picture2](/Images/Bildschirm%C2%ADfoto%202023-02-01%20um%2011.33.11.png) 
 
 I have to research the problem, I guess, but stuborn as I am, I took the VCD-Workstation and continued as nothing happend! 

 As already mentioned before, I wanted to try Cilium, and as a little plus I've received the sweet bonus of using helm for deploying.

 ![picture3](/Images/Bildschirm%C2%ADfoto%202023-02-01%20um%2011.51.19.png)

 ![picture4](/Images/Bildschirm%C2%ADfoto%202023-02-01%20um%2011.56.17.png)

 Okay, the Master is sort of up, but instead of joining the nodes, I will get into the ssh-topic. I have some hunchs, but I needed to read some stuff, before making it public.

 Okay, again dropped the plan, researching the ssh-thing! But it is alive!!

 ![picture5](/Images/Bildschirm%C2%ADfoto%202023-02-01%20um%2014.13.47.png)

 Deployed a nginx pod, worked fine. Okay, now I will handle the connection-problem. <br>
 It seems, that the soulution might be very easy. I will try to [deploy an ssh-server](https://www.octopus.com/blog/ssh-into-kubernetes-cluster), so I can connect and don't need to work with the VCD-Console.

 Still didn't working, because there was no External IP:

 ![picture6](/Images/Bildschirm%C2%ADfoto%202023-02-01%20um%2015.44.18.png)

 I have to figure out this topic. Marco gave me the hint, that there is a LoadBalancer-Provider missing. He gave me a link to [MetalLB](https://metallb.universe.tf/) and adviced me to take a closer look on it. <br>
 After inspection I decided to use it and installed with [helm](https://metallb.universe.tf/installation/).

 I started to configure it by creating a yaml-file:

 ![picture7](/Images/Bildschirm%C2%ADfoto%202023-02-01%20um%2017.26.10.png)

 I wasn't quite satisfied with the result, but at least some progress:

 ![picture8](/Images/Bildschirm%C2%ADfoto%202023-02-01%20um%2017.26.57.png)

 I deployed a Nginx-Webserver and exposed it with a LoadBalancer-Service, but I can't access it and I had no idea what is wrong there. I tired a curl on the created service-pod-combo:

 ![picture9](/Images/Bildschirm%C2%ADfoto%202023-02-02%20um%2015.00.20.png)

 Looked good to me. Where is the problem??

 Finally I found the problem, you need to have to be in the same Subnet as the nodes. Didn't knew that.

 Okay, since I can work again with the Mac-Terminal, I was ready to get things done, I wanted to be done.
 I used the K8s Documention to set up Volumes.

 Since I was never a huge fan of the K8s-Docu, I pieced it together, it is of course more elegant to put some of those yamls together, wouldn't never again do it like in this example, but here are some pics of the yamls for the storage: 
 ![storage class](/Images/Bildschirm%C2%ADfoto%202023-02-06%20um%2014.37.22.png)

 ![volume-claim](/Images/Bildschirm%C2%ADfoto%202023-02-06%20um%2014.36.41.png)

 ![configmap](/Images/Bildschirm%C2%ADfoto%202023-02-06%20um%2014.32.32.png)

 ![volume](/Images/Bildschirm%C2%ADfoto%202023-02-06%20um%2014.38.38.png)

 ![deploy](/Images/Bildschirm%C2%ADfoto%202023-02-06%20um%2014.39.10.png)

 ![nodePort](/Images/Bildschirm%C2%ADfoto%202023-02-06%20um%2014.31.37.png)

 Some thoughts, as I told, I peiced it a bit together and that is why we have a lot of yamls around. I took cinder, because it was mentioned in the K8s-Docu and was part of the guide I took.
 Postgresql was taken, because I asked Marco and he mentioned it in a message to my, so I thought: 'Okay, let's give it a shot!'

 Never made it this way, in my courses they took always `local`, so I wanted to use another approach. Also I could have done some things defferent, for example I could have been taken helm instead of configMap, but I used this also to learn and repeat some things. 

Received further tasks from Marco, write a little Spring App and deploy it in the Cluster. Easier said then done. The App and the Image is ready, but deploying seems to get a bit of a ride.
