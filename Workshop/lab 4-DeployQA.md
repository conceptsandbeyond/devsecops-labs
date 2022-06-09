# DevSecOps Lab 4 - Deploy to QA for Dynamic Application Security Testing

## Task - Deploy your application to QA

<p>

Dynamic testing needs a running application. <br>
For this lab the infrastructure is already created for you. <br>
Just go through the following instructions to deploy the application to QA environment


```
cd /home/ec2-user/environment/devsecops-labs
# to make sure you are at project root directory
cp labs/lab4.1-DeployQA.yml .github/workflows/build.yml

```

### **Change the port number.** 
* Open *application.properties file(at devsecops-labs/src/main/resources)* files as shown below.

    ![](static/lab4-1.png)

Change the last digit of ```server.port:9090``` to match with your team number. </P>
i.e. 
  *student1* -  `server.port:9091`</p>
  *student2* - `server.port:9092` </p>
  *student3* -  `server.port:9093`</p>
  *student4* - `server.port:9094` and so on

<br>

* Open Stop.sh at the folder root (*devsecops-labs*)

    ![](static/lab4-2.png)

Change the port number to the same as in the previous file and to match with your team number</p>
`sudo kill -9 $(sudo lsof -t -i:9090)`</br>
change to </p>
i.e. 
  *student1* -  `sudo kill -9 $(sudo lsof -t -i:9091)` </p>
  *student2* - `sudo kill -9 $(sudo lsof -t -i:9092)` </p>
  *student3* -  `sudo kill -9 $(sudo lsof -t -i:9091)` </p>
  *student4* - `sudo kill -9 $(sudo lsof -t -i:9092)` and so on

### Change the artifacts location ###

**Open your build.yml file and rename the S3Folder section to match with your number </p> Search for the line** `S3Folder: githubactions0` **and update it with your team number.**
S3Folder: githubactions`<your team number>`</p>

>e.g.</p>
>student1 will have  `S3Folder: githubactions1`</p>
>student2 will have  `S3Folder: githubactions2`</p>
>student3 will have  `S3Folder: githubactions3`</p>
>student4 will have  `S3Folder: githubactions4`</p>

 Push the code
```
git add .
git commit -m "adding upload action"
git push 
```
>*username - enter your username* </p>
>*password - enter the Personal access token provided to you.*

<br>

View your running application at this link.

http://< yourIP>:< yourPort>/

 **Replace the IP address with the one retrieved from following command.**

Run the following command from Cloud9 Terminal

`aws ec2 describe-instances --instance-id i-0edaf3625fea3c0bd  --query 'Reservations[*].Instances[*].PublicIpAddress'`

**Change the port number to match with your port number.**

    ![](static/lab4-5.png)

