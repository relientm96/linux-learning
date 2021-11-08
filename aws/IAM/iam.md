# Identity Access Management (IAM)

What is IAM?

* AWS managed service
* Enables you to state whether a party should be allowed or denied the ability to invoke an AWS action on a resource.
* IAM decides **who** can (or can’t) do **what** to **which** AWS resources.

## Definitions

IAM runs on policy documents, which contain a list of IAM statements.

Each statement contains the following fields:

* Principal - The party (AWS user/role/account) that the policy applies to (**who**).
* Effect - A string literal. Either `Allow` or `Deny`. (**can or can't**)
* Action - List of allowed actions on resource (**what**)
* Resource - The resource(s) in question that listed actions are tied to. (**which**)

## Policy Structure

```json
{
  "Version": "2012-10-17",
  "Statement": [
    ... one or more Statement objects ...
    {
      "Sid": ... (Optional) Statement Identifier ...,
      "Effect": ...either "Allow" or "Deny" ...,
      "Action": [... array of Actions ...],
      "Resource": [ ... array of Resources ... ]
      ],
      "Principal": { ... one kind of principal ...
        "AWS": [... array of AWS accounts and IAM principals ...]
        "Service": [... array of AWS AWS services ...]
        ... others ...
      }
      "Condition": { ... (Optional) extra condition objects }
    }
  ]
}
```

Ultimately, a policy document can be read as a list of statements of the following form:

```bash
Statement <SID> <grants/denies> <principal> actions 
<action1, action2, .... actionN> on AWS resources <resource1, 
resource2, ... resourceN>
```

## IAM Workflow