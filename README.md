# Coworking Space Service Extension
The Coworking Space Service is a set of APIs that enables users to request one-time tokens and administrators to authorize access to a coworking space. This service follows a microservice pattern and the APIs are split into distinct services that can be deployed and managed independently of one another.

For this project, you are a DevOps engineer who will be collaborating with a team that is building an API for business analysts. The API provides business analysts basic analytics data on user activity in the service. The application they provide you functions as expected locally and you are expected to help build a pipeline to deploy it in Kubernetes.

## Setup
1- Clone the repo
2- Run the database Dockerfile found inside db and pass args for the db connection
3- Run the app Dockerfile  with run time variable to configure DB_USERNAME and DB_PASSWORD (use same as step 2)

## How to contribute to analytic
create a branch based on the development branch, add your changes to the app.py commit and push your code
then create a pull request from you branch that targets the development branch.
Once you code is reviewed it eill be mergedon dev branch once tests are accepted it will be merged on main and deployed

## Deployment Process
Once the pull request is merged on Main branch the following happens:
1- aws Codebuild pipline executes the buildspec.yml file and push the resulting image to a repo in aws ecr
2- The image ARN is used in the analytics-api.yml file  which is deployed along with the database config files
3 the pod associated with the analytics service thus, the app is up and running.