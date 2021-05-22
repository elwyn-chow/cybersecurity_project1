**Question 2: Unsecured Web Server**

We have discovered that one of our virtual machines is running a web server on port 80. This is a problem because we want:
* all of our web traffic to be secure ie use HTTPS protocol and
* run on port 443
* our compliance guidelines require encryption in motion.

In our ELK Project, we allowed HTTP access to the load balancer that was handling all the traffic to three Web virtual machines that were running Damn Vulnerable Web Application. The Web virtual machines were not publicly accessible - HTTP data to and from these machines had to pass through the load balancer.
Those lackadaisical conditions were acceptable because it was a training environment (not a production environment) and we had set our network security group's inbound rules such that only my personal laptop's IP address could connect to the Jump Box Provisioner machine (for configuring docker and running docker to setup the Web VMs) and the Load Balancer. 

In a production environment, the solution to the problem would be:
* block all inbound traffic on port 80
* turn off the HTTP server and disable it such it does not restart at reboot
* the load balancer would have to changed such that it is publicly accessible to any user but only on the correct port 443
* a HTTPS server needs to be running on port 443 of each Web virtual machine and the data needs to be encrypted appropriately
* obtain HTTPS certification so users don't get that annoying warning about a web site being uncertified. We can obtain [free SSL certification from CloudFlare](https://www.cloudflare.com/ssl/?&_bt=488025616931&_bk=ssl%20certificate&_bm=e&_bn=g&_bg=113915058632&_placement=&_target=&_loc=9071836&_dv=c&awsearchcpc=1&gclid=Cj0KCQjw16KFBhCgARIsALB0g8LUZcO_GQzeitoXNCCPXeR7nhDZN3hH1stTWrD9VBmFpWP9XhcqmkYaAhbFEALw_wcB&gclsrc=aw.ds) and [instructions on how to make the transition from HTTP to HTTPS](https://www.smashingmagazine.com/2017/06/guide-switching-http-https/)

To adapt Project 1, I would:
* change the ansible playbook file such it no longer uses Damn Vulnerable Web Application
* change the ansible playbook file such that it uses Apache and implements the certification requirements (I would adapt these [instructions](https://dockerwebdev.com/tutorials/docker-php-development/) to the ansible playbook.)

The main disadvantages of the change will be that clients that expect to communicate with port will break. Since we have blocked all communication to port 80, we can't even send the clients a redirect message to the HTTPS version of the URL.

Furthermore, we should maintain our SSL certificate. This isn't a huge ongoing maintenance task but it will be periodical. SSL certificates may not last longer than 27 months. We should change it every two years.

The advantages are that all communication will be encrypted.
