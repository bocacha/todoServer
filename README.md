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

