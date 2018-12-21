# AWS Naming & Tagging Conventions
AWS Tagging policy and naming convention for all resources created within any AWS accounts under the AWS Master Account

# Table of Contents
[Terms and Abbreviations](#_Toc500424982)

[Bibliography](#bibliography)

[Executive Summary](#executive-summary)

[AWS Terms and Abbreviations](#aws-terms-and-abbreviations)

[Tagging Overview](#tagging-overview)

[Tagging Best Practices](#tagging-best-practices)

[Resource Groups](#resource-groups)

[Compound Tags](#compound-tags)

[Style Rules](#style-rules)

[Tagging Region Codes](#tagging-region-codes)

[Enterprise Tagging Standards](#enterprise-tagging-standards)

[Environment Names](#environment-names)

[Name Tag Format](#name-tag-format)

[AMI Versioning](#ami-versioning)

[Additional Tags](#additional-tags)

[Operational Tags](#operational-tags)

[Business Tags](#business-tags)

[Security Tags](#security-tags)

[AWS Resource Suffixes 11](#aws-resource-suffixes)

[Name Tag Examples 12](#name-tag-examples)

## Terms and Abbreviations

The following table lists the Terms and Abbreviations that are
referenced within the document.

| Term    | Explanation                                |
| ------- | ------------------------------------------ |
| AMI     | Amazon Machine Image                       |
| AWS     | Amazon Web Services                        |
| AWS IAM | AWS Identity and Access Management Service |
| DB      | Database                                   |
| EBS     | Elastic Block Store                        |
| EC2     | AWS Elastic Compute Cloud                  |
| OS      | Operating System                           |
| PCI     | Payment Card Industry                      |
| PII     | Personally identifiable information        |
| RBAC    | Role-based Access Control                  |
| RDS     | Relational Database Service                |
| S3      | Simple Storage Service                     |
| SNS     | Simple Notification Service                |
| SQS     | Simple Queue Service                       |
| VPC     | Virtual Private Cloud                      |

### Bibliography

The table below contains information about, and (where possible) links
to, supporting documentation.

<table>
<thead>
<tr class="header">
<th>NO.</th>
<th>DESCRIPTION</th>
<th>VERSION</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ol type="1">
<li></li>
</ol></td>
<td>“How Should I Tag my AWS resources?” - <a href="https://d0.awsstatic.com/aws-answers/AWS_Tagging_Strategies.pdf" class="uri">https://d0.awsstatic.com/aws-answers/AWS_Tagging_Strategies.pdf</a></td>
<td>June 2, 2017</td>
</tr>
<tr class="even">
<td><ol start="2" type="1">
<li></li>
</ol></td>
<td>AWS Naming Convention Best Practices (tagging) - <a href="http://www.myrtec.com.au/sites/www.myrtec.com.au/files/attachments/aws_naming_convention_best_practices_-_tagging.pdf" class="uri">http://www.myrtec.com.au/sites/www.myrtec.com.au/files/attachments/aws_naming_convention_best_practices_-_tagging.pdf</a></td>
<td>September 11, 2014</td>
</tr>
<tr class="odd">
<td><ol start="3" type="1">
<li></li>
</ol></td>
<td>AWS now supports 50 tags per resource - <a href="https://aws.amazon.com/blogs/security/now-organize-your-aws-resources-by-using-up-to-50-tags-per-resource/" class="uri">https://aws.amazon.com/blogs/security/now-organize-your-aws-resources-by-using-up-to-50-tags-per-resource/</a></td>
<td>August 15, 2016</td>
</tr>
<tr class="even">
<td><ol start="4" type="1">
<li></li>
</ol></td>
<td>User defined tag restrictions - <a href="http://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/allocation-tag-restrictions.html" class="uri">http://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/allocation-tag-restrictions.html</a></td>
<td>LATEST</td>
</tr>
<tr class="odd">
<td><ol start="5" type="1">
<li></li>
</ol></td>
<td>Tagging your EC2 resources - <a href="http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/Using_Tags.html" class="uri">http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/Using_Tags.html</a></td>
<td>LATEST</td>
</tr>
<tr class="even">
<td><ol start="6" type="1">
<li></li>
</ol></td>
<td>Naming Conventions - <a href="https://en.wikipedia.org/wiki/Naming_convention_(programming)" class="uri">https://en.wikipedia.org/wiki/Naming_convention_(programming)</a></td>
<td>August 3, 2017</td>
</tr>
<tr class="odd">
<td><ol start="7" type="1">
<li></li>
</ol></td>
<td>Elasticache replication group naming limits - <a href="http://docs.aws.amazon.com/cli/latest/reference/elasticache/create-replication-group.html" class="uri">http://docs.aws.amazon.com/cli/latest/reference/elasticache/create-replication-group.html</a></td>
<td>As of 06/09/2017</td>
</tr>
</tbody>
</table>

## AWS Terms and Abbreviations

The following terms and abbreviations will be used through this design and implementation of all Enterprise applications.

| Name                       | Value    |
| -------------------------- | -------- |
| Connectivity               | CONN     |
| Database Layer             | RDS      |
| Productuion Environment    | PROD     |
| Dev Test Environment       | DEV/TEST |
| Pre Production Environment | PPE      |
| Management and Monitoring  | MGMT     |
| Private                    | PRI      |
| Public                     | PUB      |

N.B. In the above table the forward slash character (“/”) is part of the Value and is not being used as a delimiter.

## Tagging Overview

AWS provide the ability to tag resources with descriptive metadata. Tags
simplify resource management at scale and will be used for cost
allocation. As the Enterprise plans to implement multiple applications,
multiple application environments and multiple AWS accounts; tagging
must be applied consistently to allow costs to be separated out into
applications, environments and business units.

Each tag consists of a key and a value, both of which are user-defined
strings. Once defined, tags can be used as a filter when requesting
resources, such as Amazon EC2 instances, based on tag keys or values.
Tags are also reported against in Cost Allocation Reports.

Tags provide identification and classification of AWS resources.
Examples of commonly used tags include application identifier,
environment, or owner.

### Resource Groups

Use resource groups. A Resource Group is a collection of resources that
shares one or more tags. It can span services and can be used to create
a custom console that organizes and consolidates resources on a
per-project basis. In AWS, a resource is an entity such as an EC2
instance, a S3 bucket and so on. Using the resource group tool, custom
consoles can be created that organize and consolidate all resources for
a specific project in a single view. For example, all the resources for
a version of TEAM_A in production can be in one resource group whilst
those resources used for TEAM_B be can be in another resource group
(though the Enterprise's cloud operating model dictates that applications must
exist in different accounts).

### Compound Tags

There is a limit of 50 tags per resource in AWS, as such it is a good
practice to combine several tag keys and values into a single compound
tag. For example, rather than creating 3 keys (tags) called “OwnerName”,
“OwnerPhone”, and “OwnerEmail,” the 3 keys should be combined into 1 key
called “OwnerContact,” which could contain the compound values of Name,
Phone, and Email address using a pipe delimiter.

We will assign the Name Tag as a compound value. We will use the hyphen
as a delimiter. An example of the values assigned to the Name Tag are
shown in examples section at the end of this document.

### Style Rules

  - Tag key names are case-sensitive and can contain mixed-case letters,
    numbers, underscores, and hyphens.

  - Tag key names should use upper CamelCase (a.k.a. Pascal case), a
    convention that combines words/abbreviations by beginning each word
    with a capital letter such as “MiscMetadata” and “SupportEndpoints”.

  - Tag values are case-sensitive and should not use the semi-colon
    (“;”), equal sign (“=”), or pipe (“|”) characters as these are
    used as delimiters in compound values.

  - Compound tag value key names should use Pascal case followed by an
    equal sign (“=”) such as
    KeyName1=value1-value2-value3;KeyName2=value1-value2-value3
    
## Tagging Region Codes

AWS’ regions codes are unique; therefore, they will be abbreviated as
follows:

| Region         | Region Code |
| -------------- | ----------- |
| ap-northeast-1 | an1         |
| ap-northeast-2 | an2         |
| ap-south-1     | as1         |
| ap-southeast-1 | ase1        |
| ap-southeast-2 | ase2        |
| ca-central-1   | cc1         |
| eu-central-1   | ec1         |
| eu-west-1      | euw1        |
| eu-west-2      | euw2        |
| sa-east-1      | se1         |
| us-east-1      | ue1         |
| us-east-2      | ue2         |
| us-west-1      | uw1         |
| us-west-2      | uw2         |

## Business Tags

These can be used to capture business relevant information and which
part of the business is responsible for this resource. Can greatly speed
up the elimination process in an event of failure or
attack.

| Tag            | Description                                                                                                                            |
| -------------- | -------------------------------------------------------------------------------------------------------------------------------------- |
| SquadName      | Squad / Business are responsible for resource                                                                                          |
| CostCentre     | Business group to be billed for the AWS resources                                                                                      |
| PartnerContact | Value contains contact information for external managed services partner Pipe separated John Smith| +44 0000 00000 |jsmith@example.com |

## Security Tags

To obtain a full visibility over account surface data we use these
security classification tags in conjunction with the [Additional
Tags](#additional-tags) to map which classification of data is where.
AWS Config Rules can also be set where PCI data can only sit in
Network=Red.

| Tag             | Description                                                                                   |
| --------------- | --------------------------------------------------------------------------------------------- |
| Compliance      | An identifier for workloads designed to adhere to specific compliance e.g. Normal / PII / PCI |
| Permissions     | An identifier for the specific entity that can modify the resource                            |
| LastReviewed    | Last time this instance was reviewed for compliance - YYYY-mm-dd                              |
| ApprovedVersion | Steps which are taken to approve AMI image                                                    |
| ApprovedBy      | Department or software which has approved AMI for use in WorldPay                             |

