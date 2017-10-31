# AWSCertifiedSolutionsArchitectAssociate
Notes and code labs for A Cloud Guru's AWS Certified Solutions Architect Associate course

## IAM - Identity Access Management
- Centralized Control of AWS Account
- Shared Access to AWS account
- Granular Permissions
- Identity Federation (including Facebook, LinkedIn, Active Directory, etc.)
- MultiFactor Authentication (MFA)
- Temporary access for Users/Devices and Services
- Allows for setup of a password rotation policy
- Integrates with many different AWS Services
- Supports PCI DSS Compliance [Payment Card Industry (PCI) Data Security Standard (DSS)](https://www.pcisecuritystandards.org/document_library?category=pcidss&document=pci_dss)

#### Terms
- **User** - end users
- **Group** - a collection of Users under one set of Permissions<br/>
  A group is a way of applying a set of permissions to multiple Users.
- [**Role**](http://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles.html)
  - IAM roles are a secure way to grant permissions to entities that you trust.  IAM roles issue keys that are valid for short durations, making them a more secure way to grant access.  An IAM role is similar to a user, in that it is **an AWS identity with permission policies that determine what the identity can and cannot do in AWS**. However, instead of being uniquely associated with one person, **a role is intended to be assumable by any user, resource or service that needs it**. Also, **a role does not have any credentials** (password or access keys) associated with it (again, it might be an application that get's the role). Instead, if a user is assigned to a role, access keys are created dynamically and provided to the user.  
  - Here are examples of entities that could be given a Role:
    - IAM user in another account
    - Application code running on an EC2 instance that needs to perform actions on AWS resources
    - An AWS service that needs to act on resources in your account to provide its feature
    - Users from a corporate directory who use identity federation with SAML
  - Here are some scenarios where Roles would be used;<br/>
    A Role can be used to help **prevent accidental access to or modification of sensitive resources**.  You can **grant your IAM users permissions to switch to roles** that you create within your own or another AWS account.  They can switch roles easily using the IAM console **to use permissions that you don't ordinarily want them to have**, and then exit the role to surrender those permissions.  
    - [Provide access for an IAM user in one AWS account that you own to access resources in another account that you own](http://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_common-scenarios_aws-accounts.html)
    - [Provide access to IAM users in AWS accounts owned by third parties](http://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_common-scenarios_third-party.html)
    - [Provide access for services offered by AWS to AWS resources](http://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_common-scenarios_services.html)
    - [Provide access for externally authenticated users (identity federation)](http://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_common-scenarios_federated-users.html)
- [**Permission and Policy**](http://docs.aws.amazon.com/IAM/latest/UserGuide/access.html)
    - [**Permission**](http://docs.aws.amazon.com/IAM/latest/UserGuide/access_permissions.html) - Permissions let you specify who has access to AWS resources, and what actions they can perform on those resources.  Permisions can be added by
      - adding the user to a group
      - copying permissions from another user
      - attaching existing policies directly to the user (an AWS Managed Policy)
    - [**Policy**](http://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies.html) - a document that defines one or more permissions

IAM is global (regionless).  IAM users, groups and roles can be used in any region.

See the lab on creating an IAM users
- Note that if the user is given programmatic access, then their access key id and secret will be shown immediately upon successful creation - **the access key secret is only shown one time - immediately after creating the user**.  You download the CSV or send an email to the user with the credentials.
- The access key id and secret can only be used for programmatic access.  They cannot be used to log into the console.
- neither can the User name and password be used for programmatic access.
- programmatic access can be created, regenerated or taken away by editing the user's 'Security Credentials' in the console.

[Ed](https://emurmur.signin.aws.amazon.com/console)
- for programmatic access:
  - accesskeyId: AKIAI74AP6GOU77S23JA
  - accesskeySecret: 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
