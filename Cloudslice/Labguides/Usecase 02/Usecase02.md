# Usecase 02- Modernize your code with agents with Microsoft Foundry 

**Scenario: Modernizing Large Data Estates for Contoso**

Contoso, a global enterprise managing vast amounts of historical data,
faces significant challenges while modernizing its legacy data estate.
Over the years, the organization has accumulated thousands of files
written in multiple outdated query dialects. With missing documentation
and limited expertise in these legacy languages, analyzing and
maintaining their systems has become increasingly difficult.

Modernization efforts require translating all legacy queries into a
modern, standardized alternative—a process that is typically slow,
manual, and error-prone. Engineers often spend substantial time
reverse-engineering business logic, increasing the risk of errors that
can affect data integrity and downstream analytics. In addition, the
limited availability of specialists familiar with older languages
increases costs and creates long-term dependencies on niche skills.

To address these challenges, **Nathan Rigby**, an experienced Software
Developer at Contoso, plays a key role in maintaining and modernizing
the company’s critical systems. Nathan leverages the **Modernize Your
Code Solution Accelerator**, powered by **Microsoft Foundry agents**, to
automate and streamline the translation of outdated code. These
intelligent agents analyze legacy queries, extract underlying business
logic, and convert them into modern, optimized equivalents with high
accuracy.

By offloading complex translation and analysis tasks to Foundry agents,
Nathan significantly reduces manual workload and removes repetitive,
error-prone processes. This frees him to focus on higher-value
engineering tasks—such as performance tuning, building new features, and
advancing Zava’s modernization roadmap.

With the combined power of the solution accelerator and Microsoft
Foundry agents, Zava accelerates its modernization journey, ensures
high-quality and consistent code translation, and builds a scalable,
future-ready data environment.

By adopting the Modernize Your Code Solution Accelerator, Zava
accelerates its migration efforts, ensures consistent and accurate
translations, and builds a scalable path forward for modernizing its
entire data environment.

**Introduction**

Modernizing legacy codebases is one of the most challenging tasks for
organizations with large and outdated data estates. Over the years,
companies like **Zava** have accumulated thousands of SQL queries and
scripts across multiple legacy dialects such as Informix, Netezza,
Teradata, and other outdated systems. These queries lack proper
documentation, rely on deprecated syntax, and require niche expertise to
interpret and migrate. Manually modernizing such code is slow,
error-prone, and heavily dependent on specialized engineers.

To address these challenges, Zava adopts the **Modernize Your Code
Solution Accelerator**, powered by **Microsoft Foundry agents**, which
provide intelligent, automated assistance for analyzing, translating,
and modernizing legacy SQL code. These agents understand legacy logic,
extract business rules, translate them into modern standards, and ensure
consistency across large-scale migrations. By integrating Foundry’s
agent-driven capabilities into their modernization workflow, Zava
accelerates its migration journey while significantly reducing manual
effort and technical risk.

**Objectives**

- Understand how Microsoft Foundry agents assist in code modernization
  by analyzing legacy SQL dialects and generating optimized modern
  equivalents.

- Set up required Azure services including resource providers, resource
  groups, Foundry, Container Apps, Cosmos DB, and supporting components
  using Azure Developer CLI.

- Create and configure an environment using GitHub Codespaces to run the
  Modernize-your-code Solution Accelerator.

- Deploy and verify modernization components such as backend, frontend,
  and Foundry project within Azure.

- Upload and translate legacy SQL files using the accelerator’s workflow
  and review the conversion output.

- Observe real-time batch processing that shows how legacy files are
  queued, processed, and made available for download.

- Download and validate translated modern SQL code, ensuring translation
  accuracy and completeness.

- Clean up deployed Azure resources safely after completing the lab.

![A diagram of a code AI-generated content may be
incorrect.](./media/image1.png)

**Prerequisites**

- **GitHub Account**: You are expected to have your own GitHub login
  credentials.  
  If you do not have an account, please create one by visiting:  
  https://github.com/signup

## Task 0: Understand the VM and the credentials

In this task, we will identify and understand the credentials that we
will be using throughout the lab.

1.  **Guide** tab hold the lab guide with the instructions to be
    followed throughout the lab.

2.  **Resources** tab has got the credentials that will be needed for
    executing the lab.

    - **Username -**VM username

    - **Password-** VM password

**Azure credentials:**

- **Username** – The user id with which you need to login to the Azure
  services.

- **Password** – Password to the Azure login. Let us call this Username
  and password as Azure login credentials. We will use these creds
  wherever we mention Azure login credentials.

- **Generate Authentication code**

![](./media/image2.png)

3.  Ensure that **Enhanced Mode** is enabled in the Tools section before
    proceeding with the lab tasks

> ![](./media/image3.png)

\[!Alert\] **Important:** Make sure you create all your resources under
this Resource group

## Task 1: Register Service provider

1.  Open a browser go to +++https://portal.azure.com+++ and sign in with
    your cloud slice account below.

Username: <+++@lab.CloudPortalCredential>(User1).Username+++

Password: <+++@lab.CloudPortalCredential>(User1). *TAP*+++

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image4.png)

![A login box with a red box and blue box with text AI-generated content
may be incorrect.](./media/image5.png)

2.  Click on **Subscriptions** tile.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image6.png)

3.  Click on the subscription name.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image7.png)

4.  Expand Settings from the left navigation menu. Click on **Resource
    providers**, enter **+++** **Microsoft.CognitiveServices+++** and
    select i,t, and then click **Register**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image8.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image9.png)

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image10.png)

