# Agentic AI and data governance on Microsoft Azure

### Overall Estimated Duration: 4 Hours

## Overview

In this hands-on lab, you will work through three Microsoft Foundry scenarios that go beyond building a single agent — orchestrating many agents together, hardening an agent against misuse, and specializing a model's behavior through fine-tuning.

In **Usecase 3 (Autonomous Multi-Agent Employee Onboarding Orchestration)**, you will deploy Contoso's Multi-Agent Custom Automation accelerator on Azure and use it to run several cross-department business scenarios — including HR onboarding — where specialized AI agent teams collaborate to generate and execute task plans with human-in-the-loop approval.

In **Usecase 4 (Safeguard your agents with AI Red Teaming Agent in Microsoft Foundry)**, you will deploy Zava's document-aware AI knowledge assistant using Azure AI Agent Service, validate its retrieval accuracy, score it with Foundry's built-in evaluators, and then run an automated **AI Red Teaming Agent** scan to proactively surface safety and security gaps before enabling tracing and continuous evaluation for production monitoring.

In **Usecase 5 (Deploying and Evaluating Fine-Tuned GPT Models in Azure AI Projects)**, you will deploy a base GPT-5 model in a Microsoft Foundry project for a travel-planning assistant, observe how generic and inconsistent its tone is out of the box, then fine-tune the model on a small curated set of example conversations, and deploy and compare the fine-tuned model against the base model.

## Objective

By the end of this lab, participants will be able to:

- **Deploy the Multi-Agent Custom Automation accelerator on Azure** using GitHub Codespaces and the Azure Developer CLI (`azd auth login`, `azd up`), provisioning Foundry, a Foundry project, Container Apps, Cosmos DB, Azure AI Search, and a storage account.

- **Complete post-deployment configuration**, including uploading team configurations and sample data for specific use-case scenarios, and adding authentication to the deployed App Service.

- **Run and observe multiple business-process scenarios** — Retail, Product Marketing, HR Onboarding, and RFP Analysis — where specialized agent teams (such as HR Helper, Technical Support, and Proxy agents) generate task plans, request human-in-the-loop clarification and approval, and coordinate execution across departments.

- **Deploy a document-aware AI knowledge assistant** using Azure AI Agent Service, provisioned through `azd` alongside Foundry, Container Apps, Cosmos DB, AI Search, and storage.

- **Validate agent retrieval accuracy** by interacting with the assistant using predefined and custom prompts.

- **Run Foundry's built-in evaluators** — intent resolution, tool call accuracy, task adherence, and content safety — to measure agent quality and safety.

- **Run an automated AI Red Teaming Agent scan** that generates its own adversarial prompts across configurable attack strategies (such as Flip and Base64) and multi-turn conversations, then analyze the results in Microsoft Foundry.

- **Enable tracing, monitoring, and continuous evaluation** to track real-time agent behavior in production.

- **Deploy a base GPT-5 model in a Microsoft Foundry project** and test it in the chat playground to observe its default tone and behavior.

- **Fine-tune the model** on a small dataset of example conversations that define a specific tone and behavioral constraints (for example, a travel assistant that must not book flights or hotels).

- **Review fine-tuning metrics and training data**, then deploy the fine-tuned model and compare its responses against the base model.

- **Clean up all deployed Azure resources** across each lab to avoid unnecessary cloud costs.

## Pre-requisites

Participants should have:

