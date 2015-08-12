# continuous-delivery
Documentation (and tools?) for continuous delivery.

* Cycle time: from change to delivery to the customer.
* 
References:
* http://ant.apache.org/ivy/ - The agile dependency manager
* http://fitnesse.org/ - The fully integrated standalone wiki and acceptance testing framework
* http://www.youtube.com/watch?v=KH2_sB1A6lA - Tools for Continuous Integration at Google Scale

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
#### Allow jenkins to administrate LXC instance through a deamon running as root

In order to allow Jenkins to start instance for e.g. 

* Make sure that it is the 'right' originator(jenkins) of the request.
  * Perhaps using a key.
  * Possibly only listen on the localhost network.
* Possibly using wt?
* Operations needed:
  * Create
  * Start
  * Stop
  * Destroy
  * Status
    * Running/stopped
    * IP address(s)
    * 
  * What kind of Web interface is Amazon providing? Possibly use the same kind of methods?

lxc-clone -o u_base -n u_tst
   48  virsh -c lxc:// start u_tst
   49  virsh -c lxc:// list

# Deploymnet pipeline
Loc617

* Commit stage
  * Compile
  * Unit test
  * Analysis
  * Build installers
  * Put binaries in repo
* Automated acceptance testing
* Automated capacity testing
* Manual testing
* Release


## Commit stage

### Compile

* C:
  * gcc
  * clang?
* Unit test
  * C/C++
    * CxxUnit
    * check
* Analysis
  * Security
  * McCabe
    * Sonar module: 
  * Code Coverage
    * Sonar module: 
  * Code Copy
    * Sonar module: 
  * Lint
  
## CI Roll-out

See: [http://www.youtube.com/watch?v=q5_VzA9k29E|Continuous Integration with Jenkins CI (Ladder)]

* Install and configure Jenkins
  * One time setup of master server.
  * Flexibility for your development/operations environment.
* Automated build
  * Build your source on every commit.
  * Early and often integration of source code.
  * Scheduble for appropriate timing
* Unit and integration test
  * Testing accross multiple code modifications
  * Early test failure information
  * Reporting: Pass/Fail and Trends
  * Tests are repeatable
  * Early detection of bugs is worth a lot in the end.
* Reporting and metrics
  * Clearly indicates progress
  * Product quality and Non Functional requirements
  * Improve visibility and decision making
  * Help understand maintainability of code base
  * Trends can indicate systemic issues in governance/process
* Distributed builds
  * Fast, fast, Fast
  * Robust, no single point of failure
  * Multiple platforms and versions
* Functional testing
  * Reporting: Consistent and timely PasS/Fail and Trends
  * Test are repeatable
  * Detect bugs and help to prevent their reintroduction
  * regression testing
  * Reduce risk in a way business users understand
* Continuous deployment/delivery
  * Reduce risk of releasing software
  * Validate how good your business plan is, much more quickly.
  * Get real feedback  on the progress of their projects.


### Install and configure Jenkins

#### Jenkins master

* https://wiki.jenkins-ci.org/display/JENKINS/Distributed+builds

* Plugins
    * Green Balls
      * http://updates.jenkins-ci.org/latest/greenballs.hpi
* Testing plugins
    * TestNG
    * Mozmill
    * Gallio
    * Japex
    * Nunit
    * xUnit
* Report and metric plugins
    * Code analysis
    * Console sections
    * Log parser
    * Performance
    * Statistics
    * Section view
    * Timestamper
    * warnings
    * Sonar
* Functional test
    * Enviject
    * Windmill - http://www.getwindmill.com/
    * Selinium
* Continuous deployment/delivery
    * SAAS
* Version control
  * https://wiki.jenkins-ci.org/display/JENKINS/archive-files-scm-plugin
  * https://wiki.jenkins-ci.org/display/JENKINS/ClearCase+Plugin
  * https://wiki.jenkins-ci.org/display/JENKINS/Config+Rotator+Plugin
  * https://wiki.jenkins-ci.org/display/JENKINS/Git+Plugin
    * Requires 
      * scm-ap
      * git-client - https://wiki.jenkins-ci.org/display/JENKINS/Git+Client+Plugin
    * http://code.hootsuite.com/how-to-make-jenkins-play-nicely-with-git/
  * https://wiki.jenkins-ci.org/display/JENKINS/Tracking+Git+Plugin
  * https://wiki.jenkins-ci.org/display/JENKINS/Pretested+Integration+Plugin
* Jenkins control
  * https://wiki.jenkins-ci.org/display/JENKINS/Accelerated+Build+Now+Plugin
  * https://wiki.jenkins-ci.org/display/JENKINS/Build+Flow+Plugin
  * https://wiki.jenkins-ci.org/display/JENKINS/FLOW+Plugin
    * http://startflowing.net/
  * https://wiki.jenkins-ci.org/display/JENKINS/Join+Plugin
  * http://rundeck.org/
  * https://wiki.jenkins-ci.org/display/JENKINS/Disk+Usage+Plugin
* Artifact db
  * http://hackers.lookout.com/deploydb/
* Triggers
  * https://wiki.jenkins-ci.org/display/JENKINS/Gerrit+Trigger
  * https://wiki.jenkins-ci.org/display/JENKINS/ScriptTrigger+Plugin
  * https://wiki.jenkins-ci.org/display/JENKINS/XTrigger+Plugin
* Slave control
  * https://wiki.jenkins-ci.org/display/JENKINS/Libvirt+Slaves+Plugin
  * https://wiki.jenkins-ci.org/display/JENKINS/Swarm+Plugin
* Jenkins CI
  * https://wiki.jenkins-ci.org/display/JENKINS/The+Continuous+Integration+Game+plugin
* Jenkins administration
  * https://wiki.jenkins-ci.org/display/JENKINS/thinBackup
  * https://wiki.jenkins-ci.org/display/JENKINS/DiskCheck+Plugin

### Installing a artifact repository
Deploy seems to be the name for uploading artifacts to the repo.

Build Artifact Repository 
* https://dzone.com/refcardz/binary-repository-management
* https://en.wikipedia.org/wiki/Binary_repository_manager
* https://github.com/teamfruit/defend_against_fruit/wiki/When-To-Use-A-Build-Artifact-Repository
 

Candidates:
* https://archiva.apache.org/index.cgi
  * http://stackoverflow.com/questions/22479847/deploy-from-jenkins-to-archiva-steps
  * http://stackoverflow.com/questions/15010016/deploy-artifact-from-jenkins-to-archiva-with-nant
  * http://evertrue.github.io/blog/2014/07/21/setting-up-an-archiva-repository/
  * https://archiva.apache.org/docs/2.2.0/userguide/deploy.html
* http://www.sonatype.org/nexus/
* https://wiki.jenkins-ci.org/display/JENKINS/ArtifactDeployer+Plugin
* http://www.avajava.com/tutorials/lessons/how-do-i-deploy-an-artifact-to-an-archiva-repository.html
* Initial version
  * scp with keys/host thing, so there is a jenkins account on the artifact machine and use the homedir for the storage
    * no metadata; deps etc.
    * can be overwritten.
  * Use an http server to get the bins on a build machine
    * No login so everyone can read the data :-(

*

# XORP as an example

## Core XORP

* Automated build
* Developer started build.
* How to split out in multi-threaded paths
  * Do deliver build and UT build at the same time/in parallel.
* Lint ?
* Build for multiple platforms: Ubuntu, Fedora 20, RedHat 6.6

## XORP installation package with configuration files.

* test ping
* Test multicast
