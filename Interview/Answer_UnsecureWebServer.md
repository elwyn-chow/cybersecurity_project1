## Activity File: Interview Questions

- This first project covers a wide range of topics including cloud, network security, and logging and monitoring.

- When networking and talking to potential employers, you should be able to reference the work done on this project to answer specific interview questions or demonstrate your skills within a specific domain. 

- You will choose a domain that you're interested in pursuing as a career and answer mock questions based on the suggested response format. 
​
### Instructions 

1. Choose one of the following domains:
    - Network security
    - Cloud security
    - Logging and monitoring

    If you are unsure of which domain you want to focus on, that's okay. You can either choose the one you're most comfortable discussing, or complete the tasks in two or all three domains.

2. Select one domain and one question. 

    - Questions are provided for each domain. Choose one to answer from your chosen domain. 
​
3. Write a one-page response that answers the question using specific examples from your work on Project 1. Your response should flow and read like a presentation while keeping the general structure of the technical question response guidelines. 

    You will submit this one-page response. 

#### Reminder: Response Guidelines
As a reminder,  good responses do the following. 
​
1. Restate the problem.
2. Provide a concrete example scenario.
3. Explain the solution requirements.
4. Explain the solution details.
5. Identify advantages and disadvantages of the solution​.
​
Including each of these components will ensure you prove your competency of subject matter and critical thinking. 
​
### Interview Questions by Domain

Below you will find a list of questions, grouped by specific domains. Select one question to answer. 
​ 

For each question, where appropriate, we have provided you with specific prompts to consider as you structure each section of your response. Feel free to use these prompts or your own examples. 

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
* a HTTPS server needs to be running on port 443 of each Web virtual machine


3. Explain the Solution Requirements
   
    - How would you reconfigure a server to serve HTTP traffic safely?
    - How does this solution fix the problem?

4. Explain the Solution Details
    - Which tools and technologies would you use to implement this solution in Project 1?
    -  How, specifically, would you use these tools to harden your deployment?

5. Identify Advantages and Disadvantages of the Solution
    -  Will your solution break clients that used to communicate with the server over port `80`?
    -  Do you have to do any work to keep this solution running longterm? Or can you simply "set it and forget it?”