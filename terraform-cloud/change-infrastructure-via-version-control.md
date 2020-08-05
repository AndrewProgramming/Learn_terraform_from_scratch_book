# Change Infrastructure via Version Control

There are two ways to update your workspace deployments on Terraform Cloud — changing the configuration in VCS or updating variables in the Terraform Cloud UI.

This guide will walk you through the Terraform Cloud UI and both approaches.

### Explore your workspace

Within the Terraform Cloud UI, you will notice several menus and options for your workspace, including "Runs", "States", "Variables", "Settings", and the "Queue plan" interface you used to apply the example configuration.

![Workspace Actions](https://learn.hashicorp.com/img/terraform/cloud/workspace-actions.png)

* **Runs** shows a list of all of the plan and apply actions you have taken with this workspace.
* **States** shows a list of the entire _tfstate_ file of your workspace after each successful run.
* **Variables** will let you configure Terraform variables and environment variables.
* **Settings** contains all of the other configuration for your workspace.
* **Queue plan** will let you start a new plan.

Since there haven't been any changes since the last successful run, you can safely queue a new plan, and you will see that there were no changes to apply.

### Changing variables

One way to update the infrastructure managed by a workspace is by changing your Terraform Cloud variables.

In the Terraform Cloud interface, return to the "Variables" section of your workspace.

First, change the value of `db_read_capacity` from `2` to `1` and click the purple "Save variable" button. Then, use the "Queue plan" interface to begin another run. After the plan completes, the plan log should indicate that there are "0 to add, 1 to change, 0 to destroy".

![Plan Finished](https://learn.hashicorp.com/img/terraform/cloud/plan-finished.png)

In this case, Terraform can make the change to the DynamoDB table without destroying and recreating it. Click the "Confirm & Apply" button, followed by the "Apply Change" button to apply the change.

### Changing configuration

In other cases, you might need to update infrastructure by directly changing your configuration files. Below, you will update your configuration by using a GitHub **Pull Request** \(PR\).

The repository you forked already includes a branch named `add-username` with changes that you can use to create a pull request. In a normal workflow, you would make the edits in your code, test them locally using the Terraform CLI, push them to a branch, and make a pull request from changes you had personally written.

First, you'll need to visit your fork of the `tfc-guide-example` project in GitHub. From there, click "New pull request" button to create a pull request. Set the **base** branch to the `master` branch of _your fork_, and the **compare** branch to the `add-username` branch.

![Pull Request](https://learn.hashicorp.com/img/terraform/cloud/pull-request.png)

Once you have created the pull request, Terraform Cloud will trigger a **speculative plan**.

Speculative plans are

* **plan-only runs** - they show a set of possible changes that cannot be applied
* **temporary** - they won't appear in any log within Terraform Cloud
* **individual** - they can only be accessed from a direct link on GitHub PR
* **non-destructive** - no action is taken, no infrastructure is provisioned

You can view this plan by clicking on the "Details" link in the "Checks" portion of your pull request.

![View Speculative Plan](https://learn.hashicorp.com/img/terraform/cloud/gh-speculative-plan.png)

You will see that a new run was created, so you can review the plan before merging the pull request. This is another way that teams can collaborate on changes to their Terraform configuration before they are implemented.

Since speculative plans cannot be applied, you will need to merge the pull request before applying this change.

![TFC Speculative Plan](https://learn.hashicorp.com/img/terraform/cloud/tfc-speculative-plan.png)

Return to the GitHub UI, and merge the pull request with the "Merge pull request" button.

Switch back to the "Runs" tab for your workspace in Terraform Cloud. You will see that Terraform Cloud picked up the change to your configuration and has started a new run.

![Run Triggered by Pull Request](https://learn.hashicorp.com/img/terraform/cloud/trigger-run.png)

Click on the new run in the Terraform Cloud UI, and you'll see the run details. Just as before, you can "Confirm & Apply" the run.

