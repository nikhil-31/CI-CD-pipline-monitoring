
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


## Screenshots are in the `/screenshots` folder [link](https://github.com/nikhil-31/CI-CD-pipline-monitoring/tree/main/screenshots)

## License
Licensed under the Apache License, Version 2.0 (the "License"); you may not use this file except in compliance with the License. You may obtain a copy of the License at
http://www.apache.org/licenses/LICENSE-2.0 Unless required by applicable law or agreed to in writing, software distributed under the License is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the License for the specific language governing permissions and limitations under the License.

Copyright 2023 Nikhil Bhaskar