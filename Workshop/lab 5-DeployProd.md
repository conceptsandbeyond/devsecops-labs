
# DevSecOps Lab 5 - DeploytoProd - Manual approval

## Task - Add Manual Approval step before deploying to Prod.


In this lab we will protect the deployment to prod by introducing a manual approval checkpoint. 

GitHub actions let you do that by way of adding Environment protection rule. 
<br>
spend 10 minutes researching how environement protection works - <br>
https://docs.github.com/en/actions/deployment/targeting-different-environments/using-environments-for-deployment

<br>
spend 5 minutes reviewing the steps to approve the workflow here - <br>
https://docs.github.com/en/actions/managing-workflow-runs/reviewing-deployments 

<br><br>

for our lab we are using `Environment = prod` with protenction rule as reviewers required. <br>
This part of setting is already created for you.

***Create new the job definition.***
Add an empty job that just requires manual review. 


refer to pre-built yml file from <i> labs/lab5-deployprod.yml </i> location by running the following command. 

```
cd /home/ec2-user/environment/devsecops-labs
# to make sure you are at project root directory
cp labs/lab5-deployprod.yml .github/workflows/build.yml

```


Push the code
```
git add .
git commit -m "adding upload action"
git push 
```
>*username - enter your username* </p>
>*password - enter the Personal access token provided to you.*

<br>

Go to GitHub Actions Console. your pipeline will wait for admins to review and approve.

After approval, the pipeline will continue and deploy the changes to prod.