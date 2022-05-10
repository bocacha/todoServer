# GitHub Pipeline
## Continuous Integration Final Assignment

## Work around:

1) It was mandatory to pick a repository, clone it and testing it to ensure the project run smoothly and got its testing working properly.
   In this case, a Gradle Backend with H2 Database was picked up, making use of IntelliJ as project IDE with JDK 11.

2) Then this repository was created, where it was neccesary to set up an GitHub Action to store the Pipeline Workflow, following the GitHub   
   steps, choosing Java with Gradle as template.

3) Next step was to start editing the gradle.yaml file, setting the Workflow with their corresponding jobs & steps, allowing to seeing the 


![GItHub action1](https://user-images.githubusercontent.com/82456534/167513190-cc57a21d-e0fb-4605-92a2-0e60d03c1a53.png)

4) Next step was to set up JFROG, where the created Artifacts would be uploaded througt the implementation of a new job in the gradle.yaml. 
   To achieve this task, three Repositories were created in Jfrog: 
   
   *  Local 
   *  Remote
   *  Virtual ( this one contains the other two )
   
   Following the JFrog assist helper "Set me Up" a snippet is generated containing the code lines to be added inside build.gradle, besides
   the gradle.properties file that must me copied into the project root containing the JFrog credentials:
   
   
 ![set me up](https://user-images.githubusercontent.com/82456534/167514710-ec38c832-29dd-48b3-8452-a85ec7dddca5.png)
 
The Artifactory code portion in build.gradle:

![artifactory](https://user-images.githubusercontent.com/82456534/167519082-4ef779f1-55a0-4841-a2f3-0d71ec0def09.png)

The gradle.properties file:
![gradloeprop](https://user-images.githubusercontent.com/82456534/167518366-33523f4f-f8e6-4e6f-8ea5-ad7c4339b76a.png)

 
 5) Once the build.gradle and and gradle.properties has been updated, the Artifactories will be uploaded on the next GitHub push:

![JFrog upload](https://user-images.githubusercontent.com/82456534/167515294-ee878e74-48aa-4419-8396-2c86459a0658.png)

6) Once the Artifactory has been set up, Sonar Cloud will be added, loggin in their webpage and granting GitHub permissions.
   Then enter in Administration menu, analyze with GitHub actions and generating a token to add in GitHub secrets.
   Update build.gradle, and finally set Quality Gate & rules:
   
![sonar](https://user-images.githubusercontent.com/82456534/167524302-6ebaa52c-1e63-4596-88fa-b90d98098a0a.png)
   
![sonarEnYaml](https://user-images.githubusercontent.com/82456534/167524362-c46f84b1-d988-4d9c-be6a-4dc2a722d885.png)


The Quality gate running: (-Dsonar.qualitygate.wait=true & continue-on-error=true must be added at gradle.yaml )


 ![qgfail](https://user-images.githubusercontent.com/82456534/167524698-8f968b23-142b-4365-839b-6c2543285d94.png)


![sonar3](https://user-images.githubusercontent.com/82456534/167524332-b3f2799b-dd03-4443-b845-86512a4baf0e.png)

The Quality Gate then was updated modifying the rules avoiding the 5 code smell detected by Sonar.

7) Git Leaks: update  gradle.yaml to call the action from zricethezav/gitleaks GitHub repository, wich will scan the pipeline
   searching for hardcoded tokens: (zricethezav/gitleaks-action@master )

![gitleaks](https://user-images.githubusercontent.com/82456534/167525053-dd1b3f61-8643-4362-a1dd-2f909ff0b091.png)

8) Adding Snyk security:



![snyk](https://user-images.githubusercontent.com/82456534/167525304-be52edbe-6580-4837-aef4-255991928b01.png)

![snyk2](https://user-images.githubusercontent.com/82456534/167525317-638922ac-06b9-442b-8015-98fa887486ba.png)



