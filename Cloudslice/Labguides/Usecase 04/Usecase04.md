# Usecase 04-Developing Intelligent Chat Applications with Azure RAG

**Introduction**

This sample demonstrates a few approaches for creating ChatGPT-like
experiences over your own data using the Retrieval Augmented Generation
pattern. It uses Azure OpenAI Service to access the ChatGPT model , and
Azure Cognitive Search for data indexing and retrieval.

The repo includes sample data so it's ready to try end to end. In this
sample application we use a fictitious company called Contoso
Electronics, and the experience allows its employees to ask questions
about the benefits, internal policies, as well as job descriptions and
roles.

This use case you through the process of developing a sophisticated chat
application using the Retrieval Augmented Generation (RAG) pattern on
the Azure platform. By leveraging Azure OpenAI Service and Azure
Cognitive Search, you will create a chat application that can
intelligently answer questions using your own data. This lab uses a
fictitious company, Contoso Electronics, as a case study to demonstrate
how to build a ChatGPT-like experience over enterprise data, covering
aspects such as employee benefits, internal policies, and job roles.

![RAG Architecture](./media/image1.png)

GitHub account -- You are expected to have your own GitHub login
credentials. If you do not have, please create one from here -
+++<https://github.com/signup?user_email=&source=form-home-signup+++>

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

## Task 1: Retrieve resource group name and location

1.  Open your browser, navigate to the address bar, and type or paste
    the following URL: +++<https://portal.azure.com/+++>, then press
    the **Enter** button.

![A screenshot of a computer Description automatically
generated](./media/image4.png)

2.  In the **Microsoft Azure** window, use the **User Credentials** to
    login to Azure.

![](./media/image5.png)

3.  Then, enter the password and click on the **Sign in** button.

![](./media/image6.png)

4.  In **Stay signed in?** window, click on the **Yes** button.

5.  Type in +++Resource group+++ in the search bar and select **Resource
    groups**.

![](./media/image7.png)

6.  Click on your assigned **Resource group**.

![](./media/image8.png)

7.  In **Resource group** page, copy **resource group name and
    location** and paste them in a notepad, then **Save** the notepad to
    use the information in the upcoming tasks.

![](./media/image9.png)

## Task 2: Open development environment

1.  Open your browser, navigate to the address bar, type or paste the
    following URL:
    +++<https://github.com/technofocus-pte/azuresearchopenai.git+++>

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image10.png)

2.  Click on **fork** to fork the repo. Give unique name to the repo and
    click on **Create repo** button.

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image11.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image12.png)

3.  Click on **Code -\> Codespaces -\> Create codespace on main**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image13.png)

4.  Wait for the Codespaces environment to setup .It takes few minutes
    to setup completely

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image14.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image15.png)

## Task 3: Provision Services and deploy application to Azure

1.  Run the following command on the Terminal. It generates the code to
    copy. Copy the code and press Enter.

+++azd auth login+++

![](./media/image16.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image17.png)

2.  Default browser opens to enter the generated code to verify. Enter
    the code and click **Next**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image18.png)

3.  Sign in with your Azure credentials.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image19.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image20.png)

4.  To create an environment for Azure resources, run the following
    Azure Developer CLI command.

\[!Note\]: When creating an environment, ensure that the name consists
of lowercase letters.

+++azd env new+++

It asks you to enter environment name.
Enter [+++ragopenaiXXXX](mailto:+++ragopenai@lab.LabProfile.Id)+++

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image21.png)

5.  Run below command to provision the services to Azure, build your
    container.

+++azd env set AZURE_RESOURCE_GROUP
@lab.CloudResourceGroup(ResourceGroup1).Name+++

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image22.png)

6.  Run below command to provision the services region to Azure, build
    your container

+++azd env set AZURE_LOCATION
@lab.CloudResourceGroup(ResourceGroup1).Location+++

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image23.png)

7.  Run azd up - This will provision Azure resources and deploy this
    sample to those resources, including building the search index based
    on the files found in the ./data folder.

+++azd up+++

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image24.png)

8.  Wait until app is deployed. It may take **35-40** minutes for the
    deployment to complete.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image25.png)

9.  Select below values.

    - **Select your Azure
      Subscription** : **@lab.CloudSubscription.Name**

    - **documentIntelligenceResourceGroupLocation**: East US

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image26.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image27.png)

