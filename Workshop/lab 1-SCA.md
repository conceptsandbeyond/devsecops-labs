# DevSecOps Lab 1 - SCA - Dependency Scan

## Task - Add Security Composion analysis for dependency vulnerability testing

Software Composition Analysis (SCA) is an application security methodology for managing open source components. Using SCA, development teams can quickly track and analyze any open-source component brought into a project. SCA tools can discover all related components, their supporting libraries, and their direct and indirect dependencies. SCA tools can also detect software licenses, deprecated dependencies, as well as vulnerabilities and potential exploits. The scanning process generates a bill of materials (BOM), providing a complete inventory of a project’s software assets.
<p>


Dependency-Check is an open source Software Composition Analysis (SCA) tool that attempts to detect publicly disclosed vulnerabilities contained within a project’s dependencies. It does this by determining if there is a Common Platform Enumeration (CPE) identifier for a given dependency. If found, it will generate a report linking to the associated CVE entries.


<b>Learn More about the tool here </b>-   https://owasp.org/www-project-dependency-check/


Dependency-check has a command line interface, a Maven plugin, an Ant task, and a Jenkins plugin. 

In this example we will be using Maven Plugin

<b>Check how to use maven plugin here </b> - https://search.maven.org/artifact/org.owasp/dependency-check-maven/6.5.3/maven-plugin 


Add dependency plugin by following the instructions here 
https://jeremylong.github.io/DependencyCheck/dependency-check-maven/index.html

Once integrated with pom.xml, you can run following command to generate the report.
mvn verify

The dependency report " dependency-check-report.html" will be stored in your target directory


if you need help. please refer to file at lab/static/pom-dependency-check.xml. you can copy that file over for reference. you can copy this file over by using following command.

go to project root directory and run this command - 

```
cd /home/ec2-user/environment/devsecops-labs
# to make sure you are at project root directory
cp labs/pom-dependency-check.xml pom.xml
```
