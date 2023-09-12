# 🚀 Lab 3: Deploy

> [!IMPORTANT]
> This workshop is still work in progress for the time being.

## Lab 3 - Tasks

In this lab, you will go though the following tasks:

- Create your first pipeline (Dev - QA - Prod)
- Run the first deployment to the Test environment
- Install the Creator Kit solution in QA environment
- Install the Creator Kit solution in Prod environment
- Retry the deployment to the QA environment
- Deploy to the Prod environment
- Use AI generated descriptions

## Task 1: Create your first pipeline

In this task, you will create your first pipeline. The `Deployment Pipeline Configuration` app that you installed in lab 1 will be used for that.

Go to the [maker portal](https://make.powerapps.com), and make sure you are in the `Prod` environment.

![](./assets/prod-env-pipelines-installed.png)

Select the **Deployment Pipeline Configuration** app and make sure to **play** it.

This will open the app in a new tab:

![](./assets/create-pipeline-app.png)

Make yourself familiar with the app, by looking around which menu items there are:

First, there is an `Overview` section, where you land when you open the app. This is the `Pipelines Dashboard`, which will show you the latest info about runs and pipelines that are active. When you open this for the first time, it's supposed to be empty, so don't worry!

There is also a `Pipeline Setup` section where you can view your environments and pipelines.

Last but not least, there is a `Deployments` section which enables you to view the run history and find solution artifacts.

### Create a new pipeline

Let's create a new pipeline, by selecting the **+ new button** on the `Pipelines Dashboard`.

![](./assets/create-pipeline-new-pipeline.png)

This will lead you to a form where you can enter details about your pipeline:

![](./assets/create-pipeline-new-pipeline-details.png)

1. Use `My first pipeline` as the name

1. Leave the rest as default and save the pipeline by selecting the **Save** button

Some components of the form only appear after the first save, so that's why we save the pipeline. After saving, scroll down and you will see the following content below the owner field:

![](./assets/create-pipeline-new-pipeline-saved.png)

As you can see there are two sections: **Linked Development Environments** & **Deployment Stages**.

**Linked Development Environments**

A pipeline can be available for multiple development environments. This is very convenient when you want to use multiple development environments and use shared test and shared production environments.

In this lab, we will only add one development environment to the Linked Development Environments, but when you use this at your company later on, remember that it can be more than one environment here.

**Deployment Stages**

The Deployment Stages section will give you the option to add stages after your development environment. So for instance, in our lab today, we are going to add a stage called `Deploy to QA` and another stage called `Deploy to Prod`. The cool thing is that we can set previous stages for these stages. This gives us the ability to make sure `Deploy to QA` goes first, and `Deploy to Prod` comes second.

### Create a development environment

Let's continue our lab and start by adding a new development environment by selecting the New Development Environment button in the Linked Development Environments section.

![](./assets/create-pipeline-new-development-env-create.png)

A sidebar will be opened, where you can enter the details of the `Dev` environment you created in lab 01.

![](./assets/create-pipeline-new-development-env-details.png)

1. Add `Dev` as the Name

1. Set the Environment Type to `Development Environment`

1. For the next step, make sure to grab the `Environment Id` from the Power Platform Admin Center

    - Open a new tab and go to the [Power Platform Admin Center](https://aka.ms/ppac)
    - Select **Environments** in the menu on the left
    - Select the environment named **Dev**

      ![](./assets/create-pipeline-new-development-env-ppac-dev.png)

    - Copy the environment ID from there and paste it in the `Deployment Pipeline Configuration` app.

1. Select the **Save and Close** button on the bottom of your sidebar

If all went well, you'll see the following screen (*Refresh* the page if you don't see it):

![](./assets/create-pipeline-new-development-env-saved.png)

Make sure to select the **+ New Deployment Stage** button now to add the first deployment stage.

![](./assets/create-pipeline-new-deployment-stage.png)

### Add the first deployment stage

This will open a new sidebar, where you can enter details about your first deployment stage.

1. Add `Deploy to QA` as the Name

1. We're leaving the Description and Previous Deployment stage empty, because we don't have a previous deployment stage, since this is our first stage

1. Set focus to the input box next to target deployment environment. This will open up a small popup which enables you to add a new deployment environment

1. Select **+ New Deployment Environment**

![](./assets/create-pipeline-new-deployment-stage-details.png)

This will open another sidebar where you can add details about your QA environment.

#### Add the QA environment

In the sidebar, make sure to add the following details:

1. Add `QA` as the `Name`

1. Add `Target Environment` as the `Environment Type`

1. Add the environment ID of the test environment

    - Open a new tab and go to the [Power Platform Admin Center](https://aka.ms/ppac)
    - Select **Environments** in the menu on the left
    - Select the environment named **QA**

      ![](./assets/create-pipeline-new-development-env-ppac-qa.png)

    - Copy the environment ID from there and paste it in the `Deployment Pipeline Configuration` app.

1. Select the **Save and Close** button on the bottom of your sidebar

1. Select **Save and Close** again to save the deployment stage as well

Make sure to select the **+ New Deployment Stage** button again to add a second deployment stage: `Deploy to prod`.

### Add the `Deploy to prod` deployment stage

1. Add `Deploy to prod` as the `Name`

1. Leave the `Description` empty

1. Focus on the `Previous Deployment Stage` and search for the `Deploy to QA` stage. After you have found that stage, select it

1. Set focus to the input box next to target deployment environment. This will open up a small popup which enables you to add a new deployment environment

1. Select **+ New deployment Environment**

> **Note:**  
> There is a setting field called `Pre Deployment Step Required`. We're not using that in this case, but think about what could that be used for. During the workshop, the trainers will show an example of it.

![](./assets/create-pipeline-deploy-to-prod.png)

#### Add the Prod environment

1. Add `Prod` as the Name

1. Set the Environment Type to `Target Environment`

1. For the next step, make sure to grab the `Environment Id` from the Power Platform Admin Center

    - Open a new tab and go to the [Power Platform Admin Center](https://aka.ms/ppac)
    - Select **Environments** in the menu on the left
    - Select the environment named **Prod**

      ![](./assets/create-pipeline-new-development-env-ppac-prod.png)

    - Copy the environment ID from there and paste it in the `Deployment Pipeline Configuration` app.

1. Select the **Save and Close** button on the bottom of your sidebar

    ![](./assets/create-pipeline-deploy-to-prod-env.png)

1. Select **Save and Close** again to save the deployment stage as well

## Task 2: Run the first deployment to the QA environment

In this task, you will deploy the solution we created in lab 2 to the QA and Prod environments. Let's start by our first deployment to QA:

### First deployment to QA

In this lab, you have configured a pipeline and the stages that belong to it. But how does a maker deploy a solution from the `Dev` environment to the `QA` and `Prod` environments?

1. Go to the [maker portal](https://make.powerapps.com)

1. Make sure to select the **Dev** environment

1. Go to **Solutions** via the left menu

1. Select the **MPPC 23** solution by selecting the display name

    ![](./assets/run-first-pipeline-dev.png)

1. Select the **rocket icon** on the left

    ![](./assets/run-first-pipeline-solution.png)

    This will show you a new screen where you can see an overview of all stages you just configured in the last task

    ![](./assets/run-first-pipeline-overview.png)

1. Select the purple **Deploy here** button. This will open a new sidebar which will give you the option to start your deployment now or plan your deployment for later

    ![](./assets/run-first-pipeline-select-target.png)

1. Leave it on the default (Now) and select the purple `Next` button on the bottom of the sidebar

1. This will lead you to the next screen where pipelines for Power Platform will validate if the solution needs some configuration steps and/or there are dependencies that are missing. Wait for the validation to finish

    ![](./assets/run-first-pipeline-validation-failed-01.png)

1. As you can see in the screenshot above, the validation failed due to missing dependencies. Select the `Show missing dependencies` button at the top-right corner

1. In the next sidebar that will show up, you will see which dependencies are missing. In this case, it's the `CreatorKitCore` solution:

    ![](./assets/run-first-pipeline-validation-failed-02.png)

    You might remember installing the Creator Kit in lab 01. This is what we need to in the test and prod environments as well.

1. Select the purple `Close` button at the bottom of the sidebar

    ![](./assets/run-first-pipeline-validation-failed-03.png)

1. Select the `Close` button on the bottom-right side of the sidebar

    ![](./assets/run-first-pipeline-validation-failed-04.png)

1. In the following dialog, select the purple `Discard` button to discard changes

    ![](./assets/run-first-pipeline-validation-failed-05.png)

1. This will lead us back to the pipeline overview, where we can start our deployment. Now, lets go to the environment by selecting the `Go to the environment` button in the `Deploy to QA` stage

    ![](./assets/run-first-pipeline-validation-failed-06.png)

1. It will open a new tab which will open the environment homepage where you can go to the `Solutions` menu item to see which solutions are installed in that environment

    ![](./assets/run-first-pipeline-validation-failed-07.png)

1. The `Creator Kit` solution is not part of the list of solutions, so we need to install the `Creator Kit` solution
    ![](./assets/run-first-pipeline-validation-failed-08.png)

You will have to install the Creator Kit in both the test and prod environments.

## Task 3: Install the Creator Kit solution in QA environment

The `Creator Kit` app is now only available in the `Dev` environment, so let's add the app also to the `QA` environment.

1. Go to the [Power Platform Admin Center](https://aka.ms/ppac), select `Environments` in the left menu, and select the `Test` environment by selecting the environment display name

    ![](./assets/run-first-pipeline-validation-failed-09.png)

1. Next, select `Resources` in the command bar at the top and select `Dynamics 365 Apps`. This will lead you to the installed apps in the `QA` environment. There might be some updates available, but you can ignore that for now

    ![](./assets/run-first-pipeline-validation-failed-10.png)

1. Select the `Install app` button in the command bar at the top

    ![](./assets/run-first-pipeline-validation-failed-11.png)

1. Select the `Creator Kit` app and select the purple `Next` button at the bottom of the sidebar

    ![](./assets/run-first-pipeline-validation-failed-12.png)

1. Select the `I agree to the terms of service` checkbox and select the purple `Install` button

    ![](./assets/run-first-pipeline-validation-failed-13.png)

1. In the next screen, you will see a message at the top that the installation of the `Creator Kit` has been started. Select `Environments` in the breadcrumb at the top

    ![](./assets/run-first-pipeline-validation-failed-14.png)

Next, you have to install the `Creator Kit` app in the `Prod` environment.

## Task 4: Install the Creator Kit solution in Prod environment

The `Creator Kit` app is now only available in the `Dev` and `QA` environments, so let's add the app also to the `Prod` environment to avoid missing dependencies there.

1. Go to the [Power Platform Admin Center](https://aka.ms/ppac), select `Environments` in the left menu, and select the `Prod` environment by selecting the environment display name

    ![](./assets/run-first-pipeline-validation-failed-15.png)

1. Next, select `Resources` in the command bar at the top and select `Dynamics 365 Apps`. This will lead you to the installed apps in the `QA` environment. There might be some updates available, but you can ignore that for now

    ![](./assets/run-first-pipeline-validation-failed-16.png)

1. Select the `Install app` button in the command bar at the top

    ![](./assets/run-first-pipeline-validation-failed-17.png)

1. Select the `Creator Kit` app and select the purple `Next` button at the bottom of the sidebar

    ![](./assets/run-first-pipeline-validation-failed-18.png)

1. Select the `I agree to the terms of service` checkbox and select the purple `Install` button

    ![](./assets/run-first-pipeline-validation-failed-19.png)

1. In the next screen, you will see a message at the top that the installation of the `Creator Kit` has been started. Select `Environments` in the breadcrumb at the top

    ![](./assets/run-first-pipeline-validation-failed-20.png)

Now that you have triggered the install of the `Creator Kit` in both the `QA` and `Prod` environments, you can move on to task 06, retrying the deployment to the `QA` environment.

## Task 5: Retry the deployment to the QA environment

To make sure your deployment goes well, lets check if the Creator Kit solution has been properly installed in the `QA` environment.

### Check if the Creator Kit app is correctly installed

1. Go to the [maker portal](https://make.powerapps.com)

1. Check if you are in the `QA` environment and if not, switch to that environment

    ![](./assets/check-environment-test.png)

1. Select `Solutions` in the left navigation and check if the `Creator Kit (Name: CreatorKitCore)` solution is installed

    ![](./assets/check-install-creator-kit-test.png)

1. If that's the case, you are ready for deployment. If not, you probably have to wait a little bit until the Creator Kit is installed

### Deploy the solution to the QA environment

For the deployment to QA, you have to switch to your `Dev` environment. Make sure to do that and verify that you are in the right environment:

![](./assets/check-environment-dev.png)

1. Go to Solutions via the left menu

1. Select the `Mixed Reality Workshop` solution by selecting the display name

    ![](./assets/run-first-pipeline-dev.png)

1. Select the rocket icon on the left

    ![](./assets/run-first-pipeline-solution.png)

1. Select the purple `Deploy here` button.

    ![](./assets/run-deploy-to-test-deploy-here.png)

1. This will open a new sidebar which will give you the option to start your deployment now or plan your deployment for later. Select the purple `Next` button to go to the next screen

    ![](./assets/run-first-pipeline-select-target.png)

1. The next screen will be a bit different from our last try, it will now show a summary of the deployment. Fill in some deployment notes, like for instance: `First deployment of the Mixed Reality solution` and select the purple `Deploy` button

    ![](./assets/run-deploy-to-test-deployment-notes.png)

1. This will trigger the `Deploy to QA` stage

    ![](./assets/run-deploy-to-test-in-progress.png)

1. When it's done, you will see that the deployment has been finished

    ![](./assets/run-deploy-to-test-finished.png)

### Test if the solution was correctly deployed

1. Of course, you want to see for yourself if the deployment was successful, so select the `Go to this environment` button in the `Deploy to QA` stage

    ![](./assets/run-deploy-to-test-check-test.png)

1. Select `Solutions` in the left navigation

1. Check if the `Mixed Reality Workshop` solution with version 1.0.0.1 is installed in the `QA` environment

    ![](./assets/run-deploy-to-test-check-test-solution.png)

1. Open the `Mixed Reality Workshop` by selecting the display name

    ![](./assets/run-deploy-to-test-open-solution.png)

1. Select the `Mixed Reality App` canvas app and select the `Play` button in the command bar at the top

    ![](./assets/run-deploy-to-test-open-app.png)

1. When the app is opened, you will have to allow the connections to connect to both OneDrive for Business as well as the Smithsonian 3D connector. Make sure to select the purple `Allow` button

    ![](./assets/run-deploy-to-test-allow-connections.png)

1. In the app, you will find three buttons:

    `Corals and Coral Reefs`, `Smithsonian 3D Search`, and `Tutorial Screen`.

    Select the `Corals and Coral Reefs` button

    ![](./assets/run-deploy-to-test-select-corals.png)

1. Next, select the first coral to check if the coral 3D object works

    ![](./assets/run-deploy-to-test-select-coral.png)

1. The next screen should show a 3D object of the coral you just selected

    ![](./assets/run-deploy-to-test-coral-detail.png)

Now you know the app works in QA, let's deploy it to production.

## Task 6: Deploy to the Prod environment

To make sure your deployment goes well, lets check if the Creator Kit solution has been properly installed in the `Prod` environment.

### Check if the Creator Kit app is correctly installed

1. Go to the [maker portal](https://make.powerapps.com)

1. Check if you are in the `Prod` environment and if not, switch to that environment

    ![](./assets/check-environment-prod.png)

1. Select `Solutions` in the left navigation and check if the `Creator Kit (Name: CreatorKitCore)` solution is installed

    ![](./assets/check-install-creator-kit-prod.png)

1. If that's the case, you are ready for deployment. If not, you probably have to wait a little bit until the Creator Kit is installed

### Deploy the solution to the Prod environment

For the deployment to prod, you have to switch to your `Dev` environment. Make sure to do that and verify that you are in the right environment:

![](./assets/check-environment-dev.png)

1. Go to Solutions via the left menu

1. Select the `Mixed Reality Workshop` solution by selecting the display name

    ![](./assets/run-first-pipeline-dev.png)

1. Select the rocket icon on the left

    ![](./assets/run-first-pipeline-solution.png)

1. Select the purple `Deploy here` button.

    ![](./assets/run-deploy-to-prod-deploy-here.png)

1. This will open a new sidebar which will give you the option to start your deployment now or plan your deployment for later. Select the purple `Next` button to go to the next screen

    ![](./assets/run-deploy-to-prod-select-target.png)

1. Fill in some deployment notes, like for instance: `First deployment of the Mixed Reality solution` and select the purple `Deploy` button

    ![](./assets/run-deploy-to-prod-deployment-notes.png)

1. This will trigger the `Deploy to prod` stage

    ![](./assets/run-deploy-to-prod-in-progress.png)

1. When it's done, you will see that the deployment has been finished

    ![](./assets/run-deploy-to-prod-finished.png)

### Test if the solution was correctly deployed

1. Of course, you want to see for yourself if the deployment was successful, so select the `Go to this environment` button in the `Deploy to prod` stage

    ![](./assets/run-deploy-to-prod-check-prod.png)

1. Select `Solutions` in the left navigation

1. Check if the `Mixed Reality Workshop` solution with version 1.0.0.1 is installed in the `Prod` environment

    ![](./assets/run-deploy-to-prod-check-prod-solution.png)

1. Open the `Mixed Reality Workshop` by selecting the display name

    ![](./assets/run-deploy-to-prod-open-solution.png)

1. Select the `Mixed Reality App` canvas app and select the `Play` button in the command bar at the top

    ![](./assets/run-deploy-to-prod-open-app.png)

1. When the app is opened, you will have to allow the connections to connect to both OneDrive for Business as well as the Smithsonian 3D connector. Make sure to select the purple `Allow` button

    ![](./assets/run-deploy-to-test-allow-connections.png)

1. In the app, you will find two buttons:

    `Corals and Coral Reefs` and `Smithsonian 3D Search`

    Select the `Corals and Coral Reefs` button

    ![](./assets/run-deploy-to-test-select-corals.png)

1. Next, select the first coral to check if the coral 3D object works

    ![](./assets/run-deploy-to-test-select-coral.png)

1. The next screen should show a 3D object of the coral you just selected

    ![](./assets/run-deploy-to-test-coral-detail.png)

Now you know the app works in prod as well and you have successfully deployed the solution to the `QA` and `Prod` environments.

## Next lab

This is the end of lab 3, select the link below to move to the next lab.

[⏭️ Move to lab 4](../lab4/README.md)
