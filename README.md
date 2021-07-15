# Introduction to AWS Security Hub

## Intro 

- Data is at the center of your business, and protecting that data is extremely important
- AWS Security Hub gives you a unified view of your security alerts across AWS
- Security Hub aggregates, organizes, and prioritizes your alerts from multiple AWS services and third-party solutions.

## Challenges

- Too many different data formats
- Hard to prioritize alerts
- These security alerts are separated between dashboards
- No unified compliance checking

# Elevator pitch

Amazon Web Services has a lot of resources and accounts that you need to keep tabs on for security and compliance. This is too segregated and large to manage for any reasonable sized organization. Security Hub solves this by automatically gathering data, alerting on the security problems it finds, and prioritizing which one of them should be done more urgently. It covers most AWS resources, from EC2 machines, to S3 buckets, to networking permissions, to user security rules like password complexity and multi-factor authentication.

# Setting up Security Hub

## Setup

- Security Hub is quick and easy to set up
- Go to the service page and click on *enable*
- Security Hub is a regional service. It has to be enabled on every region that you want to use it on

# The Security Hub console

## Main features

- When opened, you get a summary dashboard of your alerts
- The second tab is a security international standard summary
- The third tab is a collection of generated insights with filtering
- The fourth tab is a table of security issues that you can filter
- The fifth tab is a collection of data sources from third-party partners
- The last tab is information for custom actions, account usage, and other general settings

# Account integration

## Managing account security

- Security Hub is integrated with AWS Organization
- Easy setting up and enabling multi-account management
- Checking any existing and new account for security problems
- Security alerting for up to 5000 AWS accounts
- Every account enrolled in Security Hub must have AWS Config enabled and configured

## Delegated administrator access

- You can provide an account ID to delegate Security Hub administrator access
- Grants trusted account access with AWS Organizations to Security Hub
- This delegated account can see the accounts on the organization
- When setting up for the first time, Security Hub detects the delegation and displays the delegated administrator section
- This delegated administrator account is the Security Hub master and selects the member accountsi
- Monitored accounts can be added automatically if you check **auto-enable** on the settings page.

# Security standards

## AWS Foundational Security Best Practices

- Automated security checks for AWS accounts and resources for security checks
- Defined by security experts at Amazon
- Improves your security posture in AWS

## CIS AWS Foundations Benchmark

- Laid down by the Center for Internet Security
- Automated checks for compliance with a CIS subset of standards

## Payment Card Industry Data Security Standard (PCI DSS)

- Security compliance standard for entites storing, processing and transmitting credit card holder data
- Automated checks against this official standard subset of rules
- Required for PCI DSS validation, for example, for online stores that store this data

# Enabling AWS Security Hub

## Configuration

- Select the security standards from the list before that you want to enable (usually the first two)
- Enable security hub and wait for it to gather alert data from several compatible AWS services

This data-gathering process can usually take from around two hours to a day depending on the list. After that, these checks are periodically run automatically.

These standard lists can also be enabled or disabled after enabling AWS Security Hub on the Security Dashboard.

## Pricing

- AWS Security Hub is free for the first 30 days
- After this period, the pricing is calculated per alert in batches

### Security checks

- The first 100.000 checks are $0.0010 each
- the next 400.000 checks are $0.0008
- From then on, each check is $0.0005

This cost is calculated per account, per region, per month

### Finding ingestions

- Finding ingestions are free if they are associated with security checks
- If not associated with a security check, the first 10.000 finding ingestions are free
- from then on, each finding ingestion not associated with a security check is $0.00003

### Other costs

Keep in mind that there are other services associated with security hub that have their own costs, These services are:

- AWS Firewall Manager
- IAM Access Analyzer
- Amazon GuardDuty
- Amazon Inspector
- Amazon Macie
- AWS Systems Patch Manager
- Amazon Detective

