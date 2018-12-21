# AWS Naming & Tagging Conventions
AWS Tagging policy and naming convention for all resources created within any AWS accounts under the AWS Master Account

# Table of Contents
[Terms and Abbreviations 3](#_Toc500424982)

[Bibliography](#bibliography)

[Executive Summary 5](#executive-summary)

[AWS Terms and Abbreviations 5](#aws-terms-and-abbreviations)

[Tagging Overview](#tagging-overview)

[Tagging Best Practices 6](#tagging-best-practices)

[Resource Groups 6](#resource-groups)

[Compound Tags 6](#compound-tags)

[Style Rules 6](#style-rules)

[Tagging Region Codes 6](#tagging-region-codes)

[Enterprise Tagging Standards 7](#enterprise-tagging-standards)

[Environment Names 7](#environment-names)

[Name Tag Format 8](#name-tag-format)

[AMI Versioning 9](#ami-versioning)

[Additional Tags 9](#additional-tags)

[Operational Tags 10](#operational-tags)

[Business Tags 10](#business-tags)

[Security Tags 10](#security-tags)

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
