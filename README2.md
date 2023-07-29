
# CI/CD with monitoring
This project is a part of the 3rd project in cloud developer nanodegree.

## Description

This repo has a node frontend and backend application for employee management. The application is deployed to AWS using
circleCI for CI/CD, cloudformation to provision the infrastructure, ansible for deployment configuration and 
prometheus for monitoring during runtime. 

It has a fully automated CI/CD release pipeline, from build to production. It follows the blue-green deployment model.
The new infrastructure is created using Cloudformation(IaC), configured using ansible, after successfully passing 
the smoke tests, the newly crated and configured infrastructure is promoted to production by updating the cloudfront
domain, and the old infrastructure is destroyed. 

For monitoring, prometheus is used, the node exporter is configured by ansible in the configuration phase.
The prometheus instance is set up separately, and new instances are discovered using prometheus service discovery
[link](https://codewizardly.com/prometheus-on-aws-ec2-part2/).

The different phases of the CI/CD pipeline are shown,

**Continuous Integration**

1. Build Phase - Build the frontend and backend applications.
2. Test Phase - Test the frontend and backend applications.
3. Analyse Phase - Check for security vulnerabilities and outdated dependencies.

**Continuous Delivery**

4. Create the infrastructure - Create the infrastructure using cloudformation.
5. Configure the infrastructure - Configure the infrastructure using ansible.
6. Run migrations - Run migrations for the database.
6. Deploy the infrastructure - Deploy frontend and backend applications using ansible.
7. Smoke Test - Checking if the new deployment is working .
8. Rollback - If there is an issue detected during the smoke test phase, the new infra is cleaned-up/ deleted.
9. Promotion Phase - If the smoke test passes successfully, the new infra is promoted to production by updating 
the cloudfront distribution.
10. Cleanup - The old infra is cleaned-up deleted.

## Pipeline diagram

![udapeople-pipeline](https://github.com/nikhil-31/django-docker-kubernetes-deploy-scripts/assets/19944703/7c94c26e-921c-4770-bc92-ab71be2db119)


## Technologies used

- [Circle CI](www.circleci.com) - Cloud-based CI/CD service
- [Amazon AWS](https://aws.amazon.com/) - Cloud services
- [AWS CLI](https://aws.amazon.com/cli/) - Command-line tool for AWS
- [CloudFormation](https://aws.amazon.com/cloudformation/) - Infrastructure as code
- [Ansible](https://www.ansible.com/) - Configuration management tool
- [Prometheus](https://prometheus.io/) - Monitoring tool


## Getting started 

1. Fork the repository and work on your own repo, please do not push updates to this repo.
2. Setup command line access to your AWS account with AWS CLI [link](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-configure.html).
3. Create an account on circleCI, they have free credits to run the pipeline with a rate limit, check their website 
and signup for more details [link](https://circleci.com/).
4. Setup the repo inside CircleCI to build the repo when a new commit is made [link](https://circleci.com/docs/getting-started/).
5. 