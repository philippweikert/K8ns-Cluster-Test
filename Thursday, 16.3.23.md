# Daily summary from Thursday

- I decided to renew the whole ingress thing, not best practice, but I wan't it running
- first I wanted to perform an update to kubeadm 1.26.2
- then I purged the ingress and replaced it
- then I wanted to make some changes in my role-concepts, so I wanted to change my auth-concept

- first step done update performed...using 1.26.2 right now
- was a bit of a struggle, because context weren't set on the workers

- the conclusion of the ingress-change is, that it might be a DNS-Problem, not a general ingress-topic
- I needed to get deep into DNS-topic, something is there strang with the resolving-structure, need to understand this first

- unfortuanetly this consumed so much time, that I wasn't able to handle the rolebinding-issue anymore today