10. When prompted, **enter a value for the ‘openAiResourceGroupLocation’
    infrastructure parameter** use the arrow keys to
    select **@lab.CloudResourceGroup(ResourceGroup1).Location**.

\[!Note\] If another **Location** selection appears, use the arrow keys
to select **@lab.CloudResourceGroup(ResourceGroup1).Location**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image28.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image29.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image30.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image31.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image32.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image33.png)

11. After the application has been successfully deployed, you see a URL
    displayed in the terminal. Copy the **URL**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image34.png)

12. Click on the **Open**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image35.png)

13. Open your browser, navigate to the address bar, paste the link. Now,
    resource group will open in a new browser

![A screenshot of a computer Description automatically
generated](./media/image36.png)

![A screenshot of a computer Description automatically
generated](./media/image37.png)

## Task 4: Verify deployed resources in the Azure portal

1.  Select **Resource groups**

![](./media/image38.png)

2.  Click on your assigned **Resource group**.

![](./media/image39.png)

3.  Make sure the below resource got deployed successfully

    - Azure App Service

    - Azure Application Insights

    - Container App

    - Container registry

    - Azure OpenAI

    - Azure Document Intelligence

    - Azure Search Service

    - Azure Storage Account

    - Azure Speech Service

![](./media/image40.png)

![](./media/image41.png)

4.  On the resource group and click on **AI Search service.**

![](./media/image42.png)

5.  Make sure Indexes should be deployed successfully

![](./media/image43.png)

6.  Go back to resorcegroup and click on **Storage account.**

![](./media/image44.png)

7.  From the left navigation menu, click on **Containers** , Make sure
    data should be deployed successfully

![](./media/image45.png)

## Task 6: Use chat app to get answers from PDF files

1.  Wait for the web application deployment to complete.

![](./media/image46.png)

2.  In the **GPT+Eneterprise data |Sample** web app page, enter the
    following text and click on the **Submit icon** as shown in the
    below image.

+++What happens in a performence review?+++

![](./media/image47.png)

![A screenshot of a computer Description automatically
generated](./media/image48.png)

3.  From the answer, select a **citation**.

![](./media/image49.png)

4.  In the right-pane, use the tabs to understand how the answer was
    generated.

[TABLE]

5.  ![](./media/image50.png)

6.  ![](./media/image51.png)

> ![](./media/image52.png)

7.  Select the selected tab again to close the pane.

8.  The intelligence of the chat is determined by the OpenAI model and
    the settings that are used to interact with the model.

9.  Select the **Developer settings**.

![](./media/image53.png)

![](./media/image54.png)

[TABLE]

10. Check the **Suggest follow-up questions** checkbox and ask the same
    question again.

![](./media/image55.png)

11. Enter the following text and click on the **Submit icon** as shown
    in the below image.

+++What happens in a performance review?+++

![](./media/image56.png)

12. The chat returned suggested follow-up questions such as the
    following

![](./media/image57.png)

13. In the **Settings** tab, deselect **Use semantic ranker for
    retrieval**.

![](./media/image58.png)

![](./media/image59.png)

14. Enter the following text and click on the **Submit icon** as shown
    in the below image.

+++What happens in a performance review?+++

![](./media/image60.png)

![](./media/image61.png)

## Task 7: Delete the Resources

1.  To delete Resource group , type **Resource groups** in the Azure
    portal search bar, navigate and click on **Resource
    groups** under **Services**.

![A screenshot of a computer Description automatically
generated](./media/image62.png)

2.  Click on the sample web app resource group.

![](./media/image63.png)

3.  In the resource group home page , select **all resources** .

![](./media/image64.png)

4.  Select Delete

![](./media/image65.png)

![](./media/image66.png)

**Summary**

In this lab, you’ve learned how to set up and deploy an intelligent chat
application using Azure's suite of tools and services. Starting with the
installation of essential tools like Azure CLI and Node.js, you’ve
configured your development environment using Dev Containers in Visual
Studio Code. You've deployed a chat application that utilizes Azure
OpenAI and Azure Cognitive Search to answer questions from PDF files.
Finally, you’ve deleted the deployed resources to effectively manage
resources. This hands-on experience has equipped you with the skills to
develop and manage intelligent chat applications using the Retrieval
Augmented Generation pattern on Azure.
