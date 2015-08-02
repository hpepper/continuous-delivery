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
* 
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


* Plugins
    * Green Balls
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
    * Windmill
    * Selinium
* Continuous deployment/delivery
    * SAAS
