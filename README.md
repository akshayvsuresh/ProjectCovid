# ProjectCovid
Objective
To automate a web application server which shows the latest state-wise Covid-19 cases in India using Jenkins, Docker and GitHub.

Environments needed
1.Production Team

2.Testing team

3.Quality Assurance

Pre-requisites
Docker image : httpd
Jenkins with GitHub plugin
GitHub account and Git locally installed on your machine

Steps(Git, GitHub)

1.Create a new local git repository with your code in git with two branches called master and updater
2.Create a post-commit git hook which will push the code as soon as the developer commits the code
3.Now push the data to your GitHub remote repository

Steps(Jenkins Jobs)

1.Create a job ProductionEnvUpdate which will check for latest commits from GitHub in the master branch and if new commits are made, will pull the code from GitHub to a docker volume named ProductionVolume which will be linked to the docker container that will be launched as soon as this job is built. The port 80 of the docker container is forwarded to the port 8085 of the base RHEL8 machine

2.Create a job TestingEnvUpdate which will check for latest commits from GitHub in the updater branch and if new commits are made, will pull the code from GitHub to a docker volume named TestingVolume which will be linked to the docker container that will be launched as soon as this job is built. The port 80 of the docker container is forwarded to the port 8086 of the base RHEL8 machine

3.Create a job QAT for the Quality Assurance Team which will merge the branches master and updater and will trigger build in ProductionEnUpdate
