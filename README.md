# Aws-notes
Notes I've written down for the AWS developer exam

## What is AWS
AWS(Amazon Web Services) is a cloud provider 
- provide servers and services that can be used on demand 
  and scale easily.

30 AWS services will be the course 


2002 
internally launched ...

# Section 3: Getting Started with AWS 

## AWS global infra
### AWS regions
 - AWS has regions all around the world 
 - naming convention is us-east-1,eu-west-3
 - A region is a cluster of data centers 
 - Most AWS services are region-scoped
 
### How to choose AWS region(exam qn)
 Depends on factors 
 - COMPLIANCE with data governance and legal requirements:
   Data never leaves a region without explicit permission 
   Eg: France data should stay in France so launch in the France region 
 - PROXIMITY to customers: reduced latency 
   Eg: if the customer base is in America makes sense to deploy in America for reduced latency/lag 
 - AVAILABLE SERVICES within a region: new services 
   and new features aren't available in every region
   Eg: if leveraging a service with an app ensure the deployed region has that service available.
 - PRICING: Pricing varies from region to region and is transparent on the service pricing page
   A factor for deployment into a specific region 
   
### AWS Availability zones
 Each region has multiple availability zones Min 3  Max 6 Usually 3 
  for example: 
			AWS region
			Sydney: ap-southeast-2 
			- ap-southeast-2a
			   - 2 - 4 data centers 
			- ap-southeast-2b
			   - 2 - 4 data centers 
			- ap-southeast-2c
			   - 2 - 4 data centers 
	
### AWS data centers
- Each AZ is one or more discrete data centers with redundant power,
	  networking and connectivity 
		
- They are separate from each other so that they are isolated from disasters 
	
- They are connected with high bandwidth ultra-low latency networking 



- AWS Edge Locations/ Points of Presence
-------------------------------------------- 
- Amazon has 400+ Points of presence in 90+ cities acorss 40+ countries 




## Tour of AWS console
- AWS has global service:
  - identity and Access Management(IAM)
  - Route 53 (DNS service)
  - CloudFront (Content Delivery Network)
  - WAF(Web application firewall)

- Most AWS services are Region-scoped:
  Amazon EC2 (Infra as a service)
  Elastic Beanstalk(Platform as a service)
  Lambda (function as a service)
  Rekognition(software as a service) 
  
  
  
 # Section 4: IAM  & AWS CLI 
 
 ## IAM section
 - identity and access management, Global service 
 - Within IAM create users and assign them to groups
 - root account is an example, created by default shouldn't be used or shared
 - Users are people within the organization and can be grouped 
 - Groups can only contain users, not other groups !!!!!!
 - users do not have to belong to a group and users can belong to multiple groups 
 
 Example : 
 Group: Developers
 Alice, Bob, Charles 
 
 Group: Audit Team 
 Charles, David 
 
 Group: Operations
 David, Edward 

 Fred  
 
 
 Why create users and why create groups?
 - Allow users to use AWS accounts for that permissions are required to assign 
   users or groups 
 
 IAM: Permissions 
 - Users or Groups can be assigned JSON documents called policies 
 - these policies define the permission of the users 
 - in AWS apply the least privilege principle: don't give more permissions than a user
   needs 
  Eg: if the user needs access to  three services just create a permission
			for that user 


- creating a user in IAM will be available everywhere and therefore tagged under global  
 1. Naviagate to IAM in AWS console 
 2. click on users on the side panel
 Is not good practice to use a root account 
 So create users such as admin users to access accounts more safely 
 create user >[check] I want to create an IAM user 
 create group > [Check] administrator access policy 
 
 