- A **GitHub account**, required to open GitHub Codespaces and deploy the Multi-Agent accelerator and the AI Red Teaming knowledge assistant (sign up at https://github.com/signup if you don't already have one).

- Access to the **Azure Portal** with an assigned Azure subscription and resource group.

- Access to the **Microsoft Foundry portal** (ai.azure.com) for model deployment, fine-tuning, agent evaluation, and red teaming.

- Basic familiarity with running commands in a terminal, including the Azure Developer CLI (`azd`), Python, and `pytest`, since both accelerator deployments and the evaluation/red-teaming tests run from the command line.

- Basic familiarity with core AI agent concepts — agents, tools, and multi-agent orchestration — as well as evaluation and red-teaming concepts such as evaluators, attack strategies, and risk taxonomies.

- Basic familiarity with model fine-tuning concepts, such as training data format, supervised fine-tuning, and comparing base versus fine-tuned model behavior.

## Explanation of Components

The architecture across this lab's three usecases involves the following key components:

1. **GitHub Codespaces & Azure Developer CLI (azd):** The development environment used to authenticate, provision, and deploy both the Multi-Agent Custom Automation accelerator (Usecase 3) and the document-aware knowledge assistant (Usecase 4) to Azure with a few `azd` commands.

2. **Microsoft Foundry & Foundry project:** Hosts the deployed agents and models across all three usecases — the multi-agent orchestration team, the document-aware knowledge assistant, and the base and fine-tuned GPT-5 models.

3. **Azure Container Apps & Container Registry:** Run the deployed web front-ends — the multi-agent orchestration UI in Usecase 3, and the document-aware chat assistant in Usecase 4.

4. **Azure Cosmos DB:** Stores agent and session state for both deployed accelerator solutions.

5. **Azure AI Search:** Indexes the sample business documents and knowledge base content so agents can retrieve grounded, citation-supported answers in Usecase 3 and Usecase 4.

6. **Azure Storage account:** Holds the sample datasets and team configuration files uploaded during post-deployment (Usecase 3) and the internal documents used for retrieval (Usecase 4).

7. **Application Insights & Log Analytics Workspace:** Capture tracing and telemetry for the deployed knowledge assistant, enabling console traces, agent traces in Foundry, and continuous evaluation in production (Usecase 4).

8. **Specialized agent teams (HR Helper, Technical Support, Proxy, and others):** Collaborate within the Multi-Agent accelerator to generate and execute cross-department task plans — such as onboarding a new employee — with human-in-the-loop clarification and approval (Usecase 3).

9. **Foundry built-in evaluators:** Score the deployed knowledge assistant on intent resolution, tool call accuracy, task adherence, and content safety (Usecase 4).

10. **AI Red Teaming Agent:** Automatically generates adversarial prompts across configurable attack strategies and risk taxonomies — with no test dataset or adversarial LLM required — to probe the deployed agent for safety and security gaps (Usecase 4).

11. **Microsoft Foundry model catalog & fine-tuning job:** Deploys a base GPT-5 model and runs a supervised fine-tuning job against a curated JSONL training file, producing a tone- and behavior-constrained travel-assistant model that can be deployed and compared against the base model (Usecase 5).

## Getting Started with the lab

Welcome to your Azure AI Agents Workshop, Let's begin by making the most of this experience.

## Accessing Your Lab Environment

Once you're ready to dive in, your virtual machine and **Guide** will be right at your fingertips within your web browser.

![Access Your VM and Lab Guide](media/guideee.png)

## Lab Guide Zoom In/Zoom Out

To adjust the zoom level for the environment page, click the **A↕ : 100%** icon located next to the timer in the lab environment.

![](./media/zum.png)

## Virtual Machine & Lab Guide

Your virtual machine is your workhorse throughout the workshop. The lab guide is your roadmap to success.

## Exploring Your Lab Resources

To get a better understanding of your lab resources and credentials, navigate to the **Environment** tab.

![Explore Lab Resources](media/envtab.png)

## Utilizing the Split Window Feature

For convenience, you can open the lab guide in a separate window by selecting the **Split Window** button from the Top right corner.

![Use the Split Window Feature](media/splittt.png)

## Managing Your Virtual Machine

Feel free to **Start, Stop, or Restart (2)** your virtual machine as needed from the **Resources (1)** tab. Your experience is in your hands!

![Manage Your Virtual Machine](media/VMSS.png)

## Let's Get Started with Azure Portal

1. On your virtual machine, click on the Azure Portal icon.

   ![](media/GettingStarted-07.png)

2. You'll see the **Sign into Microsoft Azure** tab. Here, enter your **credentials (1)** and select **Next (2)**:

   - **Email/Username:** <inject key="AzureAdUserEmail"></inject>

     ![Enter Your Username](media/odlusr.png)

3. Next, provide your **password (1)** and select **Sign In (2)**:

   - **Password:** <inject key="AzureAdUserPassword"></inject>

     ![Enter Your Password](../media/password.png)

      >**Note:** If you see **Temporary Access pass**, enter the the password and select **Sign In (2)**:

       - Enter **Temporary Access Pass:** <inject key="AzureAdUserPassword"></inject> **(1)**

          ![](media/image.png)

4. If **Action required** pop-up window appears, click on **Ask later**.
5. If prompted to **stay signed in**, you can click **No**.

   ![](media/GettingStarted-04.png)

6. If a **Welcome to Microsoft Azure** pop-up window appears, simply click **"Cancel"** to skip the tour.

## Steps to Proceed with MFA Setup if "Ask Later" Option is Not Visible

1. At the **"More information required"** prompt, select **Next**.

1. On the **"Keep your account secure"** page, select **Next** twice.

1. **Note:** If you don’t have the Microsoft Authenticator app installed on your mobile device:

   - Open **Google Play Store** (Android) or **App Store** (iOS).
   - Search for **Microsoft Authenticator** and tap **Install**.
   - Open the **Microsoft Authenticator** app, select **Add account**, then choose **Work or school account**.

1. A **QR code** will be displayed on your computer screen.

1. In the Authenticator app, select **Scan a QR code** and scan the code displayed on your screen.

1. After scanning, click **Next** to proceed.

1. On your phone, enter the number shown on your computer screen in the Authenticator app and select **Next**.
1. If prompted to stay signed in, you can click "No."

1. If a **Welcome to Microsoft Azure** pop-up window appears, simply click "Maybe Later" to skip the tour.

## Support Contact

The CloudLabs support team is available 24/7, 365 days a year, via email and live chat to ensure seamless assistance at any time. We offer dedicated support channels tailored specifically for both learners and instructors, ensuring that all your needs are promptly and efficiently addressed.

Learner Support Contacts:

- Email Support: [cloudlabs-support@spektrasystems.com](mailto:cloudlabs-support@spektrasystems.com)
- Live Chat Support: https://cloudlabs.ai/labs-support

Click **Next** from the bottom right corner to embark on your Lab journey!

![Start Your Azure Journey](../media/PageNo.png)

Now you're all set to explore the powerful world of technology. Feel free to reach out if you have any questions along the way. Enjoy your workshop!
