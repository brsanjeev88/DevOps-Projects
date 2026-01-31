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
  		ssh ubuntu@copied IP address - this command will give you Permission Denied because keypair is not used
  	    ssh -i /Enter/the/Path/to/keyPair.pem/file ubuntu@copied IP address 
  		Again you will get Permission Denied because permissions are too open
  	    chmod 600 /Enter/the/Path/to/keyPair.pem/file
  	    ssh -i /Enter/the/Path/to/keyPair.pem/file ubuntu@copied IP address
   - Install AWS CLI from AWS CLI Documentation
     	curl "https://awscli.amazonaws.com/AWSCLIV2.pkg" -o "AWSCLIV2.pkg"
        sudo installer -pkg AWSCLIV2.pkg -target / 
        Or
        sudo snap install aws-cli --classic
        Or
        sudo apt install awscli
   - Go to AWS Console and navigate to Security Credentials under profile
   - Navigate to Access Keys and create a new one and save it
   - Go to terminal and type the below commands
	     aws configure
		 enter access key and other details
   - To test try aws s3 ls
- At this point you should be seeing in your terminal as **ubuntu@ip-Private-IP-Address:**
- Install Java for running Java applications on EC2 instance
    - sudo apt update
    - sudo apt install fontconfig openjdk-21-jre
    - java -version
- Install Long Term Support Release version of Jenkins
    - sudo wget -O /etc/apt/keyrings/jenkins-keyring.asc \
    - https://pkg.jenkins.io/debian-stable/jenkins.io-2026.key
    - echo "deb [signed-by=/etc/apt/keyrings/jenkins-keyring.asc]" \
    - https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
    - /etc/apt/sources.list.d/jenkins.list > /dev/null
    - sudo apt update
    - sudo apt install jenkins
- Check the status of jenkins - it should be in active state
    - sudo systemctl status jenkins
- Open any browser and enter the URL as http://Public-IP-Address:8080/ (Default port for Jenkins is 8080)
    - You should see a textbox with a command displayed
- Unlock Jenkins
    - Copy the path mentioned in the above step and navigate to terminal and paste the command
        - Command: sudo cat /var/lib/jenkins/secrets/initialAdminPassword
        - copy the password
    - Paste the password in the textbox mentioned in the URL - http://Public-IP-Address:8080/
- Customize Jenkins - select the option **Install Suggested plugins**
- Create First Admin User account
    - Enter all the details and click on Save and Continue
    - 
   