You have the option of doing a [pricing estimate](https://calculator.aws/#/) of your AWS Security Hub bill.

# Existing problems and proposed solutions

## Different alert formats

- Companies have between 15 and 60 security tools used
- These tools all have different alerting formats
- This data has to be parsed into a common format before it can be assessed
- Security Hub solves this by processing all its findings into the AWS Security Finding Format (ASFF)

## Service integrations

- Security tools don't integrate with each other
- Gathering their findings into a single place is complicated and time-consuming
- Security Hub solves this by integrating services into its processing system

### First-party AWS services

- AWS Firewall Manager triggers alerts from WAF or ACL rules, or identified attacks
- AWS IAM Access Analyzer sends an alert, for example, when an external user gets total access to a resource
- Amazon GuardDuty sends all the events it gets continuously to AWS Security Hub based on events from several AWS services like CloudTrail or CloudWatch.
- Amazon Macie alerts you if it finds personally identifiable data, or sensible files stored in an AWS S3 bucket
- Amazon Inspector sends alerts about resource misconfigurations and vulnerabilities
- AWS Systems Manager Patch Manager sends alerts about missing important patches on resources, like EC2 machines.
- Amazon Detective gets findings from AWS Security Hub and helps you find the problem via Root Cause Analysis

### Third-party services

#### Readily available

AWS allows you to get alerts, findings and analysis warnings from third-party services through the AWS Partner Network (APN) like firewall information, Managed Security Service Providers (MSSP's), Security Information and Event Management (SIEM) tools, third-party ticketing software...

These integrations are enabled through the AWS Marketplace on AWS Security Hub. Some available integrations on the marketplace are:

- Atlassian Jira
- Atlassian OpsGenie
- IBM QRadar
- PagerDuty
- Slack
- Splunk Enterprise

#### Custom integrations

Security Hub can accept data from any security product through its API:

- Create a product Amazon Resource Name
- Define the product name
- Supply IDs for your findings when making the API calls
- Provide the account ID to query into
- Set the dates

Then, you can just generate alerts from your security software on-demand with an API call, all accessible through [the API](https://docs.aws.amazon.com/securityhub/1.0/APIReference/Welcome.html). Sometimes these custom alerts can even be easily built with Amazon products, like [Integrating AWS CloudFormation security tests with AWS Security Hub and AWS CodeBuild reports](https://aws.amazon.com/es/blogs/security/integrating-aws-cloudformation-security-tests-with-aws-security-hub-and-aws-codebuild-reports/).

## Priority and urgency

- Customers can deal with dozens, maybe hundreds of alerts a day. Thousands for a big company.
- Analyzing and prioritizing these alerts takes time
- AWS Solves this with Findings and Insights

### Findings

- Findings are security alerts based on the list of security standards you enabled
- Fidings are parsed, prioritized, and stored up to 90 days
- Every alert gives you the resources that failed the check, and where to fix it
- Automatically integrated with AWS services
- Easily integrated with third party services
- Custom integrations available

### Insights

- Findings grouped by similar resources and accounts
- Quickly flags the most vulnerable resources that need immediate attention
- Powerful pre-configured managed insights
- Ability to create custom insights easily based on filters

## Complicated compliance

- Some companies have complicated compliance requirements, like credit card data-handling companies
- No easy way to keep track of the compliance checks
- Compliance can be an internal requirement in a company
- Compliance can be an external requirement for business (NIST for security, HIPAA for health data, PCI for credit card handling)
- Security Hub solves this problem with automated security checks for selected available security standards

# Taking action

- Once you identify a security problem, you need to deal with that problem
- You can manually check and deal with these problems
- You can also automatically solve some configuration problems on Security Hub alerts

## Manual remediation

- You can manually check and deal with these problems 
- AWS Security Hub generates an alert that links to AWS Config
- AWS Config will list the affected resources that triggered this alert
- you can directly open the resource from there and go fix the issue

## Automatic remediation

- When the impact on workloads is low, these problems can be automatically solved from Security Hub
- An example is enabling CloudTrail in the account
- Auto remediation is not available when it could interrupt workloads, like changing EC2 instance configurations
- If you understand your workload to automatically fix it, you can setup custom automatic remediations for certain alert types

# Conclusions

If you run a considerable amount of your insfrastructure inside Amazon Web Services, using AWS Security Hub to give you a better lens into cybersecurity is a very compelling option, especially in a day and age where AWS products are more and more diversified, and infrastructure requires looking at more panels and sites. Centralization of alerting is a big step towards a more secure infrastructure without losing time in analyzing every part of it by yourself.
