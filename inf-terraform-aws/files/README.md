# ODS AWS Quickstarter

This Quickstarter can be used to deploy AWS resources. It's primary usage is to build a stack based on Terraform modules, but it also supports Cloudformation, by wrapping this in Terraform.

## What is a Stack?

A stack is a useful combination of reusable modules or blueprints and infrastructure code, typically for the purpose of providing a digital product's technical fundament.

## How to use this Stack?

The behavior of a stack is determined by its purpose and the set of input parameters. Here is an overview of the *inputs* and *outputs* available for this stack.

<!-- BEGINNING OF PRE-COMMIT-TERRAFORM DOCS HOOK -->
## Requirements

| Name | Version |
|------|---------|
| terraform | >= 0.13 |
| aws | 3.24.1 |
| random | 3.0.1 |

## Providers

| Name | Version |
|------|---------|
| aws | 3.24.1 |
| local | n/a |
| random | 3.0.1 |

## Inputs

| Name | Description | Type | Default | Required |
|------|-------------|------|---------|:--------:|
| data\_bucket\_name | The name of the S3 data bucket. | `string` | `"bi-qs-demo-quicky"` | no |
| meta\_computer\_system\_name | The name of the computer system. | `string` | `"quickstarter"` | no |
| meta\_contact\_email\_address | An email address of a contact person. | `string` | `"changeme@phoenix.com"` | no |
| meta\_environment\_type | The type of the environment. Can be any of development, evaluation, productive, qualityassurance, training, or validation. | `string` | `"test"` | no |
| name | The name of the stack. | `string` | `"stack-aws-quickstarter"` | no |

## Outputs

| Name | Description |
|------|-------------|
| inputs2outputs | all inputs passed to outputs |
| meta\_computer\_system\_name | The name of the computer system. |
| meta\_contact\_email\_address | An email address of a contact person. |
| meta\_environment\_type | The type of the environment. |
| name | The name of the stack. |

<!-- END OF PRE-COMMIT-TERRAFORM DOCS HOOK -->

## How to test this Stack?


Testing the functionality of this stack requires the following dependencies: `make`, `tee`, `ruby`, [`bundler`](https://bundler.io/), and [`terraform`](https://www.terraform.io/). Once installed, run `make test` from the command line.


Note that, when running tests, stacks will interact with some cloud provider, such as *AWS*, *Azure* or *VMware*. It is up to you to provide sufficient configuration to enable these interactions, which differs between vendors. Here is an example for *AWS* that uses environment variables (via [Configuring the AWS CLI](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-getting-started.html)):

```
$ export AWS_ACCESS_KEY_ID=...
$ export AWS_SECRET_ACCESS_KEY=...
$ export AWS_DEFAULT_REGION=us-east-1
$ make test
```

## How to extend a Stack?

Extending a stack basically involves adding more blueprints whichever fit, and garnish it with custom infrastructure code if necessary.

Setting up stack development guardrails requires the following dependencies: `make`, `tee`, `ruby`, [`bundler`](https://bundler.io/), `python`, [`pre-commit`](https://pre-commit.com/) [`terraform`](https://www.terraform.io/), and [`terraform-docs`](https://github.com/segmentio/terraform-docs). Once installed, run `make install-dev-deps` to install a set of quality improving *pre-commit hooks* into your local Git repository. Upon a `git commit`, these hooks will make sure that your code is both syntactically and functionally correct and that your `README.md` contains up-to-date documentation of your stack's supported set of *inputs* and *outputs*.

## Environments
The stack supports multiple environments (Testing/DEV/QA/PROD) within OpenDevStack. The behaviour of the stack in the environments can be controlled within the **environments** directory.
The *.yml files define the Jenkins secrets to read and are used to deploy into the right environments.
The *.json files can override variables from **variables.tf** in case different environments request different inputs (e.g. deploy a smaller version of the stack in DEV).

## Problems? Questions? Suggestions?

In case of problems, questions or suggestions, feel free to file an issue with the respective project's repository. Thanks!
