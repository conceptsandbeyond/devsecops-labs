# DevSecOps Lab 4 - DAST - Dynamic Application Security Testing

## Task - Implement DAST in your GitHub Actions workflow using OWAPS ZAP

<p>
 DAST is a process of testing an application or software product in an operating state

**Zed Attack Proxy (ZAP)** is a free, open-source dynamic testing tool being maintained under the umbrella of the Open Web Application Security Project (OWASP). ZAP is designed specifically for testing web applications and is both flexible and extensible.

At its core, ZAP is what is known as a “man-in-the-middle proxy.” It stands between the tester’s browser and the web application so that it can intercept and inspect messages sent between browser and web application, modify the contents if needed, and then forward those packets on to the destination. It can be used as a stand-alone application, and as a daemon process.

spend 5 mins to learn More about ZAP here - https://www.zaproxy.org/getting-started/ 

Confirm that your application is running. 

http://< yourIP>:< studentport>/

 **Replace the IP address with the one retrieved from following command.**

Run the following command from Cloud9 Terminal

`aws ec2 describe-instances --instance-id i-0edaf3625fea3c0bd  --query 'Reservations[*].Instances[*].PublicIpAddress'`

**Change the port number to match with your port number.**

    ![](static/lab4-5.png)


<br><br>
### Add DAST steps ###

Go through the instructions here for adding DAST action

https://github.com/marketplace/actions/owasp-zap-full-scan 

You will need target, which is a running web app.  
Use your application URL from above step.

> **Help?** Verify your DAST steps with pre-built actoins file. 

refer your ZAP action commands with the pre-built commands under job   
zap_scan: at <i> labs/lab4.2-ZAP.yml </i>

<br>
you can also copy the pre-built files from labs location by running the following command. 

```
cd /home/ec2-user/environment/devsecops-labs
# to make sure you are at project root directory
cp labs/lab4.2-ZAP.yml .github/workflows/build.yml
```

Run the following command to push the change. 

```
git add .
git commit -m "adding upload action"
git push 
```
>*username - enter your username* </p>
>*password - enter the Personal access token provided to you.*

<br>

Once the workflow completes, you can view the results of the scan in issues section of your GitHub Repo.

<!-- <screenshot> -->