# 🚀 Lab 1: Setup and configure

> [!IMPORTANT]
> This workshop is still work in progress for the time being.

## Lab 1 - Tasks

In this lab, you will go though the following tasks:

- Creating a new browser profile
- Logging into the account you are going to use during the workshop
- Creating a GitHub account (optional)
- Fork a GitHub repository
- Creating a GitHub Codespace
- Connecting to the Power Platform using the Power Platform Command-Line Interface (CLI)
- Creating developer environments
- Switch between environments with the Power Platform CLI
- Enabling Dataverse settings

## Task 1: Create a new browser profile (Microsoft Edge)

It's always good to have a separate browser profile for your work and for workshops like this. This way you can keep all of your credentials separate and not have to worry about logging out of your personal / work accounts.

1. Open Microsoft Edge
1. Click on the profile icon on the top left corner
1. Hover over "Other Microsoft Edge Browsers" / "Other profiles" and then select **Add Browser** / **Add profile**

    ![Add new browser profile](assets/add-new-browser-profile.png)

1. Click **Add**

    ![Add a profile dialog](assets/add-profile.png)

    This will then open up a new browser window on your taskbar.

1. Pin that browser window to your taskbar
1. In the new browser window, select **Start without your data**

    ![Start without your data](assets/start-without-your-data.png)

1. Then select **Confirm and start browsing**.

    ![Confirm and start browsing](assets/confirm-and-start-browsing.png)

    It may prompt you to configure your new browser theme. If this happens, just select **Next** and then **Finish**.

## Task 2: Log on to your account

With the credentials that were provided to you, let's log into the account you are going to use during the workshop.

