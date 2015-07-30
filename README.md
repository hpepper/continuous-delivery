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

* Must be able to handle different versions of environments.

Jenkins:
* https://wiki.jenkins-ci.org/display/JENKINS/Docker+Plugin
* https://wiki.jenkins-ci.org/display/JENKINS/Libvirt+Slaves+Plugin
