# sample repo - code that create resource in 2 regions 

## Intro

This manual is dedicated to create Amazon AWS resources in two regions using terraform code.

Tested on Mac OS X.

## Requirements

- Hashicorp terraform recent version installed
[Terraform installation manual](https://learn.hashicorp.com/tutorials/terraform/install-cli)

- git installed
[Git installation manual](https://git-scm.com/download/mac)

- Amazon AWS account credentials saved in .aws/credentials file
[Configuration and credential file settings](https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-files.html)

## Preparation 
- Clone git repository. 

```bash
git clone https://github.com/antonakv/tf-ob-2regions.git
```

Expected command output looks like this:

```bash
Cloning into 'tf-ob-2regions'...
remote: Enumerating objects: 12, done.
remote: Counting objects: 100% (12/12), done.
remote: Compressing objects: 100% (12/12), done.
remote: Total 12 (delta 1), reused 3 (delta 0), pack-reused 0
Receiving objects: 100% (12/12), done.
Resolving deltas: 100% (1/1), done.
```

- Change folder to tf-ob-2regions

```bash
cd tf-ob-2regions
```

## Run terraform code

- In the same folder you were before run init


```bash
terraform init
```

Sample result

```bash
$ terraform init

Initializing the backend...

Initializing provider plugins...
- Finding latest version of hashicorp/aws...
- Installing hashicorp/aws v3.42.0...
- Installed hashicorp/aws v3.42.0 (self-signed, key ID 34365D9472D7468F)

Partner and community providers are signed by their developers.
If you d like to know more about provider signing, you can read about it here:
https://www.terraform.io/docs/cli/plugins/signing.html

Terraform has created a lock file .terraform.lock.hcl to record the provider
selections it made above. Include this file in your version control repository
so that Terraform can guarantee to make the same selections by default when
you run "terraform init" in the future.

Terraform has been successfully initialized!

You may now begin working with Terraform. Try running "terraform plan" to see
any changes that are required for your infrastructure. All Terraform commands
should now work.

If you ever set or change modules or backend configuration for Terraform,
rerun this command to reinitialize your working directory. If you forget, other
commands will detect it and remind you to do so if necessary.
```

- In the same folder you were before run terraform apply

```bash
terraform apply
```

Sample command output

```bash
An execution plan has been generated and is shown below.
Resource actions are indicated with the following symbols:
  + create

Terraform will perform the following actions:

  # aws_dynamodb_table.dynamodb-table-1 will be created
  + resource "aws_dynamodb_table" "dynamodb-table-1" {
      + arn              = (known after apply)
      + billing_mode     = "PROVISIONED"
      + hash_key         = "UserId"
      + id               = (known after apply)
      + name             = "UserTable"
      + range_key        = "UserTitle"
      + read_capacity    = 10
      + stream_arn       = (known after apply)
      + stream_label     = (known after apply)
      + stream_view_type = (known after apply)
      + tags             = {
          + "Name" = "dynamodb-table-user"
        }
      + tags_all         = {
          + "Name" = "dynamodb-table-user"
        }
      + write_capacity   = 10

      + attribute {
          + name = "UserId"
          + type = "S"
        }
      + attribute {
          + name = "UserTitle"
          + type = "S"
        }

      + point_in_time_recovery {
          + enabled = (known after apply)
        }

      + server_side_encryption {
          + enabled     = (known after apply)
          + kms_key_arn = (known after apply)
        }
    }

  # aws_dynamodb_table.dynamodb-table-2 will be created
  + resource "aws_dynamodb_table" "dynamodb-table-2" {
      + arn              = (known after apply)
      + billing_mode     = "PROVISIONED"
      + hash_key         = "UserId"
      + id               = (known after apply)
      + name             = "UserTable"
      + range_key        = "UserTitle"
      + read_capacity    = 10
      + stream_arn       = (known after apply)
      + stream_label     = (known after apply)
      + stream_view_type = (known after apply)
      + tags             = {
          + "Name" = "dynamodb-table-user"
        }
      + tags_all         = {
          + "Name" = "dynamodb-table-user"
        }
      + write_capacity   = 10

      + attribute {
          + name = "UserId"
          + type = "S"
        }
      + attribute {
          + name = "UserTitle"
          + type = "S"
        }

      + point_in_time_recovery {
          + enabled = (known after apply)
        }

      + server_side_encryption {
          + enabled     = (known after apply)
          + kms_key_arn = (known after apply)
        }
    }

Plan: 2 to add, 0 to change, 0 to destroy.

Do you want to perform these actions?
  Terraform will perform the actions described above.
  Only 'yes' will be accepted to approve.

  Enter a value: yes

aws_dynamodb_table.dynamodb-table-1: Creating...
aws_dynamodb_table.dynamodb-table-2: Creating...
aws_dynamodb_table.dynamodb-table-1: Creation complete after 8s [id=UserTable]
aws_dynamodb_table.dynamodb-table-2: Creation complete after 9s [id=UserTable]

Apply complete! Resources: 2 added, 0 changed, 0 destroyed.
```

