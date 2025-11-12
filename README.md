# Implementation of Application Load Balancer project

## Indroduction

In today’s online world, websites and apps need to be available, reliable, and able to handle a lot of users at the same time. A Load Balancer helps make this possible by spreading traffic across different servers. In this project, we will learn how an Application Load Balancer (ALB) works by setting up a real example where it shares incoming traffic between multiple servers like EC2 instances or containers.

This project showcases the deployment of an Application Load Balancer (ALB) on AWS by launching three EC2 instances, each representing a different service: Home, Laptop, and Mobile. Three separate target groups are created and associated with these instances. The ALB is then set up to route incoming traffic to the appropriate target based on predefined rules. Finally, the DNS name of the ALB is obtained and tested to confirm that traffic is being properly distributed among the instances.

### Project Highlights


1] Three EC2 Instances: In this project, we launch three EC2 instances, each running an Apache web server. To make each server unique, we use a User Data script that customizes the index.html page with different content for each one — labeled Home, Laptop, and Mobile.

2] Target Groups:
We create three separate target groups, assigning each EC2 instance to its own group. This setup ensures that traffic can be routed individually to the Home, Laptop, and Mobile servers.

3] Application Load Balancer (ALB):
An Application Load Balancer is then set up and linked to all three target groups. The ALB is configured to distribute incoming traffic based on routing rules. To verify everything is working correctly, we access the DNS name of the ALB in a browser and check that traffic is being directed to the correct server.

## Steps of Implementation

### Step1: Launch 3 instance Home, Laptop, Mobile.

* Click on "Launch Instances" to start creating servers.

* Name your first Instance "Mobile".

* Choose a key pair so you can connect to the server later.

* Select a security group to allow internet access (like HTTP or SSH).

* Scroll down and click on "Advanced Details".

* Find the "User Data" box and paste your script there (this sets up the server automatically).

* Set the "Number of Instances" to 2 so that two servers will be created at the same time.

<p><img src="Images/Screenshot 2025-09-18 145839.png" alt="Instance"></p>


* Create a Second instance "Laptop" same as first instance

* Find the "User Data" box and paste your script there as shown below

<p><img src="Images/Screenshot 2025-09-18 150136.png" alt="Instance"></p>

* Create a Third instance "Mobile" same as first instance

* Find the "User Data" box and paste your Mobile script Same as Laptop



* Now, we Launch the Instances like Home, Laptop & Mobile


<p><img src="Images/home.png" alt="Instance"></p>


<p><img src="Images/lap,mo.png" alt="Instance"></p>









### Step 2:  Create Target Groups

* Create 3 target groups in AWS console. Register each EC2 instance to its respective target group

* Go to the Target Groups

<p><img src="Images/TG create.png" alt="Instance"></p>

* Create three target groups

<p><img src="Images/TG.png" alt="Instance"></p>


### Step 3: Create Application Load Balancer

 * Click on load balancer

<p><img src="Images/1.png" alt="Instance"></p>


 * Select Application Load Balancer and click on create

 <p><img src="Images/2.png" alt="Instance"></p>

 * Put Load Balancer name like ALB

 <p><img src="Images/3.png" alt="Instance"></p>

 * Select all AZ's

 <p><img src="Images/4.png" alt="Instance"></p>

 * Select Exsisting Security Group which allows port 80 & port 22

  <p><img src="Images/5.png" alt="Instance"></p>

 * Click on create target groups

  <p><img src="Images/6.png" alt="Instance"></p>


  * Specify all group details

   <p><img src="Images/7.png" alt="Instance"></p>

  * Put Health check path for home is /

<p><img src="Images/8.png" alt="Instance"></p>

  * Then select the both home targets for register targets

<p><img src="Images/9.png" alt="Instance"></p>

  * Same target group create for Laptop 

  * Put health check path for laptop is /Laptop/

  *  Then select the both Laptop targets for register targets

<p><img src="Images/10.png" alt="Instance"></p>

  * Same target group create for Mobile

  * Put health check path for laptop is /Mobile/

<p><img src="Images/11.png" alt="Instance"></p>

*  Then select the both Mobile targets for register targets

<p><img src="Images/12.png" alt="Instance"></p>


* Then Add a Home target group on the Load balancer


<p><img src="Images/13.png" alt="Instance"></p>

* Now, Click on load balancer

<p><img src="Images/14.png" alt="Instance"></p>

* Sucessfully created a load balancer

<p><img src="Images/15.png" alt="Instance"></p>

* Go to the listeners and rules

<p><img src="Images/16.png" alt="Instance"></p>

* Click on manage rule and add the rules like Lapto and Mobile rule

<p><img src="Images/17.png" alt="Instance"></p>



<p><img src="Images/18.png" alt="Instance"></p>

* Add a laptop-rule first 

<p><img src="Images/19.png" alt="Instance"></p>

* Select a condition as a path 

<p><img src="Images/20.png" alt="Instance"></p>

* Give Path /Laptop/*

<p><img src="Images/21.png" alt="Instance"></p>

* Then add Laptop target group


<p><img src="Images/22.png" alt="Instance"></p>

* Set rule priority 1st to the laptop rule

<p><img src="Images/23.png" alt="Instance"></p>

* Now, add the rule Mobile

<p><img src="Images/24.png" alt="Instance"></p>

* Select Path like /Mobile/*

<p><img src="Images/25.png" alt="Instance"></p>

* Give 2nd Priority to Mobile

<p><img src="Images/26.png" alt="Instance"></p>

* Now, sucessfully we create a Load balancer named as ALB

<p><img src="Images/27.png" alt="Instance"></p>

* Copy the DNS name of load balancer and hit on browser 

<p><img src="Images/28.png" alt="Instance"></p>

* Final output

This is Output of server- Home Instance

<p><img src="Images/29.png" alt="Instance"></p>

This is Output of server- Laptop Instance

<p><img src="Images/30.png" alt="Instance"></p>

This is Output of server- Mobile Instance

<p><img src="Images/31.png" alt="Instance"></p>




## Summary

In this project, we set up an Application Load Balancer (ALB) on AWS to share traffic between three EC2 instances: Home, Laptop, and Mobile.
Each instance ran a script when it started to install Apache and show a custom webpage.
We created three target groups, and each instance was added to its own group.
Then, we created an Application Load Balancer with a listener on port 80 (HTTP), which sends traffic to these target groups.
Finally, we tested the ALB's DNS link in a web browser. The page showed different responses from Home, Laptop, and Mobile, proving that the load balancer was working correctly.