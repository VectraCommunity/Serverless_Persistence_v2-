

Lab Cleanup
===========

Cleanup
++++++++++++

Exit pacu
Delete Lambda functions
There will be 2
- aws lambda delete-function --function-name admin_function-<initials> 
- Function created by Pacu

Detach the policies from the user "chris".  This was added in a pervious step.

aws iam  detach-user-policy --user-name <username> --policy-arn arn:aws:iam::aws:policy/AdministratorAccess

Run cloudgoat destroy lambda_privesc