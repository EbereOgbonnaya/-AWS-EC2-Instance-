# launching an EC2 instance from the command line using an IAM user with the necessary permissions.
## STEP 0: Prerequisites:
* AWS account
* AWS CLI installed and configured with IAM user credentials
* IAM user group with necessary permissions
![Alt text](<IMAGES/IAM User Acess.png>)
## STEP1:  AWS CLI Installation and Configuration:
- Install AWS CLI
- Run ```aws configure``` and input IAM user credentials (access key and secret key) along with default region settings.
![Alt text](<IMAGES/AWS Configuration and installation.png>)
## STEP2: Creating a key pair
- ```aws ec2 create-key-pair --key-name eby --query 'KeyMaterial' --output text > eby.pem```
- “eby” is the unique key pair name.
![Alt text](<IMAGES/Creating a Key Pair.png>)
## STEP3: Creating Security Group
- ```aws ec2 create-security-group --group-name EdoSecurityGroup --description "Edo security group"```
![Alt text](<IMAGES/Creating Security Group.png>)
- “Edo Security Group” is the unique security group name
## STEP4: Allow SSH Port
-``` aws ec2 authorize-security-group-ingress --group-name EdoSecurityGroup --protocol tcp --port 22 --cidr 0.0.0.0/0```
![Alt text](<IMAGES/Allowing SSH Port.png>)
## STEP5: Launching the instance
- ```aws ec2 run-instances --image-id ami-03a6eaae9938c858c --count 1 --instance-type t2.micro -- key-name eby --security-groups EdoSecurityGroup```
![Alt text](<IMAGES/Launch the Instance.png>)
![Alt text](<IMAGES/launch the instance2.png>)
## STEP6: Describe the instance
- ```aws ec2 describe-instances```
![Alt text](<IMAGES/Describe the instance.png>)
## STEP7: View instance on your AWS management console
Log in to your AWS account using your IAM user credentials.
- In the AWS Management Console, search for "EC2" to access the EC2 Dashboard.
- In the EC2 Dashboard, you'll find the "Instances" option, click on it to view your EC2 instances.
- You'll find a list of launched instances, click on the one you just created and view the details by clicking on the description tab.

![Alt text](<IMAGES/View the Instance.png>)

### CONGRATULATIONS! YOU HAVE SUCCESSFULLY LAUNCHED AN EC2 INSTANCE.




















