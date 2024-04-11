# Automate the reporting of Incident Manager

This repo hosts templates written for the AWS Blog Post "[Automate Incident Reports from AWS Systems Manager Incident Manager](https://aws.amazon.com/blogs/mt/automate-incident-reports-from-aws-systems-manager-incident-manager)" published on the [AWS Cloud Operations & Migrations](https://aws.amazon.com/blogs/mt/) blog channel.

## Overview
The solution will demonstrate the process of generating insightful reports within Incident Manager. Our goal is to show you a step by step for generating regular reports and storing them in Amazon Simple Storage Service (Amazon S3). This solution helps you to:
- **Automate report generation**: No more manual work - streamline the process and store reports securely in Amazon S3.
- **Uncover valuable trends**: Identify frequent issues, vulnerable resources, and resolution times.
- **Boost efficiency and security**: Proactively address bottlenecks, prevent recurring problems, and optimize your cloud environment for ultimate resilience.

This is a sample solution using [AWS Systems Manager Automation](https://docs.aws.amazon.com/systems-manager/latest/userguide/systems-manager-automation.html) to execute Python code that extracts metadata from the [AWS Systems Manager Incident Manager](https://docs.aws.amazon.com/incident-manager/latest/userguide/what-is-incident-manager.html) API and then stores the output in a CSV file in an [Amazon Simple Storage Service (Amazon S3)](https://aws.amazon.com/s3/) bucket.

![Architectural Diagram](/Images/ArchitecturalDiagram.png)


## Deployment
### Cloudformation
### Prerequisites
To deploy the application to AWS you need the following:
* An active AWS account
* Incident Manager setup for [Single Account](https://docs.aws.amazon.com/incident-manager/latest/userguide/getting-started.html) or [Cross-Account and Cross-Region](https://docs.aws.amazon.com/incident-manager/latest/userguide/incident-manager-cross-account-cross-region.html).



### Getting Started
1. Download deployment template. For this example we'll use the [IncidentManagerReport.yml](/Templates/CloudFormation/IncidentManagerReport.yml) CloudFormation template.
2. [Create a stack from the AWS CloudFormation Console](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/cfn-console-create-stack.html).  The CloudFormation template will create the resources shown in the architectural diagram above.

### Template Parameters
The stack template includes the following parameters:

| Parameter | Required | Description |
| --- | --- | --- |
| RunOnSchedule | Optional | Scheduled the process vs running on-demand. |
| AssociationSchedule | Optional | The [cron expression](https://docs.aws.amazon.com/systems-manager/latest/userguide/reference-cron-and-rate-expressions.html#reference-cron-and-rate-expressions-association) to use for the association in UTC. |

If you set `RunOnSchedule` parameter to `false` in the template, CloudFormation will create the required Systems Manager Automation document and other resources, however you would need to manually execute the above created automation document to generate report.

## Security

See [CONTRIBUTING](CONTRIBUTING.md#security-issue-notifications) for more information.

## License

This library is licensed under the MIT-0 License. See the LICENSE file.
