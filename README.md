Amazon Web Services Foundations Benchmark CIS
================
Configure AWS Tenant to be [CIS](https://www.cisecurity.org/cis-benchmarks/) compliant

Based on [CIS Amazon Web Services Foundations Benchmark 1.4.0 ](https://workbench.cisecurity.org/benchmarks/1408)

Caution(s)
-------
This role **will make changes to the subscription** which may have unintended consequences. This is not an auditing tool but rather a remediation tool to be used after an audit has been conducted.

This role was developed against a new Azure Tenant and subscription. If you are implementing to an existing tenant and subscription(s) please review this role for any site specific changes that are needed.

To use release version please point to main branch

Additional costs may be incurred for specific features
- 1.1 Sounds expensive


Documentation
------------
[Installing AWS CLI](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2-linux.html)


Requirements
------------
- RHEL 8 or CentOS 8 to execute the playbook/role
- AWS Tenant 
  - A IAM with AdministratorAccess permissions

Dependencies
------------
- Python3
- Ansible 2.9+
- AWS CLI 2.2.8+

Known Issues
------------
- 1.11
  - 🔩HIGH COMPLEXITY. Need a way to determine which access key to delete
- 1.13
  - 🔩HIGH COMPLEXITY. Need a way to programatically determine which Access Key to remove
- 1.14
  - 🔩HIGH COMPLEXITY. Involves creating new access keys, and deleting old ones.
- 1.16
  - 🔩HIGH COMPLEXITY. Involves removing the default 'AdministratorAccess' policy from all users, groups, and Roles
- 1.17
  - 🔩HIGH COMPLEXITY. COMPLEX but probably do-able. Need to create a new support role.
- 2.1.3
  - 🔩HIGH COMPLEXITY. You must use your 'root' account to enable MFA Delete on S3 buckets.
- 3.4
  - 🔩HIGH COMPLEXITY. Need a way to ensure the values for "--cloud-watch-logs-log-group-arn" and "--cloud-watch-logs-role-arn" are specific to the respective region
- 3.7
  - 🔩HIGH COMPLEXITY. Need to add this command: "aws kms put-key-policy" for each CloudTrail for each Region. Need to apply a pretty complex policy.
- 3.8
  - ⚠ https://stackoverflow.com/questions/52683015/how-to-get-list-of-all-child-elements-with-field-from-parent 
- 3.10 & 3.11
  - ⚠ Had trouble finding the S3 buckets that were missing their respective policy. Worked around by just applying "All"(Read and Write) in single step
- Section 4
  - Assumes 3.1 was already complete
  - Probably an opportunity to have a single block and loop (instead of 15 distinct blocks) because they are very similar