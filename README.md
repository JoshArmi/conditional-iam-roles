# Conditional IAM Roles

This is a very small proof of concept showing how you can use IAM condition to allow for a configurable set of policies to be applied to an IAM role.

## For more information

Read the blog post here: [https://josharmi.github.io/posts/conditional-iam-roles/](https://josharmi.github.io/posts/conditional-iam-roles/)

## Why you might want to use this

If you are charged with delivering functionality into accounts you do not own or are not responsible for, it is important to give the consuming team control over what your role can do.

For example, if enacting compliance remediations of resources in other accounts, they may be happy for only certain resources or actions to be attempted. Rather than have them self edit the role, or accept the maintenance of many disparate roles, this would allow you to let them configure it into a set of known states by toggling parameters.

## How to Deploy

1. Edit the `parameters.json` file to enable or disable the options as required
2. Assume a role in the desired account
3. If creating anew:
    - Run `aws cloudformation create-stack --stack-name ConditionalRole --template-body file://role.yaml --parameters file://parameters.json --capabilities CAPABILITY_NAMED_IAM`
4. If updating:
    - Run `aws cloudformation update-stack --stack-name ConditionalRole --template-body file://role.yaml --parameters file://parameters.json --capabilities CAPABILITY_NAMED_IAM`