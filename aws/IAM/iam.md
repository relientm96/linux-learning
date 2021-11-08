# Identity Access Management (IAM)

What is IAM?

* AWS managed service
* Enables you to state whether a party should be allowed or denied the ability to invoke an AWS action on a resource.

## Definitions

* Policy - Document outlining permissions granted/denied for a principal to use an AWS resource. Usually in `json` or `yaml`.
* Principal - The party (AWS user/role/account) that the policy applies to.
* Effect - A string literal. Either `Allow` or `Deny`.
* Action - AWS Actions that are bounded by the effect.
* Resource - The resource(s) in question that listed actions are tied to.

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
Statement <SID> <grants/denies> the party <principal> actions 
<action1, action2, .... actionN> on AWS resources <resource1, 
resource2, ... resourceN>
```

## IAM Workflow

