main_section: Reference
sub_section: Integrations
page_title: GitHub integration

# GitHub integration

GitHub integration is enabled for your Shippable account in one of 2 ways:

* You sign in to Shippable with your GitHub credentials. In this case, we automatically set up an Account Integration for you. You can see this integration by going to your Account Settings (gear menu in top navbar) and clicking on `Integrations` in the sidebar menu.

* You sign in to Shippable with another supported source control provider, and add a GitHub integrations through Account Settings -> Integrations. To learn how to do this, read the [Adding a GitHub integration section](#addGithub).

## Signing in with Github

To build repositories hosted on GitHub. you will need to authorize Shippable to access your repositories.

To enable public repositories:

- Log in to [Shippable](https://app.shippable.com) using your GitHub credentials.
- Click on `Authorize application` button to authorize Shippable to access your public
  repositories on GitHub (This is a one-time step). Provide your GitHub password, if prompted.
- Your account is ready to use after this step.
- You can click on the top left menu icon to see a list of your Subscriptions. Choose the subscription you want.
- In the 'CI' tab, click the 'Enable Project' section to view all your public and private repositories. Proceed to enabling a project.
- If you don't see your projects in the above step, click on the Account settings (gear icon on the top navigation bar). In the 'Accounts' section click the `Sync` button.

To enable private repositories:

- Go to your **Account Settings** by clicking on the gear icon on the right of the top navbar.
- In the **Git identities** section, authorize Shippable for private repositories.

## Adding your GitHub integration

-  Go to your **Account Settings** by clicking on the gear icon in the top navigation bar.

<img src="../../images/reference/integrations/account-settings.png" alt="Add GitHub credentials">

-  Click on **Integrations** in the left sidebar menu and then click on **Add integration**
-  Locate **GitHub** in the list and click on **Create Integration**
-  Name your integration and enter your github api token.
-  Click **Save**

<img src="../../images/reference/integrations/github-integration.png" alt="Add GitHub credentials">

## Set up CI for your repositories

Skip this section if you signed into Shippable with GitHub credentials or if you don't want to use your integration to enable repositories for CI.

* In your Account Settings, click on `Sync`.
* Go to your Home dashboard. Click on the Subscription dropdown on the top left of your screen.
* You should see your Organizations from GitHub in your list of subscriptions.
* Click on any GitHub organization and you should be able to enable projects for CI.

## Use your integration in your Pipeline configuration

* Go to your Subscription's Settings tab. This should be the Subscription where you want to set up your pipelines.
* Click on **Integrations** in the sidebar menu.
* Click on **Add Integration**.
* Name your GitHub integration with a friendly name. This can be the same name as the one in your account integration.
* From the dropdown, choose the account integration you just created in the step above.
* Click on **Save**.

The integration is now added to your subscription. You can now use this account integration while configuring your Pipeline workflows. In your configurations, **you should use the friendly name for the integration from Subscription Settings**.

For example, if the integration is called `github-foo` in your subscription settings, you can use it in `shippable.resources.yml` as follows:

```
- name: github-repository                      #required
  type: gitRepo                             	#required
  integration: github-foo                     	#this is your github integration name
  pointer:
    sourceName: org/repo                  		#required
    branch: master                          	#optional
```

##Editing your GitHub integration

You can go to your **Account Settings** at any time, click on **Integrations** in the left sidebar menu, and click the **Edit** button for your GitHub integration. You can then change integration name and your github api token.

However, you cannot edit the list of Subscriptions that are allowed to use the integration from this page. To add your integration to additional Subscriptions, read our [Adding your integration to additional Subscriptions section](integrations-overview/#add-subscriptions)

##Deleting your GitHub integration

If you no longer need the integration, you can delete it by following the steps below.

-  Go to your **Account Settings** by clicking on the gear icon in the top navigation bar.

<img src="../../images/reference/integrations/account-settings.png" alt="Account settings">

-  Click on **Integrations** in the left sidebar menu and then click on **Add integration**
- Locate the integration you want to delete and click on the **Delete** button.
- If there are no Subscriptions using this integration, you will be able to delete it by clicking on **Yes**. You are done at this point.

<img src="../../images/reference/integrations/confirm-delete-integration.png" alt="Delete integration confirmation screen">

- If your integration is being used by any Subscriptions, you will see a message telling you which Subscriptions are still using the integration.

<img src="../../images/reference/integrations/cannot-delete-integration.png" alt="Cannot delete integration because of dependencies">

- Go to each Subscription listed in the dependencies and delete it from each.
    - From the Subsciption dropdown menu at the top left of your Dashboard, click on the dependent Subscription.

    <img src="../../images/reference/integrations/list-subscriptions.png" alt="List subscriptions">

    - Go to the **Settings** tab and click on **Integrations** in the left sidebar.
    - Delete the integration.
- Once you have delete the integration from all Subscriptions, you can go back to **Account Settings** and delete the integration.