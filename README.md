# CI/CD

## What is CI/CD?

CI/CD stands for continuous integration and continuous deployment. It is the automation of the manual human intervention needed to get new code committed into production. This includes:

- Building
- Testing
- Deploying
- Infrastructure provisioning 


The CI/CD pipeline takes code that has changes and automatically tests and pushes it for delivery and deployment. This minimises downtime and helps code to be released faster. As applications become larger CI/CD can decrease development complexity.

[DevOps Culture and CICD](https://medium.com/@ahshahkhan/devops-culture-and-cicd-3761cfc62450)

**Continuous integration** is the practice of integrating all your code changes into the main branch of a shared source code repository early and often, automatically testing each change when you commit or merge them, and automatically kicking off a build. With continuous integration, errors and security issues can be identified and fixed more easily, and much earlier in the development process.

![continuous integration](imgs/continous_integration.webp)

**Continuous delivery** is a software development practice that works in conjunction with CI to automate the infrastructure provisioning and application release process.

Once code has been tested and built as part of the CI process, CD takes over during the final stages to ensure it's packaged with everything it needs to deploy to any environment at any time. CD can cover everything from provisioning the infrastructure to deploying the application to the testing or production environment.

![continous delivery](imgs/continous_delivery.webp)

**Continuous depolyment** is the step after continuous delivery. This proccess takes evry change that passes the production pipline and releases to customers. There is no human interaction and only a failed test will prevent the change going to production. End to end automation, no interaction at all to get it to production.

![continuous deployment](imgs/continous_deployment.webp)

## Why Jenkins?

Jenkins is an open source continuous integration/continuous delivery and deployment (CI/CD) automation software DevOps tool written in the Java programming language. It is used to implement CI/CD workflows, called pipelines.

While Jenkins doesn't eliminate the need to create scripts for individual steps, it does give you a quicker and more robust way to integrate your entire chain of build, test, and deployment tools than you could easily build yourself.

Benefits:

1. Open source and free
2. Plug ins and intergration 
3. Its can be hosted on any OS
4. Community support
5. Integration with other CI/CD platforms
6. Centralised working
7. Easy to debug
8. Takes less time - continous integration
9. Supports different source code management (git, svn)
    
![Jenkins img](imgs/jenkins-img.png)

Jenkins is an open-source automation server widely used for continuous integration and continuous delivery (CI/CD) pipelines. It allows software development teams to automate the building, testing, and deployment of their applications. Jenkins provides a web-based interface and a powerful set of plugins that enable users to create and manage automated workflows.

In a Jenkins environment, there are two key components: the master node and agent nodes (also known as slave nodes or build nodes).

1. Jenkins Master Node:

It is where you have logged in and is the controller.
The master node is the central server that manages the Jenkins system. It coordinates the overall build process, schedules and distributes builds to agent nodes, and monitors their execution. The master node hosts the web interface, where users configure Jenkins jobs, view build results, and manage the system's configuration. It also stores the configurations, plugins, and other essential data related to Jenkins.

The master node's responsibilities include:
- Scheduling and coordinating build jobs.
- Managing the distribution of build tasks to agent nodes.
- Storing and managing configurations, plugins, and user management.
- Providing the web-based interface for managing Jenkins.

1. Jenkins Agent Node:
Agent nodes are the worker machines responsible for executing build tasks assigned to them by the master node. They provide the computing resources required for building, testing, and deploying software. Agent nodes can be physical machines or virtual machines, and they can be located on the same network as the master node or in remote locations.

The agent nodes are configured to connect to the Jenkins master and wait for build tasks to be assigned to them. When a build is scheduled, the master node determines the appropriate agent based on criteria such as availability, labels, or specific requirements defined in the build configuration. The build task is then sent to the agent node for execution. If the job fails it will only effect that agent, not the whole system.

Agent nodes can have different configurations, such as specific software or operating systems, to accommodate different build requirements. They can be dedicated to specific types of builds or shared among multiple projects, depending on the organization's needs.

To summarize, the Jenkins master node is the central server that manages and coordinates the build process, while the agent nodes are the worker machines that execute the build tasks assigned by the master. This distributed architecture allows for scalability, parallelization, and flexibility in managing builds across various environments and configurations.

## Other tools that can be used for CICD:

- Travis Ci
- CircleCi
- TeamCity
- GitLab
- Buddy
- Bamboo
- Azure DevOps Server

![cicd tools](imgs/cicd_tools_examples.webp)

## Why build a pipeline?

With a CI/CD pipeline, development teams can make changes to code that are then automatically tested and pushed out for delivery and deployment. By automating the process, the objective is to minimize human error and maintain a consistent process for how software is released. If at any point a stage fails the next stages will also fail.

One of the most exclusive benefits of a CI/CD pipeline is that it leads to the quick and easy rollback of code changes if there are any issues in the production environment after a release. If any new code change breaks a feature or general application, you can revert to its previous stable version right away.

## Business value?

CI/CD pipeline reduces human intervention across the DevOps lifecycle by automating the handoffs, version controlling, source code management, deployment processes, and testing, among others. This significantly saves the time and money required to develop and deliver high-quality software.

CI/CD has enabled many organizations to release on a more frequent basis without compromising on quality. With CI/CD, code changes are shepherded through an automated pipeline that handles the repetitive build, test and deployment tasks and alerts you about any issues.

![benefits of cicd](imgs/benefits-cicd.png)


## Adding a key to github

To add a key go to the app repo, settings, deploy key, add key, paste the key into it and give it a name.

## Jenkins

### Creating a simple job on Jenkins

1. Go to the [Jenkins site](http://18.133.222.223:8080/) and log in
2. Click on New Item

![home page](imgs/jenkins_home_page.png)

3. Give the job a name and select Freestyle project

![create job](imgs/create-job.png)

4. You can give the job a description and tick discard old builds and set max # of builds to keep to 3. This will get rid of the build after 3 days.

![setting up job](imgs/setting-up-job.png)

5. Scroll down to the Build section and choose Excecute shell

![Build](imgs/build-jenkins.png)

6. In the shell type in your commands you woud like to execute, in this case we did uname -a which will give the type of operating system.
7. If there is another job you wish to do after this one click on post-build action and select build other projects

![shell and build other projects](imgs/shell_and_build_other.png)

8. Click on Build Now and then go to the build history and you should be able to see the job there. 
9. Click on console output to see the result 

![Build now](imgs/build-now.png)

10. In the console output you can see what the result is and if it was successful
    
![console output](imgs/console_output.png)

11. The blue circle on the main dashboard shows it is successful. It will be cloudy if there was some issues and it will be red it it failed.

![success](imgs/success.png)

### Deleting job

To delete a job click on the drop down from the name of the job and select delete.

![delete](imgs/delete.png)


## Adding webhooks and automation in Jenkins

1. Add public key to github. To add a key go to the app repo, settings, deploy key, add key, paste the key into it and give it a name. **Blocker** Make sure to add write access!
2. Click on New Item
3. Give the job a name and select Freestyle project
4. Add description and select discard old builds. Give max # of builds to keep 3.
5. Select Github Project 
6. Paste in the HTTPS url from Github

![Alt text](imgs/stage2-img/step1.png)

7. In Source Code Management in repository URL paste in the SSH url
8. Add the private key which matches the public key on github
9. Change Branch specifer to main

![Alt text](imgs/stage2-img/step2.png)

10. Build Environment - select Provide Node & npm bin/ folder to PATH
11. NodeJS installation - Sparta-Node-JS (this allows node commands)

![Alt text](imgs/stage2-img/step3.png)

12. Office 365 Connector - select Restrict where this project can be run
13. Label Expression - sparta-ubuntu-node

![Alt text](imgs/stage2-img/step4.png)

14. Scroll down to the Build section and choose Excecute shell
15. In the shell type in your commands you woud like to execute, in this case we did cd app, npm install and npm test.

![Alt text](imgs/stage2-img/step5.png)

1.  Set up a webhook in Github - go to the repo, settings, webhooks, add webhook [Example](https://www.blazemeter.com/blog/how-to-integrate-your-github-repository-to-your-jenkins-project)
2.  In payload URL paste the Jenkins url (ip) with /github-webhook/ on the end
3.  Content type - application/json
4.  Let me select individual events

![Alt text](imgs/stage2-img/step7.png)

20. Select Pull Requests and Pushes

![Alt text](imgs/stage2-img/step8.png)

21. Select Active and Update webhook

![Alt text](imgs/stage2-img/step9.png)

22. Back on Jenkins go to Build Triggers and select Github hook trigger for GITScm polling

![Alt text](imgs/stage2-img/step10.png)

Now when you push a change on the app git repo, jenkins will automatically create a job and run and then you can look at the console output. For us the script cd in to the app, did an npm install and then ran some tests. Here is the successful output:

![Alt text](imgs/stage2-img/step6.png)

## AWS production

On AWS we have to allow the jenkins IP address and the port it is on (port 8080). 

The workspace of Jenkins contains a clone of the repo.
to create branch `git checkout dev`

Job 1:

## Job 2: called elena-ci-merge
- Create a dev branch on localhost 
- Github makes a change to dev branch and pushes the code to github
- The webhook triggers
- If the test passed the code should be merged from dev to main branch

![Alt text](imgs/job2/source-code-management-git.png)

![Alt text](imgs/job2/post-build-git.png)

## Job 3:
- Clones the main branch and push to production AWS ec2
- ssh into ec2
- copy the code using scp or rsync 
- navigate to app folder
- npm install 
- npm start
- get the public ip with 3000 share with team 

Launch an ec2 instance with required SG rules
ubuntu 18.04
ensure to have node env
have app folder copied from jenkins to ec2
provide file.pem to jenkins

Steps:

1. Give discription, discard old builds and max # builds 3
2. Github project - HTTPS link

![Alt text](imgs/job3/step1.png)

3. Office 365 connector - Restrict where this project can be run
4. Label expression - sparta-ubuntu-node

![Alt text](imgs/job3/step2.png)

5. Source code management - Git
6. Repo url - SSH
7. Credentials - elena-jenkins-key (key on repo)
8. Branch - main

![Alt text](imgs/job3/step3.png)

9. Build environment - SSH agent
10. credentials - tech241.pem

![Alt text](imgs/job3/step4.png)

11. Build execute shell put in the code below:

```
rsync -avz -e "ssh -o StrictHostKeyChecking=no" app ubuntu@ec2-52-215-189-222.eu-west-1.compute.amazonaws.com:/home/ubuntu/app
 

# SSH
ssh -o StrictHostKeyChecking=no ubuntu@ec2-52-215-189-222.eu-west-1.compute.amazonaws.com <<EOF
    # For app running without the db
    unset DB_HOST

 

    cd app/app
    npm install
    pm2 kill
    pm2 start app.js
EOF
```

![Alt text](imgs/job3/step5.png)