.. title:: Vectra Community



.. toctree::
   :maxdepth: 2
   :caption: Serverless Persistence Labs
   :name: _serverless_persistence_labs
   :hidden:

   build_attack_machine/build_attack_machine
   lambda_attack/lambda_attack
   lab_cleanup/lab_cleanup

.. toctree::
   :maxdepth: 2
   :caption: Additional Resources
   :name: _additional_resources
   :hidden:

   

.. _welcome:

--------------------------------
Welcome!
--------------------------------

The Vectra Community lab for Serverless Persistence.

What is Detect for AWS?
=======================

Detect for AWS offers advanced Threat Detection & Response coverage for the AWS control plane. We leverage advanced AI & ML techniques to monitor all activity in an organization’s global AWS footprint for malicious behaviors. Detect for AWS leverages CloudTrail log and contextual IAM information to find malicious activity, and then attribute it to the malicious actor itself using Vectra’s Kingpin technology.  Detect for AWS is delivered as a SaaS (Software as a Service) solution in Vectra’s cloud.

Lab Objective
=============
The Detect for AWS Detection lab has been created to empower Vectra field staff and customers with the option to show concrete Detect for AWS Detections in live environments when the situation calls for it. To accomplish this objective, this lab contains a number of scripts, supporting resources, and associated attacker narratives that provide context for both the value and means of test execution.

Scenario 
========
An attacker finds AWS user credentials in a GitHub repository.  These accidentals leaks can happen through misconfiguration of a. gitignore file. 

The attack consists of two parts. First attacker performs privilege escalation using Lambda. After the privilege escalation attacker create persistence using a lambda create creates backdoor IAM user credentials for all new users

Lambda Privilege Escalation (Part 1)
====================================
- Stolen IAM credentials have limited access, but can assume IAM roles and query IAM details
- After IAM discovery campaign, attacker discovers two roles
   - IAM role that has full Lambda access 
   - IAM service role that has admin permissions that can only be assumed by Lambda service
- Attacker assumes the Lambda admin role
- Attacker creates a privilege escalation Lambda
- Attacker passes a high privilege Lambda service role 
- Attacker has achieved privilege escalation 

Serverless Persistence (Part 2)
================================
- Attacker pivots to pacu and uses escalated privileges to list Lambda functions
- Attacker creates a new Lambda function
   - Function has CloudWatch events rule that will trigger when new IAM users is created


Lab Notes
=========
-  There are other ways to install the tools and will depend on distro.
-  Setting up the AWS profile may very based on an organizations
   requirements. For instance SSO would vary between org.

Requirements
============
-  Linux or MacOS. Windows is not officially supported.

   -  If you are using Windows we recommand install
      `WSL2 <https://docs.microsoft.com/en-us/windows/wsl/install>`__
   -  If you are using a Linux virtual machine AWS EC2 is not supported
   -  In this guide a new Ubuntu VM was created in VM Fusion. This guide
      goes through setting up the Ubuntu VM.

-  Python3.6+ is required.
-  Terraform >= 0.14 installed and in your $PATH.
-  The AWS CLI installed and in your $PATH, and an AWS account with
   sufficient privileges to create and destroy resources.

   -  AWS `Named profile
      configured <https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-profiles.html>`__
