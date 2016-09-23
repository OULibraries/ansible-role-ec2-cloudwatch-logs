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


Dependencies
------------


Usage
----------------

Include the `ec2-cloudwatch-logs` role in your playbook yml like this:
```
    - role: ec2-cloudwatch-logs
      logs:
        - file: /var/log/syslog
          format: "%b %d %H:%M:%S"
          stream_name: "{hostname}_syslog"
          group_name: syslog
        - file: /var/log/secure
          format: "%b %d %H:%M:%S"
          stream_name: "{hostname}_secure"
          group_name: secure
        - file: /var/log/messages
          format: "%b %d %H:%M:%S"
          stream_name: "{hostname}_messages"
          group_name: messages
        - file: /var/log/nginx/*.access.log
          format: "%d/%b/%Y%H:%M:%S %z"
          stream_name: "{hostname}_nginx_access_log"
          group_name: nginx_access_log
        - file: /var/log/my_cool_log
          format: "%b %d %H:%M:%S"
          stream_name: "{hostname}_nginx_access_log"
          group_name: my_cool_log
```

License
-------

TBD

Author Information
------------------

Jason Sherman
