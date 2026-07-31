# Uasecase 08- Intelligent customer service Chatbot with Microsoft Foundry Agent Framework

**Introduction**

**Contoso Retail**, a large online retail company, receives thousands of
customer inquiries daily related to product availability, product
recommendations, return policies, shipping information, warranties, and
order-related questions. Traditional support channels rely heavily on
human agents, resulting in long wait times, inconsistent responses, and
increased operational costs.

To address these challenges, Contoso implements the **Customer Chatbot
Solution Accelerator** built on the **Microsoft Foundry Agent
Framework**. The solution uses an intelligent orchestrator agent that
analyzes customer questions and routes them to specialized agents:

- **Product Lookup Agent** retrieves product details, specifications,
  availability, and recommendations.

- **Policy & Knowledge Agent** answers questions related to return
  policies, warranties, shipping procedures, and company guidelines.

- **Orchestrator Agent** coordinates the conversation and ensures
  customers receive accurate, context-aware responses based on
  enterprise data sources

![image](./media/image1.png)

**Objectives**

- Register and configure the required Azure resource providers for AI
  services.

- Set up a GitHub Codespaces development environment for the Customer
  Chatbot Solution Accelerator.

- Provision Azure resources and deploy the Intelligent Customer Service
  Chatbot application using Azure Developer CLI (AZD).

- Configure the deployed solution by creating a virtual environment,
  authenticating with Azure, and building application container images.

- Load sample product data and create search indexes for knowledge
  retrieval.

- Create and configure AI Foundry Agents to support intelligent customer
  interactions.

- Implement an orchestrated multi-agent architecture consisting of
  Product Lookup, Policy & Knowledge, and Orchestrator Agents.

- Test chatbot functionality by interacting with the application using
  real-world customer service scenarios.

- Validate deployed Azure resources, AI models, and Foundry components
  through the Azure portal and Foundry portal.

- Demonstrate how AI-powered agents can provide accurate, context-aware,
  and efficient customer support experiences.

- Clean up and delete deployed Azure resources after completing the lab

## Task 1: Register Service provider

1.  Open a browser go to +++https://portal.azure.com+++ and sign in with
    your cloud slice account below.

> Username: <+++@lab.CloudPortalCredential>(User1).Username+++
>
> Password: <+++@lab.CloudPortalCredential>(User1). *TAP*+++

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image2.png)

![A login box with a red box and blue box with text AI-generated content
may be incorrect.](./media/image3.png)

2.  Click on **Subscriptions** tile.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image4.png)

3.  Click on the subscription name.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image5.png)

4.  Expand Settings from the left navigation menu. Click on **Resource
    providers**, enter **+++** **Microsoft.CognitiveServices+++** and
    select i,t, and then click **Register**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image6.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image7.png)

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image8.png)

## Task 2: Open Github Codespaces environment

1.  Open your browser, navigate to the address bar, type or paste the
    following URL: 
    +++https://github.com/technofocus-pte/customer-chatbotsolution-accelerator+++

> ![](./media/image9.png)

2.  Click on **fork** to fork the repo. Give unique name to the repo and
    click on **Create repo** button.

> ![](./media/image10.png)
>
> ![](./media/image11.png)

3.  Click on **Code -\> Codespaces -\> Create codespace on main**

> ![](./media/image12.png)

4.  Wait for the Codespaces environment to setup .It takes few minutes
    to setup completely

> ![](./media/image13.png)
>
> ![](./media/image14.png)

## Task 3: Provision Services and deploy application to Azure

1.  Run the following command on the Terminal. It generates the code to
    copy. Copy the code and press Enter.

+++azd auth login+++

![](./media/image15.png)

2.  Default browser opens to enter the generated code to verify. Enter
    the code and click **Next**.

![](./media/image16.png)

3.  Sign in with your Azure credentials.

![](./media/image17.png)

![](./media/image18.png)

![](./media/image19.png)

4.  Run azd up - This will provision Azure resources

+++azd up+++

5.  To create an environment for Azure resources, enter any name of your
    choice and press enter (eg :+++ chatbotXXXX +++)

![](./media/image20.png)

6.  Select below values.

- **Select an Azure Subscription to use** : Select your subscription

- **azureAiServiceLocation**: Sweden Central

- **‘location' infrastructure parameter:** Central US

- **Pick a resource group to use:** Existing resource group

> ![](./media/image21.png)

![](./media/image22.png)

![](./media/image23.png)

![](./media/image24.png)

