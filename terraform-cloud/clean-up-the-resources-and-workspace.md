# Clean Up the Resources and Workspace

In this guide, you will destroy the DynamoDB table and delete your Terraform Cloud workspace.

### Destroy infrastructure

You have already seen how to perform the basic Terraform actions of provisioning and changing infrastructure with Terraform Cloud. The last part of your infrastructure's lifecycle will be to destroy it. Terraform Cloud allows you to destroy the infrastructure you have provisioned with it as a part of the standard workflow.

To destroy the infrastructure you provisioned in this track, go to your workspace in the Terraform Cloud UI. Next, from the top menu, select "Settings -&gt; Destruction and Deletion".

![Destruction and Deletion](https://learn.hashicorp.com/img/terraform/cloud/destruction-and-deletion.png)

This page gives two different options:

* **Queue destroy plan** performs a destroy plan action to destroy any infrastructure created by prior Terraform Cloud runs.
* **Delete from Terraform Cloud** deletes your workspace from Terraform Cloud.

**Important:** Deleting a workspace does not destroy infrastructure that has been provisioned by that workspace. For example, if you were to delete this workspace now, the AWS DynamoDB table you provisioned earlier would not be destroyed.

Notice that the "Queue a destroy plan" button is disabled. Because accidentally destroying infrastructure can be a costly mistake, Terraform Cloud makes it a three step process:

1. Check "Allow destroy plans" option
2. Queue a destroy plan
3. Apply the destroy plan

#### Check "Allow destroy plans" option

Check the "Allow destroy plans" option in the **Destroy Infrastructure** section. Remember to click on the "Save settings" button to save this setting.

![Check &quot;Allow destroy plans&quot;](https://learn.hashicorp.com/img/terraform/cloud/allow-destroy.png)

#### Queue a destroy plan

You should see that the "Queue destroy plan" button is enabled. Click it now -- a prompt should appear.

You will be asked to enter your workspace name before you can click "Queue destroy plan".

![Queue Destroy Plan](https://learn.hashicorp.com/img/terraform/cloud/queue-destroy-plan.png)

#### [»](https://learn.hashicorp.com/terraform/cloud-getting-started/clean-up#apply-the-destroy-plan)Apply the destroy plan

As before, you will be asked to confirm the plan before it's applied. Do so now to destroy your DynamoDB instance.

After a few minutes, the apply step should complete successfully.

Verify that the DynamoDB instance was deprovisioned by visiting the [AWS web console](https://console.aws.amazon.com/). The configuration defaults to using the **N. California/us-west-1** region.

![Verified Destroy Applied](https://learn.hashicorp.com/img/terraform/cloud/infra-destroyed.png)

### Delete or disable the AWS IAM user

This step is also optional.

Earlier in this track, you may have created an AWS IAM user for use with Terraform Cloud. You can delete or disable this user in the AWS console, by navigating to the Identity Access Management \(IAM\) section, and then to the user you created. Once you have found the user, you can use the AWS Console to delete the user, or disable the user's access keys.

### Delete the Terraform Cloud workspace

If you would like, you can delete the workspace you created earlier in this track. This is optional, since Terraform Cloud doesn't impose a limit on the number of workspaces you have.

To do so, return to the "Settings -&gt; Destruction & Deletion" page, and click the red "Delete from Terraform Cloud" button.

You will be asked to enter your workspace name before you can click "Delete workspace".

![Delete workspace](https://learn.hashicorp.com/img/terraform/cloud/delete-workspace.png)

