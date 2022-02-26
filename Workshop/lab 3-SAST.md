Add static scanning using Sonar Cube.

Spend 5 mins reviewing Sonarcloud here - https://sonarcloud.io/features 

Add SAST in your pipeline.

step 1 - (Already done for this project)
    Create a GitHub Secret
    In your GitHub repository, go to Settings > Secrets and create a new secret with the following details:
    
    In the Name field, enter SONAR_TOKEN 
    In the Value field, enter ***********


Step 2 - (Verify that this is done)

Update your pom.xml file with the following properties:
    '''
    <properties>
      <sonar.organization>conceptsandbeyond-git</sonar.organization>
      <sonar.host.url>https://sonarcloud.io</sonar.host.url>
    </properties>
    Create or update your .github/workflows/bui
    '''

Step 3 - (your task)
Create or update your .github/workflows/build.yml 
Here is a base configuration to run a SonarCloud analysis on your master branch and Pull Requests. If you already have some GitHub Actions, you might want to just add some of these new steps to an existing one.

name: Build
on:
  push:
    branches:
      - master
  pull_request:
    types: [opened, synchronize, reopened]
jobs:
  build:
    name: Build
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
        with:
          fetch-depth: 0  # Shallow clones should be disabled for a better relevancy of analysis
      - name: Set up JDK 11
        uses: actions/setup-java@v1
        with:
          java-version: 11
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
        
        


Spend 20 mins on above exercise, if you run into issues, please copy the build.yml file from the labs section by using following commands.