7.  This deployment will take *7-10 minutes* to provision the resources
    in your account and set up the solution with sample data.

![](./media/image25.png)

![](./media/image26.png)

![](./media/image27.png)

8.  After the application has been successfully deployed, you see a URL
    displayed in the terminal. Copy the **URL**

![](./media/image28.png)

## Task 4: Post-Deployment Configuration

After successful deployment, complete these essential steps to set up
your chatbot application:

1\. Create and activate a virtual environment by running the following
command

> **python -m venv .venv**

![](./media/image29.png)

2**.** Activate the virtual environment by running the following command

source .venv/bin/activate

![](./media/image30.png)

3.  In the terminal, run the **az login** command. When the device login
    code is displayed, copy the code, open
    **https://login.microsoftonline.com/device**, and enter the code to
    authenticate your Azure session.

![](./media/image31.png)

![](./media/image32.png)

![](./media/image33.png)

![](./media/image34.png)

4.  Select azure subscription

![](./media/image35.png)

5.  The initial deployment configures the App Services with a
    placeholder container. Run the ACR build script to build the real
    backend/frontend images inside Azure Container Registry and point
    both web apps at them:

**bash ./infra/scripts/build_push_images.sh**

![](./media/image36.png)

![](./media/image37.png)

![](./media/image38.png)

6.  Run the data setup script to load sample product data

**bash ./infra/scripts/data_scripts/run_upload_data_scripts.sh**

![](./media/image39.png)

![](./media/image40.png)

7.  ** Create AI Foundry Agents** Run the data setup script to load
    sample product data and create search indexes in Azure AI Search:

**bash ./infra/scripts/agent_scripts/run_create_agents_scripts.sh**

![](./media/image41.png)

![](./media/image42.png)

## Task 5: Test the Application

1.  Open the web app URL in your browser.

> ![](./media/image28.png)
>
> ![](./media/image43.png)

2.  Click **Open Chat**

![](./media/image44.png)

3.  Enter the following text and click on the **Submit icon** as shown
    in the below image.

+++I'm looking for a cool, blue-toned paint that feels calm but not
gray+++

![](./media/image45.png)

![](./media/image46.png)

4.  Enter the following text and click on the **Submit icon** as shown
    in the below image.

> +++Do you provide a color matching service?+++

![](./media/image47.png)

![](./media/image48.png)

5.  Enter the following text and click on the **Submit icon** as shown
    in the below image

> What’s your warranty like?

![](./media/image49.png)

![](./media/image50.png)

6.  Enter the following text and click on the **Submit icon** as shown
    in the below image

**+++And if I don’t like the color once it’s on the wall?+++**

![](./media/image51.png)

![](./media/image52.png)

## Task 6: Verify deployed resources in the Azure portal

1.  Open a browser go to ++++++ and sign in with your cloud slice
    account below.

2.  Select **Resource groups**

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image53.png)

3.  Click on your assigned **Resource group**.

![](./media/image54.png)

3.  Make sure the below resource got deployed successfully

- Foundry

- Foundry project

- App Service

- Container registry

- Azure Cosmos DB account

- Container App

- SQL Database

- Search service(FoundryIQ)

![](./media/image55.png)

4.  Click on **Foundry Project.**

![](./media/image56.png)

7.  Click **Go to Foundry portal** to verify that the model has been
    successfully deployed.

![](./media/image57.png)

![](./media/image58.png)

![](./media/image59.png)

## Task 7: Delete the Resources

1.  To delete Resource group , type **Resource groups** in the Azure
    portal search bar, navigate and click on **Resource
    groups** under **Services**.

> ![A screenshot of a computer Description automatically
> generated](./media/image60.png)

2.  In the Resource groups page, select your resource group.

> ![](./media/image61.png)

3.  In the **Resource group** home page, select all resources and click
    on **delete**

![](./media/image62.png)

![](./media/image63.png)

**Summary**

In this lab, you deploy an **Intelligent Customer Service Chatbot
Solution Accelerator** on Microsoft Azure using the **Microsoft Foundry
Agent Framework**. The deployment includes provisioning Azure resources,
configuring application services, creating AI Foundry agents, loading
product data, and integrating Azure AI Search for knowledge retrieval.
The chatbot is then tested with real-world customer scenarios involving
product recommendations, color-matching services, warranties, and return
policies. Finally, the deployed resources and agents are validated in
the Azure portal to ensure successful implementation. The solution
demonstrates how AI agents can work together to deliver scalable,
personalized, and efficient customer support experiences

![](./media/image64.png)
