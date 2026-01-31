# DevOps-Projects
Project 1 Architecture:
<img width="1470" height="782" alt="Screenshot 2026-01-31 at 10 38 44 AM" src="https://github.com/user-attachments/assets/4b8cda40-721f-444b-905c-da1bf39fe087" />
**Steps:**
- Create a sample Java project or by forking an existing project (I'll be forking an existing project from https://github.com/bhasker-manikyala/DevOpsClassCodes and my Target repo will be https://github.com/brsanjeev88/DevOpsClassCodes)
-  Install Jenkins on AWS EC2 server
   - Login to AWS console
   - Search for EC2 and select EC2
   - Click on launch Instance and create a free tier instance with default options. Also create a key pair and download it
   - Once it is in running state, copy the public ip address
   - From your laptop open your terminal (Moba Xterm or iTerm)  and type the below commands
  		- ssh ubuntu@copied IP address - this command will give you Permission Denied because keypair is not used
		- ssh -i /Enter/the/Path/to/keyPair.pem/file ubuntu@copied IP address 
  		- Again you will get Permission Denied because permissions are too open
  	    - chmod 600 /Enter/the/Path/to/keyPair.pem/file
  	    - ssh -i /Enter/the/Path/to/keyPair.pem/file ubuntu@copied IP address
   - Install AWS CLI from AWS CLI Documentation
     	- curl "https://awscli.amazonaws.com/AWSCLIV2.pkg" -o "AWSCLIV2.pkg"
        - sudo installer -pkg AWSCLIV2.pkg -target / 
        - Or
        - sudo snap install aws-cli --classic
        - Or
        - sudo apt install awscli
   - Go to AWS Console and navigate to Security Credentials under profile
   - Navigate to Access Keys and create a new one and save it
   - Go to terminal and type the below commands
	     - aws configure
		 - enter access key and other details
   - To test try aws s3 ls
   
