# Change Domain name

While the application is successfully deployed, the domain name will be some long string of letters (for example: isoVis-deploy-env.eba-r7r9zsja.eu-north-1.elasticbeanstalk.com). 

To change the name of the domain with a bought domain name (i.e. from GoDaddy), Route53 is used for DNS routing. 

## Set up Route 53 on AWS 
1. Search for <span class="search">Route 53</span> app on AWS web.
![Route53_1](../Images/route53.jpg)

2. Click on the <span class="button">Hosted zones</span> on the left-hand side tab of Route 53, and click on <span class="button">Created hosted zone</span>. 
![Route53_2](../Images/route53_2.jpg)

3. This will bring a pop-up window. Type in the  <span class="search">domain name of interest</span> in the <span class="button">Domain name</span>
![Route53_3](../Images/route53_2.jpg)
   > **Note:** isoforms.com is the bought name from GoDaddy. 
   Click <span class="button">Created hosted zone</span>.

4. This will take you back to the screen with the <span class="button">hosted zones</span>. Click on the domain created, which will bring you to this page. 
![Route53_4](../Images/route53_2.jpg)
   > **Important:** The <span class="code">Name server</span> listed here needs to be copied and added to the GoDaddy domain. 

5. To link the Elastic Beanstalk application with the nameserver, click on <span class="button">Create record</span>.

6. This will bring up another page. Select <span class="button">Simple routing</span>, click <span class="button">Next</span>.
![Route53_5](../Images/route53_5.jpg)

6. Click <span class="button">Define simple record</span>.
![Route53_5](../Images/route53_6.jpg)

7. This will bring up another pop-up page. 
	- Keep the subdomain blank.
	- Select <span class="code">A - Routes traffic to an IPv4 address and some AWS resources</span> under <span class="button">Record type</span>.
	- Select <span class="code">Alias to Elastic Beanstalk enviroment</span> under <span class="button">Value/Route traffic</span>.
	- Select the region that the environment was created (in this case, eu-north-1).
	- The Elastic Beanstalk environment created shoud be listed.
	- Click on <span class="button">Define simple record</span>.
![Route53_5](../Images/route53_6.jpg)

8. Depending on the application size, this can take up to a few hours for the DNS nameserver to update. 

## Change nameservers on GoDaddy 

The nameservers listed on AWS need to be copied on the GoDaddy domain. A step-to-step guide to do this can be found on this [video](https://www.godaddy.com/en-uk/how-to/introduction-to-domains-at-godaddy/how-to-change-domain-nameservers) or [document](https://www.godaddy.com/en-uk/help/edit-my-domain-nameservers-664).