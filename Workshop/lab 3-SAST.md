# DevSecOps lab 3 - SAST - Static Application Security Testing #

## Task - Add static scanning to your GitHub Actions Workflow using Sonar Cube.

Spend 5 mins reviewing Sonarcloud here - https://sonarcloud.io/features 

Add SAST in your pipeline.

Step 1 - (Skip - Its already done for this project) <br>
    Create a GitHub Secret <br>
    In your GitHub repository, go to Settings > Secrets and create a new secret with the following details:<br>
    
    In the Name field, enter SONAR_TOKEN 
    In the Value field, enter ***********


Step 2 - (Verify if its done) - 5 mins

Update your pom.xml file with the following properties:

    
    <properties>
      <sonar.organization>conceptsandbeyond-git</sonar.organization>
      <sonar.host.url>https://sonarcloud.io</sonar.host.url>
    </properties>
    Create or update your .github/workflows/bui
    
    

Step 3 - (your task) - 10 mins <br>
Create or update your .github/workflows/build.yml <br>
Here is a base configuration to run a SonarCloud analysis on your master branch and Pull Requests. If you already have some GitHub Actions, you might want to just add some of these new steps to an existing one. <br>

```
       
  analyze:
    runs-on: ubuntu-latest
    needs: [build]
    steps:
      - uses: actions/checkout@v2
      
      - name: Cache SonarCloud packages
        uses: actions/cache@v1
        with:
        
          path: ~/.sonar/cache
          key: ${{ runner.os }}-sonar
          restore-keys: ${{ runner.os }}-sonar

      - name: Cache Maven packages
        uses: actions/cache@v1
        with:
          path: ~/.m2
          key: ${{ runner.os }}-m2-${{ hashFiles('**/pom.xml') }}
          restore-keys: ${{ runner.os }}-m2

      - name: Build and analyze
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}  # Needed to get PR information, if any
          SONAR_TOKEN: ${{ secrets.SONAR_TOKEN }}
        run: mvn -B verify org.sonarsource.scanner.maven:sonar-maven-plugin:sonar -Dsonar.projectKey=conceptsandbeyond_devsecops-labs
      
   
``` 

<br>
Optionally, you can use the yml file that is already created for you. <br>
Run the following commands to copy the files.

```
cd /home/ec2-user/environment/devsecops-labs
# to make sure you are at project root directory
cp labs/lab3-SAST.yml .github/workflows/build.yml

```
