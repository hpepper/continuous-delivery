# continuous-delivery
Documentation (and tools?) for continuous delivery.



### Providing A build machine

How to let the CI handle the build machines:
* Spinning up its own build machines (how to to it, how to limit the amount of machines?)
  1. Clone build machine
  2. Get the code on it?
* Using pre-existing build machines.

What do I gain from 
What are pro's and cons to cloning ans spinning up build slaves on the fly, in comparison to just create the images and have them sitting idle?
* Sitting Idle takes up CPU time and potential hacking risk?
* By always creating a new build machine we prove that we can re-create the image
  * So once a week, we should delete the base image, just to be sure that it can be automatically created.
* in LXC you get a random address, so it changes on each start-up/power-on anyway.

* Must be able to handle different versions of environments.

Jenkins:
* https://wiki.jenkins-ci.org/display/JENKINS/Docker+Plugin
* https://wiki.jenkins-ci.org/display/JENKINS/Libvirt+Slaves+Plugin
* Someone slave list: https://github.com/giovannimeo/lxc-jenkins-slave

When getting a job:
1. clone to a new build machine, based on the image required, name it after the current build.
  * Can I accidently have ghost machines running?
1. Start it
2. Get the IP address
3. 


* Aminator - cloning? AMI's
  * https://www.youtube.com/watch?v=7oEvlcUMqpE&list=WL&index=3
* Asgaard - 
  *  24:20 spin up new ASG canary it, put a alitle traffic and then spin old ASG down.
* glisten - workflow
  * 28:12
  * 
  

lxc-clone -o u_base -n u_tst
   48  virsh -c lxc:// start u_tst
   49  virsh -c lxc:// list

