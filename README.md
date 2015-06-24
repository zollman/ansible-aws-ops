# Generic AWS module

Generic Ansible module for running arbitrary AWS commands using a command shape similar 
to the AWS CLI

# Usage

Depends on botocore, which must be installed globally:

    pip install botocore

Then to run the example playbook, using credentials stored locally:

    ansible-playbook -i ansible-inventory.ini demo.yml

`demo.yml` contains a few basic examples.

`demo-include.yml` shows how the AWS building blocks can be combined into
idempotent sequences of tasks.

# Developer notes

1. The module also depends on jmespath to implement queries against the
   returned data (equivalent to the AWS `--query` option). This is 
   not called out separately because botocore includes a dependency on
   jmespath itself.

2. Because the module uses boto, you can either provide AWS credentials
   via the `aws_access_key_id`, `aws_secret_access_key` and 
   `aws_session_token` parameters -- or if you're running within AWS, 
   it will grab credentials from the instance metadata service or 
   environment variables if those parameters are not specified.
