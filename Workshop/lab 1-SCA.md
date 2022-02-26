Dependency-Check is an open source Software Composition Analysis (SCA) tool that attempts to detect publicly disclosed vulnerabilities contained within a project’s dependencies. It does this by determining if there is a Common Platform Enumeration (CPE) identifier for a given dependency. If found, it will generate a report linking to the associated CVE entries.


Spend 5 minutes understanding the tool here -   https://owasp.org/www-project-dependency-check/


Dependency-check has a command line interface, a Maven plugin, an Ant task, and a Jenkins plugin. 

In this example we will be using Maven Plugin
check maven plugin here - https://search.maven.org/artifact/org.owasp/dependency-check-maven/6.5.3/maven-plugin 

Add dependency plugin by following the instructions here 
https://jeremylong.github.io/DependencyCheck/dependency-check-maven/index.html

after updating the pom.xml file
run mvn verify

you should see the report dependency-check-report.html in your target directory

you have 20 minutes to try this exercise. 


if you need help. please refer to file at Workshop/static/pom-dependency-check.xml. you can copy that file over for reference. you can copy this file over by using following command.

go to project root directory and run this command - 
cp Workshop/static/pom-dependency-check.xml pom.xml

mvn verify
 

