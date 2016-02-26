Role Name
=========

Based on
[Christian E Willman's](https://github.com/christianewillman)
[aws-cloudwatch-logs role](https://github.com/christianewillman/ansible-aws-cloudwatch-logs).

Adapted for use with CentOS 7 as configured for OU Libraries.

Requirements
------------


Your EC2 machine role should have an IAM Policy to enable creating and writing logs. Here's an example policy:
```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "logs:CreateLogGroup",
        "logs:CreateLogStream",
        "logs:PutLogEvents",
        "logs:DescribeLogStreams"
    ],
      "Resource": [
        "arn:aws:logs:*:*:*"
    ]
  }
 ]
}
```
Any pre-requisites that may not be covered by Ansible itself or the role should be mentioned here. For instance, if the role uses the EC2 module, it may be a good idea to mention in this section that the boto package is required.

Role Variables
--------------

A description of the settable variables for this role should go here, including any variables that are in defaults/main.yml, vars/main.yml, and any variables that can/should be set via parameters to the role. Any variables that are read from other roles and/or the global scope (ie. hostvars, group vars, etc.) should be mentioned here as well.

Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

Usage
----------------

Include the `ec2-cloudwatch-logs` role in your playbook yml like this:

    - role: ec2-cloudwatch-logs
      logs:
        - file: /var/log/syslog
          format: "%b %d %H:%M:%S"
          group_name: syslog
        - file: /var/log/my_cool_log
          format: "%b %d %H:%M:%S"
          group_name: my-cool-log

License
-------

TBD

Author Information
------------------

Jason Sherman
