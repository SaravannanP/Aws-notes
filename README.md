# Aws-notes
Notes I've written down for the AWS developer exam

## What is AWS
AWS(Amazon Web Services) is a cloud provider 
- provide servers and services that can be used on demand 
  and scale easily.

30 AWS services covered 

# Section 3: Getting Started with AWS  

## 8. AWS Cloud Overview - Regions
### AWS regions
 - AWS has regions all around the world 
 - naming convention is us-east-1,eu-west-3
 - A region is a cluster of data centers 
 - Most AWS services are region-scoped
 
### How to choose AWS region(exam qn)
 Depends on the following factors :
 - COMPLIANCE with data governance and legal requirements:\
   Data never leaves a region without explicit permission\
   Example: France data should stay in France so launch in the France region 
 - PROXIMITY to customers: Reduced latency  
   Example: if the customer base is in America makes sense to deploy in America for reduced latency/lag 
 - AVAILABLE SERVICES within a region: 
   new services and new features aren't available in every region\
   Example: if leveraging a service with an app ensure the deployed region has that service available.
 - PRICING:\
   Pricing varies from region to region and is transparent on the service pricing page\
   A factor for deployment into a specific region 
   
### AWS Availability zones (AZ)
 Each region has multiple availability zones Min 3  Max 6 (Usually 3)\ 
 Example: 
			AWS region
			Sydney: ap-southeast-2 
			- ap-southeast-2a
			   - 2 - 4 data centers 
			- ap-southeast-2b
			   - 2 - 4 data centers 
			- ap-southeast-2c
			   - 2 - 4 data centers 
	
### AWS data centers
- Each AZ is one or more discrete data centers with redundant power,networking and connectivity 
		
- They are separate from each other so that they are isolated from disasters 
	
- They are connected with high bandwidth ultra-low latency networking 

### AWS Edge Locations/ Points of Presence
- Amazon has 400+ Points of presence in 90+ cities acorss 40+ countries 

##  AWS Services
# AWS global services:
  - identity and Access Management(IAM)
  - Route 53 (DNS service)
  - CloudFront (Content Delivery Network)
  - WAF(Web application firewall)

# AWS region-scoped services:
  - Amazon EC2 (Infra as a service)
  - Elastic Beanstalk (Platform as a service)
  - Lambda (function as a service)
  - Rekognition (software as a service) 
  
  
  
 # Section 4: IAM  & AWS CLI 
 
 ## IAM introduction: Users,Groups,Policies
 - Identity and access management, Global service 
 - IAM service creates users and assign them to groups 
 - root account is an example, created by default shouldn't be used or shared
 - Users are people within the organization and can be grouped 
 - Groups can only contain users, not other groups
 - users do not have to belong to a group and users can belong to multiple groups 
 
 Example : ![Screenshot 2024-01-05 063027](https://github.com/SaravannanP/Aws-notes/assets/67651440/a505b339-6290-42e9-a930-45c2ed5ebdb6)

 
 ## IAM Users & Groups 
 Why create users and why create groups?
 - Allow users to use AWS accounts for that permissions are required to assign 
   users or groups 
 
 IAM: Permissions 
 - Users or Groups can be assigned JSON documents called policies
   Example of a policy:
   ![Screenshot 2024-01-05 063243](https://github.com/SaravannanP/Aws-notes/assets/67651440/464b37fd-53a1-473b-b193-3dc38b64d8c5)

Short description on above policy:
Allow user to use ec2 instance and elastic load baalncing and cloudwatch.
 - these policies define the permission of the users 
 - Apply the least privilege principle: don't give more permissions than a user needs 
Example: if the user needs access to three services just create a permission for that user 

IAM as an entire service is a global service therefore is tagged under the global region 

 1. Naviagate to IAM in AWS console 
 2. Click on users on the side panel
 3. Create user > [Check] I want to create an IAM user
 4. Option to add user to existing group  or create group
 5. Create group > [Check] administrator access policy
   - Enter group name > check policy named amin acces(Provide full access to AWS services)
   - Add created user to created group 
Is not good practice to use a root account therefore create users such as admin users to access accounts more safely 
The user inherits directly the permission to whatever group they are attached to
 
## IAM Policies 
IAM policies inheritance Example:

![Screenshot 2024-01-05 084034](https://github.com/SaravannanP/Aws-notes/assets/67651440/b4ba6a78-abb2-44d7-81f6-106f0374a99d)
 
First group of developers with a policy attached at the group level 
THis policy is applied to every memeber of the developer group 

Second group of operations with a different policy attached

if Fred is a user and does not belong to a group.Possible that inline policy attached to fred 

if Charles and david belong to the audti team they both inherit the policies from audit team as well as 
the policies from the other teams 
 
