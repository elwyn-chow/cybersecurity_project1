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
* we should obtain HTTPS certification. We can obtain [free SSL certification from CloudFlare](https://www.cloudflare.com/ssl/?&_bt=488025616931&_bk=ssl%20certificate&_bm=e&_bn=g&_bg=113915058632&_placement=&_target=&_loc=9071836&_dv=c&awsearchcpc=1&gclid=Cj0KCQjw16KFBhCgARIsALB0g8LUZcO_GQzeitoXNCCPXeR7nhDZN3hH1stTWrD9VBmFpWP9XhcqmkYaAhbFEALw_wcB&gclsrc=aw.ds)


3. Explain the Solution Requirements
   
    - How would you reconfigure a server to serve HTTP traffic safely?
    - How does this solution fix the problem?

4. Explain the Solution Details
    - Which tools and technologies would you use to implement this solution in Project 1?
    -  How, specifically, would you use these tools to harden your deployment?

5. Identify Advantages and Disadvantages of the Solution
    -  Will your solution break clients that used to communicate with the server over port `80`?
    -  Do you have to do any work to keep this solution running longterm? Or can you simply "set it and forget it?”
