# Configure a Workspace and Create Infrastructure

In this guide, you will learn how to retrieve your AWS credentials and set your Terraform Cloud variables to use those values. From there, you will queue and apply your configuration to provision a DynamoDB.

### Configure AWS

The example repository uses the Amazon Web Services \(AWS\) provider. In order to use it, you will need an AWS account. If you don't have an AWS account already, [create one now](https://aws.amazon.com/).

This example is intended to only create resources which qualify under the AWS [free tier](https://aws.amazon.com/free/).

**Warning!** If you're not using an account that qualifies under the AWS [free tier](https://aws.amazon.com/free/), you may be charged to run these examples. The most you should be charged should only be a few dollars, but we're not responsible for any charges that may incur.

Once you have an AWS account, you'll need user credentials so that Terraform can use your AWS account to apply the example configuration.

You can [follow the AWS documentation](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_users_create.html#id_users_create_console) to create a user with **Programmatic access** and **Administrator** permissions, either through membership in an IAM Group with the `AdministratorAccess` policy, or by attaching the `AdministratorAccess` policy directly.

**Warning!** While Terraform Cloud stores your credentials and other variables securely, we recommend disabling or deleting the user you create for this guide after you are done. Always follow security best practices when managing credentials.

When you create the user, you will receive an **Access key ID** and a **Secret access key**. Be sure to keep these values in a secure location; you will use them in the next step.

### Configure workspace variables

Now that you have your AWS **Access key ID** and **Secret access key**, return to the Terraform Cloud UI. Within your new workspace, visit the "Variables" page.

Terraform Cloud supports both **Terraform Variables** and **Environment Variables**. We'll use both types in this guide.

Scroll down to the "Environment Variables" section, and create two variables.

1. [`AWS_ACCESS_KEY_ID`](https://learn.hashicorp.com/terraform/cloud-getting-started/setup-workspace#aws_access_key_id) with the **Access key ID** from the prior step
2. [`AWS_SECRET_ACCESS_KEY`](https://learn.hashicorp.com/terraform/cloud-getting-started/setup-workspace#aws_secret_access_key) with the **Secret access key**

Check the "Sensitive" checkbox for both of these variables and click the "Save variable" button to save each one. Once you are done, the "Environment Variables" section should look like this.

![Environment Variables](https://learn.hashicorp.com/img/terraform/cloud/environment-variables.png)

Just like when running Terraform on your local machine, Terraform Cloud will load these environment variables when planning and applying changes to your configuration.

**Note:** If you have been using the Terraform CLI, be aware that your local environment variables do not carry over to Terraform Cloud. This step configures Terraform Cloud to run AWS actions on your behalf by providing your credentials.

We also included two **Terraform Variables** in the example configuration. Scroll up to the "Terraform Variables" section to set those up now.

1. [`tag_user_name`](https://learn.hashicorp.com/terraform/cloud-getting-started/setup-workspace#tag_user_name) with your name
2. [`db_write_capacity`](https://learn.hashicorp.com/terraform/cloud-getting-started/setup-workspace#db_write_capacity) with the number `1`
3. [`db_read_capacity`](https://learn.hashicorp.com/terraform/cloud-getting-started/setup-workspace#db_read_capacity) with the number `2`

When you are done, the "Terraform Variables" section should look like this.

![Terraform Variables](https://learn.hashicorp.com/img/terraform/cloud/terraform-variables.png)

### Queue and apply plan

Now that your workspace is configured, use the "Queue Plan" button to start a plan. You may give a reason in the provided text box. Terraform Cloud will run a **plan** step, which creates a list of the requested changes. This may take a few minutes.

![Queue Plan](https://learn.hashicorp.com/img/terraform/cloud/queue-plan.png)

#### Apply Plan

Once the plan is complete, you need to confirm it before you can apply it.

Click the "Confirm & Apply" button to continue. You can include a comment if you like.

After a few minutes, your plan should be applied successfully and you can see the results in Terraform Cloud.

![Terraform Apply](https://learn.hashicorp.com/img/terraform/cloud/apply-finished.png)

The provided example configuration provisions an AWS DynamoDB table. You can optionally visit the [AWS web console](https://console.aws.amazon.com/) to verify that Terraform provisioned the table. The configuration defaults to using the **N. California/us-west-1** region, so be sure to look for the DynamoDB table in that region.

There have been several steps involved in getting to this point, so it is possible that an error occurred due to a missed step, a typo, or another problem. If an error does occur during the `plan` or `apply` step, Terraform Cloud will display the error message on the "Run" page to help you troubleshoot the problem.

**Note** The DynamoDB table that you have provisioned will remain active until it is deleted. You will do this in the [clean-up](https://learn.hashicorp.com/terraform/cloud-gettingstarted/tfc_cleanup) section of this track.

