# Terraform Cloud

## Terraform Cloud

Terraform Cloud is an application that helps teams use Terraform together,it helps you collaborate on infrastructure. It manages Terraform runs in a consistent and reliable environment, and includes easy access to shared state and secret data, access controls for approving changes to infrastructure, a private registry for sharing Terraform modules, detailed policy controls for governing the contents of Terraform configurations, and more.

Terraform Cloud is available as a hosted service at [https://app.terraform.io](https://app.terraform.io). We offer free accounts for small teams, and paid plans with additional feature sets for medium-sized businesses.

Large enterprises can purchase Terraform Enterprise, our self-hosted distribution of Terraform Cloud. It offers enterprises a private instance of the Terraform Cloud application, with no resource limits and with additional enterprise-grade architectural features like audit logging and SAML single sign-on.

![](.gitbook/assets/terraform_cloud_workflow.png)

### About Product Names

Before mid-2019, all distributions of Terraform Cloud used to be called Terraform Enterprise; the self-hosted distribution was called Private Terraform Enterprise \(PTFE\). These previous names sometimes still appear in supporting tools \(like [the `tfe` Terraform provider](https://registry.terraform.io/providers/hashicorp/tfe/latest), which is also intended for use with Terraform Cloud\).

### Get Started With Terraform Cloud

#### Sign up for Terraform Cloud

In this guide, you will learn about how Terraform Cloud enables collaboration. Then, you will sign up for a Terraform Cloud account and create an organization.

Over the course of this track, you will learn Terraform Cloud's core workflows and UI by deploying and managing an AWS DynamoDB instance.

#### **Prerequisites**

While Terraform can provision resources on many different providers and connect with several popular version control systems \(VCSs\), this guide requires:

* an AWS account
* a GitHub account

#### **The workflow**

Terraform Cloud offers a team-oriented remote Terraform workflow.

Users are individual members of a Terraform Cloud [organization](https://www.terraform.io/docs/cloud/users-teams-organizations/organizations.html). As a user, you manage, plan and apply collections of infrastructure in [workspaces](https://www.terraform.io/docs/cloud/workspaces/index.html). These workspaces contain Terraform configuration files, environment variables, Terraform variables, and state files — everything Terraform needs to manage a given collection of infrastructure.

A common workflow is:

1. **Author** - Create or update the configuration file in HCL based on the scoped parameters
2. **Select workspace** - Create or select a workspace for your resources
3. **Version Control** - Check your configuration files into a version control system \(VCS\) as a central source of truth where your changes can be managed
4. **Configure Variables** - Define your workspace's [Terraform variables](https://www.terraform.io/docs/configuration/variables.html) and environment variables
5. **Plan & Apply** - Execute Terraform Cloud runs \(plans and applies\) to manage your infrastructure

Since Terraform Cloud supports multiple users, you can collaborate with your team on each of these steps. For instance, each time you plan a new change, your team can see and approve the plan before it is applied.

### Create your account

Create a Terraform Cloud account at [https://app.terraform.io/signup/account](https://app.terraform.io/signup/account).

![](.gitbook/assets/sign-up.png)

When you sign up, you'll also receive an email asking you to confirm your email address. Confirm your email address before moving on.

For more information about account creation, refer to the [Terraform Documentation: Creating an account](https://www.terraform.io/docs/cloud/users-teams-organizations/users.html#creating-an-account).

For information about accessing Terraform Cloud with the CLI or API, refer to the [Terraform Cloud API Documentation](https://www.terraform.io/docs/cloud/api/index.html).

### Create your organization

Terraform Cloud will prompt you to create a new organization after you sign in for the first time.

Enter an organization name and email address. You can use the same email address that you used for your account.

**Note:** If you want to join an existing organization, give the organization's administrator the email address you used to create an account. They will be able to send you an invite.