5.  Repeat the steps \#4 to register the following Resource provider.

- +++**Microsoft.AlertsManagement**+++

## Task 2: Retrieve resource group name and location

1.  Type in +++**Resource group+++** in the search bar and
    select **Resource groups**.

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image11.png)

2.  Click on your assigned **Resource group**.

> ![](./media/image12.png)

3.  In **Resource group** page, copy **resource group name and
    location** and paste them in a notepad, then **Save** the notepad to
    use the information in the upcoming tasks.

> ![](./media/image13.png)

## Task 3: Open Github Codespaces environment

1.  Open your browser, navigate to the address bar, type or paste the
    following URL: 

> +++https://github.com/technofocus-pte/code-solution-accelerator.git+++

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image14.png)

2.  Click on **fork** to fork the repo. Give unique name to the repo and
    click on **Create repo** button.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image15.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image16.png)

3.  Click on **Code -\> Codespaces -\> Codespaces+**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image17.png)

4.  Wait for the Codespaces environment to setup .It takes few minutes
    to setup completely

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image18.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image19.png)

## Task 4: Provision Services and deploy application to Azure

1.  Run the following command on the Terminal. It generates the code to
    copy. Copy the code and press Enter.

+++azd auth login+++

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image20.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image21.png)

5.  Default browser opens to enter the generated code to verify. Enter
    the code and click **Next**.

![A screenshot of a computer error AI-generated content may be
incorrect.](./media/image22.png)

6.  Sign in with your Azure credentials.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image23.png)

![A screenshot of a computer error AI-generated content may be
incorrect.](./media/image24.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image25.png)

7.  To create an environment for Azure resources, run the following
    Azure Developer CLI command.It asks you to enter environment name
    .Enter any name of your choice and press enter (eg
    :+++cmsaappXXXX+++)

**Note:** When creating an environment, ensure that the name consists of
lowercase letters.

+++azd env new+++

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image26.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image27.png)

8.  Run below command to provision the services to Azure, build your
    container.

+++azd env set AZURE_RESOURCE_GROUP {Name of existing resource group}+++

![A screenshot of a computer code AI-generated content may be
incorrect.](./media/image28.png)

9.  Run azd up - This will provision Azure resources

+++azd up+++

![A screenshot of a computer code AI-generated content may be
incorrect.](./media/image29.png)

10. Select below values.

- **Select an Azure Subscription to use** : Select your subscription

- **azureAiServiceLocation**: Sweden Central

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image30.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image31.png)

11. This deployment will take *7-10 minutes* to provision the resources
    in your account and set up the solution with sample data

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image32.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image33.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image34.png)

## Task 5: Verify deployed resources in the Azure portal

1.  Select **Resource groups**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image35.png)

2.  Click on your assigned **Resource group**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image36.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image37.png)

3.  Make sure the below resource got deployed successfully

- Foundry

- Foundry project

- Container App ( backend and frontend)

- Azure CosmosDB account

- Container App Environment

- Keyvault

- Azure Storage account

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image38.png)

4.  Select **Foundry**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image39.png)

5.  Click **Go to Foundry portal** to verify that the model has been
    successfully deployed

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image40.png)

6.  Go back to resorcegroup and select **Frontend Container App**

![A screenshot of a chat AI-generated content may be
incorrect.](./media/image41.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image42.png)

7.  Click on the **Application Url**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image43.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image44.png)

## Task 6: Sample Workflow for Modernizing SQL Code with Modernize-your-code Solution Accelerator

1.  In the Container App , select **Browse files**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image45.png)

2.  Navigate to **C:\Labfiles\\** **informix** location and
    select **q1_informix.sql** from *simple* folder
    and **F1.sql** and **F2.sql** from *functions* folder, then click on
    the **Open** button.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image46.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image47.png)

3.  Click **Start Translating** Button to Process Files

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image48.png)

*Average translating time is 01 minute 15 seconds*

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image49.png)

**Review**

- The batch Processing page will open and the translation process will
  be visible. One file at a time will be processed and others will be in
  queued state.

- Once the batch processing is done for any file, the file is available
  to review.

- Once the translation process is complete for a batch, it becomes
  available for review in the History panel (located at the top right).

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image50.png)

4.  Once the files are translated, the **Download all as .zip** button
    at the bottom left will be enabled to download the translated files.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image51.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image52.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image53.png)

## Task 7: Clean up all the resources

1.  Switch back to **Azure portal -\> Resource group-\> Resource group
    name.**

> ![](./media/image13.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image54.png)

2.  Select all the resources and then click on Delete as shown in the
    below image. (**DO NOT DELETE** resource group)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image55.png)

3.  Type delete on the text box and then click on **Delete**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image56.png)

**Summary**

In this use case, you learned how Zava modernizes large and complex
legacy SQL codebases using the **Modernize Your Code Solution
Accelerator** powered by **Microsoft Foundry agents**. You began by
preparing Azure services and configuring a GitHub Codespaces environment
to run the accelerator. You then deployed the required Azure resources,
validated their availability, and explored how Foundry agents help
translate outdated SQL files into modern, standardized formats.

Using the provided modernization workflow, you uploaded legacy SQL
files, executed translations, tracked their processing, and accessed the
converted outputs. This demonstrated how Foundry agents reduce manual
effort, eliminate dependency on niche legacy expertise, and enhance
overall translation accuracy.

By the end of the lab, you gained hands-on experience with agent-driven
code transformation, explored scalable modernization architecture, and
successfully completed the end-to-end modernization process. This
foundation equips you to accelerate large-scale modernization
initiatives using Microsoft Foundry.