1. Go to [make.powerapps.com](https://make.powerapps.com)
1. On the sign-in screen, enter the email address that was provided to you and then click **Next**

    ![Sign in screen](assets/pa-sign-in-email.png)

1. Then enter the password and click **Sign in**
    ![Sign in screen](assets/pa-sign-in-password.png)

1. If you're prompted to stay signed in, click **Yes**

    You should now be logged in and on the Power Apps Home Page.

    ![Power apps home page](assets/power-apps-home-page.png)

## Task 3: Create a GitHub account

For this workshop, we are going to be using GitHub. If you already have a GitHub account, you can skip this task.

1. Go to the [GitHub](https://github.com) website
2. Click on **Sign up** on the top right corner
3. Enter your email address (Use your personal email address) and then click **Continue**
4. Create a password and then click **Continue**
5. Enter a username and then click **Continue**
6. Select whether you want to receive product updates or not and then click **Continue**
7. Solve the puzzle to verify your account and then click **Create account**
8. Enter the code that was sent to your email address and then when you've navigated to the welcome screen, click **Skip personalization**

You now have a GitHub account. Welcome to the community!

## Task 4: Create a fork of the repository for this workshop

Now that you have a GitHub account, we are going to create a fork of the repository for this workshop. A fork is a copy of an existing repository. Forking a repository allows you to freely experiment with changes without affecting the original project.

1. Go to the [MPPC23-Power-Apps](https://aka.ms/MPPC23-Power-Apps) GitHub repository
2. Click on the **Fork** button on the top right corner

    ![Screenshot of fork button in GitHub Repository](assets/fork-button.png)

3. Once the "Create a new fork" page opens, review the information and then click **Create Fork**

    ![Screenshot of "Create fork" button in GitHub](assets/create-fork-button.png)

    Once your have created the fork, you will be redirected to your forked repository. You can see that you are in your forked repository by looking at the top left corner of the page. It should say **your-username/MPPC23-Power-Apps forked from microsoft/MPPC23-Power-Apps**.

## Task 5: Create a codespace

A codespace is a cloud-hosted development environment you can access from anywhere. It has everything you need, including a text editor, terminal, and debugger. Codespaces are powered by Visual Studio Code and run in a containerized environment. For this workshop, we are going to use codespaces to do our development.

1. Make sure that you are in your forked repository (_your-username/MPPC23-Power-Apps_) and then find and click on the **<> Code** button

    ![TODO: Add image of code button](assets/repo-code-button.png)

2. On the **Code** pop up, select the **Codespaces** tab
3. Click **Create codespace on main**

    A codespace will now be created for you in a new tab. This will take a few seconds. But once it's done, you will have a fully functional Visual Studio Code environment in your browser. You can now start developing!

## Task 6: Connect to the Power Platform using the Power Platform Command-Line Interface (CLI)

1. In your codespace, click on the **Power Platform** icon in the left navigation

    ![Power Platform icon in the left navigation](assets/power-platform-icon.png)

    You'll more than likely see that there is "No auth profiles found on this computer". Let's create one.

    ![Screenshot of no auth profiles found](assets/no-auth-profiles-found.png)

1. If you don't see it open already, let's open the Terminal. Click on the Burger menu icon in the top left corner and then hover over **Terminal** and then click **New Terminal**

    ![Screenshot of new terminal menu](assets/new-terminal.png)

    A terminal window has now been opened for you. This is where you will write all of the following commands in this lab and in the upcoming labs as well.

1. Type the following command in the terminal and then press **Enter**:

    ```bash
    pac auth create --deviceCode
    ```

1. You will be prompted to use a web browser to authenticate. Copy (**ctrl + c**) the ```code``` that is provided in the terminal and then **Ctrl + click** on the ```link``` that is provided in the terminal.

    ![Screenshot of the terminal with the code and link](assets/terminal-with-code-and-link.png)

    Once you click on that link, it will open a new browser tab where you will have to paste that code into the browser and then click **Next**

    > **Note:** If you are using a Mac, you can **Ctrl + click** on the ```link``` that is provided in the terminal and then enter the ``code`` provided.

    ![Enter code and click next](assets/enter-code.png)

1. Pick the account that was provided to you. If you can't see it on screen then log in.

    ![Screenshot of the account selection page](assets/account-selection.png)

1. Then type in your password and click **Sign in**

    You will then see a page asking if you're trying to sign in to Power Platform CLI - pac.

    ![Screenshot of the Are you trying to sign in to Power Platform CLI - pac? page](assets/sign-into-pac-cli.png)

1. Click **Continue**

    You'll then see a prompt confirming that you have successfully signed in to Power Platform CLI - pac. Close the browser tab and return to your codespace.

1. Refresh the Auth Profiles section by clicking on the **Refresh** button next to "Auth Profiles"

    ![Screenshot of the Auth Profiles section with the Refresh button](assets/refresh-auth-profiles.png)

    You should now see at least one auth profile. If you have more than one, you can select the one you want to use by clicking on the **Select Auth Profile** button next to the auth profile.

    ![Select Auth Profile](assets/select-auth-profile.png)

## Task 7: Create developer environments

Developer environments are very helpful when you want to try out features, they are meant to be short living environments.

For this workshop, we are going to create three different developer environments:

- ```Dev```: The environment where we are going to create our app and solution later on.
- ```QA```: The environment where we are going to deploy our solution to in a later lab.
- ```Prod```: The environment where we are going to deploy our solution to in a later lab.

To create developer environments, you can create them in multiple ways:

1. By subscribing to the Power Apps Developer Plan
1. Via the Power Platform Admin Center (PPAC)
1. Via the Power Platform CLI

> [!IMPORTANT]
> When subscribing to the developer plan, you will automatically assign a developer license to yourself. When creating a developer environment through PPAC or the CLI, you will not do that. That's why we do this step first, so that you won't have to start a trial.

In this workshop, we will create one environment through the UI, one via PPAC, and the last one via the CLI, so that you know all about how to create developer environments.

### Create the 'Dev` environment by subscribing to the developer plan

Currently, if you want to get all that the Power Platform offers, it's required to subscribe to the Power Apps Developer Plan. In this part, we will walk you through all the steps:

1. Go to the [Power Apps Developer Plan](https://aka.ms/pp/devplan) website (use the Edge profile you created for this workshop)
1. Select the **Existing user? Add a dev environment** button

    ![Power Apps Developer Plan website with 'Get Started Free' and 'Existing user? Add a dev environment' buttons](./assets/dev-plan-1.png)

1. Select the **Sign up for a Community Plan** link

    ![Sign up page for Power Apps Developer Plan with options to request a license, buy a license or sign up for a community plan](./assets/dev-plan-2.png)

1. Leave the country on United States and select the **Accept** button.

    ![Page where you can select a country and accept or cancel. There are also links to the terms of use and the Microsoft privacy statement](./assets/dev-plan-3.png)

1. After selecting **Accept**, a Power Platform developer environment will be created for you with the name `{User}'s Environment` and you will be redirected to the maker portal. In here, you will see two things:
    1. An alert in the top-center that says 'This is a developer environment and not meant for production use'
    1. The environment picker at the top-right with your recently created environment `{User}'s Environment` selected

    ![The maker portal, with at the top-center the alert that this is a developer environment and not meant for production use. At to top-right, you will see the name of your developer environment that just got created](./assets/dev-plan-4.png)

Now, let's rename the environment to something that makes sense to us.

1. Go to the [Power Platform Admin Center](https://aka.ms/ppac)
1. Exit the Welcome / Tour pop up. You can do this by clicking on the **X** in the top right corner of the pop up screen

    ![Exit the Welcome / Tour pop up](assets/exit-welcome-tour.png)

1. Select **Environments** in the left navigation
1. Select `{User}'s Environment` by clicking on the name
1. In the details card, select **edit**

    ![](./assets/environment-edit.png)

1. In the side panel, make sure to change the **Name** to `Dev` and select the **Save** button.

    ![](./assets/environment-edit-save.png)

    This will trigger a name change, and will lead you to the following screen.

    ![](./assets/environment-edit-save-operation.png)

1. Select **Environments** to make get back to the overview of the environments.

### Create the `QA` environment via the Power Platform Admin Center (PPAC)

We are going to create a QA environment through the Power Platform Admin Center.

1. Select **New** in the top navigation

    ![Environment + New for adding environments](assets/new-environment-button.png)

1. When the right-hand side dialog pops up - enter the following information:

    | Field | Value |
    | --- | --- |
    | Name | QA |
    | Region | US - Default |
    | Type | Developer |
    | Purpose | Developer environment for MPPC23 |

    ![Create new Developer Environment](assets/create-qa-env.png)

1. Select **Next**
1. The next section is asking you to add Dataverse. Finally select on **Save**

### Create the `Prod` environment via the Power Platform Command-Line Interface (CLI)

We will create the last environment we are going to create via the Power Platform CLI. Because we don't have to go through the UI, and we don't have to load anything, this will go way faster than the other options.

We will create the last environment with the following values:

| Field | Value |
| --- | --- |
| Name | Prod |
| Region | US - Default |
| Type | Developer |

The command we need to use for creating an environment is `pac admin create`. The documentation of this command can be found [here](https://aka.ms/pac/admin/#pac-admin-create).

Run the following command in the terminal in your codespace:

```bash
pac admin create --name "Prod" --type "Developer"
```

> [!NOTE]
> We don't use `purpose` here, because the Power Platform CLI doesn't have a parameter for this. Also, we are using the defaults for `region` and `currency`, so we don't have to add those to the command.

Once you have created all three environments, you should see them in the list of environments. Click the **Refresh** button on the top navigation if you don't see them yet.

![List of developer environments](assets/list-of-environments.png)

## Task 8: Switch between environments with the Power Platform CLI

1. With the correct Auth Profile, in the terminal type the following command and then press **Enter**:

    ```bash
    pac org list
    ```

    This gets a list of all the environments that you have access to. You should see the **Dev** environment listed as one of them. This is the one we want to eventually connect to.

    ![Screenshot of pac org list](assets/org-list.png)

1. Take note of the Environment ID of the **Dev** Environment and copy it.

    ![Copy of Dev environment ID](assets/org-list-with-env-id.png)

1. Then in the terminal, type the following command and then press **Enter**. Make sure to replace ```00000000-0000-0000-0000-000000000000``` with the environment id that you copied above

    ```bash
    pac org select --environment 00000000-0000-0000-0000-000000000000
    ```

    You should then see confirmation that you have successfully selected the **Dev** org for the current auth profile.

    ![Screenshot of pac org select confirmation](assets/org-select.png)

1. To have further confirmation that you have successfully connected to the **Dev** environment, in the terminal type the following command and then press **Enter**:

    ```bash
    pac org who
    ```

    This command will return information about the environment that you are connected to. You should see the **Dev** environment listed as well as other unique information about the environment including the User email you're connected as.

    ![Screenshot of pac org who confirmation information](assets/org-confirmation.png)

## Task 9: Enable Dataverse settings

A recent addition to the Power Platform CLI is the ability to list and update Dataverse settings. This means that you can change the settings that are normally only available through the UI. In this task, you will learn how to change the settings.

### List Dataverse settings

1. Run the following command and then press **Enter**:

    ```bash
    pac org list-settings
    ```

    This command will return all the settings in the org we are connected to now (the `Dev`` environment). As you can see, this is a very large list. You can filter them though.

1. Add the `--filter` parameter and filter for all settings that contain `audit` with the following command:

    ```bash
    pac org list-settings --filter audit
    ```

    This command will return all the settings that contain `audit` in the org we are connected to now (the `Dev` environment). As you can see, this is a way smaller list than what we saw before.

    ![Screenshot of pac org list-settings --filter audit which shows 6 results](./assets/list-settings-filter-audit.png)

### Update Dataverse settings

Let's try out how updating a setting works. In the list of audit settings we just saw, there is a `isauditenabled` setting which is set to **No**.

![Screenshot of pac org list-settings --filter audit which shows 6 results - a red rectangle is placed on the is audit enabled setting. The value is set to no.](./assets/list-settings-filter-audit-enabled.png)

1. Run the following command and then select **Enter**:

    ```bash
    pac org update-settings --name isauditenabled --value true
    ```

    This command will set the `isauditenabled` setting to true. Note that the list command showed `No` as the output, but for updating you need to use true or false.

1. Run the following command again to verify if the setting is applied and select **Enter**:

    ```bash
    pac org list-settings --filter audit
    ```

    This command will return all the settings that contain `audit` in the org we are connected to now (the `Dev` environment). As you can see, the `isauditenabled` setting is now set to `No`.

    ![Screenshot of pac org list-settings --filter audit which shows 6 results - a red rectangle is placed on the is audit enabled setting. The value is set to yes.](./assets/list-settings-filter-audit-enabled-yes.png)

## Next lab

This is the end of lab 1, select the link below to move to the next lab.

[⏭️ Move to lab 2](../lab2/README.md)
