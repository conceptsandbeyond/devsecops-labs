
## Run Docker Image##

**These commands need to be run in your cloud9 environment terminal**

Pull Docker Image  
Run `docker pull bkimminich/juice-shop`

Run Juice Shop application  
Run `docker run --rm -p 3000:3000 bkimminich/juice-shop`

Open new Terminal Tab  
Find IP of your host by running the following command  
`curl http://169.254.169.254/latest/meta-data/public-ipv4 `  

Browse to http://\<replace it with public ip\>:3000 (on macOS and Windows browse to http://192.168.99.100:3000 if you are using docker-machine instead of the native docker installation)  

Click on Account, Login.  

Click on  "Not yet a customer?"  

You will be redirected to User Registration page

Create an account using <userid>@localhost.com

Move to next step.  
