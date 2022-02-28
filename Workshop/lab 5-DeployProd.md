
In this lab we will protect the deployment to prod by introducing a manual approval checkpoint. 

GitHub actions let you do that by way of adding Environment protection rule. 

spend 10 minutes researching how environement protection works -
https://docs.github.com/en/actions/deployment/targeting-different-environments/using-environments-for-deployment


spend 5 minutes reviewing the steps to approve the workflow here -
https://docs.github.com/en/actions/managing-workflow-runs/reviewing-deployments 


for our lab we are using Environment = prod with protenction rule as reviewers required. 
this part of setting is already created for you.

create the job definition.
Add an empty job that just requires manual review. 




when ready, please copy the pre-built files from labs location by running the following command. 

```
cd /home/ec2-user/environment/devsecops-labs
# to make sure you are at project root directory
cp labs/lab5-deployprod.yml .github/workflows/build.yml
# Open your build.yml file and review contents of your files
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