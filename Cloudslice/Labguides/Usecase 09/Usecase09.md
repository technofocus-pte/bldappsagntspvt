# Usecase 05: Deploying and Evaluating Fine-Tuned GPT Models in Azure AI Projects

**Scenario**

You work at a travel-agency (or a company that builds travel-planning
tools). You are building a conversational chat application (a “travel
assistant”) that helps users plan holidays: suggest destinations,
activities, cultural info, weather, visa requirements, etc. You want the
assistant to always speak in a **friendly, inspiring, conversational
tone**, and to **avoid** giving services like booking flights, hotels or
rental cars.

You have access to a pretrained, general-purpose LLM (e.g. gpt-5 via
Azure AI Foundry). But the base model’s responses tend to be generic and
inconsistent in tone. So — instead of relying on prompt-engineering
alone — you decide to **fine-tune** the model on a small dataset of
example chats that reflect exactly how you want the assistant to behave
and respond.

**Introduction**

Large language models (LLMs) can generate high-quality responses using
prompts alone, but achieving consistent tone, behavior, and
domain-specific guidance often requires more than prompt engineering.
Fine-tuning enables you to adapt a powerful base model—such as GPT-4o—to
your unique application needs by training it on example conversations
that demonstrate the tone, style, and constraints you expect.

In this use case, you work for a travel-planning company building a
conversational assistant that offers friendly, inspiring travel
suggestions while avoiding tasks like booking flights or hotels. Through
Microsoft Foundry, you will deploy a base model, fine-tune it using
curated training examples, evaluate its behavior, and compare
performance between the base and fine-tuned versions. This hands-on
exercise demonstrates how fine-tuning creates more reliable, tailored
conversational experiences for real-world applications.

**Objectives**

- Deploy a base GPT-5 model within a Microsoft Foundry project for
  initial testing.

- Fine-tune the model using a small dataset of example conversations
  that define the desired travel-assistant behavior.

- Compare outputs from the base model and the fine-tuned model to
  evaluate improvements in tone, consistency, and constraints.

- Deploy the fine-tuned model and test it in the Azure AI chat
  playground.

- Review fine-tuning metrics and training data to understand how the
  model learns target behaviors.

- Clean up deployed Azure resources to prevent unnecessary cloud costs.

## Task 1: Deploy a model in a Microsoft Foundry project

1.  Open a browser go to !!https://ai.azure.com!! and sign in with
    your cloud slice account below.

> Username: <!!@lab.CloudPortalCredential>(User1).Username!!
>
> Password: <!!@lab.CloudPortalCredential>(User1). *TAP*!!
>
> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image1.png)
>
> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image2.png)
>
> ![A login box with a red box and blue box with text AI-generated
> content may be incorrect.](./media/image3.png)
>
> ![A screenshot of a computer error AI-generated content may be
> incorrect.](./media/image4.png)
>
> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image5.png)

2.  If it is not already enabled, in the tool bar at the top of the
    page, enable the **New Foundry** option.

> ![](./media/image6.png)

3.  Then, if prompted, create a new project with a unique name;
    expanding the Advanced options area to specify the following
    settings for your project:

- Foundry resource: Use the default name for your resource (usually
  {project_name}-resource)

- Subscription: Your Azure subscription

- Resource group: Create or select a resource group

- Region: Select one of the following regions:\*

&nbsp;

- North Central US

- Sweden Central

> ![](./media/image7.png)
>
> ![](./media/image8.png)

4.  Wait for your project to be created. Then view its home page.

> ![](./media/image9.png)

5.  Select **Discover**

> ![](./media/image10.png)

6.  Now you’re ready to explore models. On the **Discover** page, select
    the **Models** tab to view the Microsoft Foundry model catalog.

7.  In the **Model Catalog**, search for **gpt-5**, then select the
    **gpt-5** model.

> ![](./media/image11.png)

8.  Review the model card, and then deploy it using the **default
    settings**.

> ![](./media/image12.png)

9.  When the model has been deployed, it will open in the model
    playground.

> ![](./media/image13.png)

## Task 2: Fine-tune a model

Because fine-tuning a model takes some time to complete, you’ll start
the fine-tuning job now and come back to it after exploring the base
gpt-5 model you already deployed.

1.  In the Foundry portal, while viewing the model playground, left
    navigation pane, select Fine-tune.

> ![](./media/image14.png)

2.  Select the **Start fine-tuning** button at the upper right, and then
    configure the fine-tuning job with the following settings:

    - **Base model**: Select **gpt-5 or gpt 4.1**

    - **Customization method**: Supervised

    - **Training type**: Standard

    - **Training data**: *Select the option to **Add training data** and
      upload and apply the* **travel-finetune-hotel.jsonl** *file
      located in **C:\Labfiles** location*

    - **Suffix**: ft-travel

    - **Automatically deploy model after job completion**: Selected

    - **Deployment type**: Developer

    - *Leave the remaining hyperparameters at their defaults*

> ![](./media/image15.png)
>
> ![](./media/image16.png)
>
> ![](./media/image17.png)
>
> ![](./media/image18.png)

3.  Select **Submit** to start the fine-tuning job. It may take some
    time to complete. ![](./media/image19.png)

> ![](./media/image20.png)
>
> **Note**: Fine-tuning and deployment can take a significant amount of
> time (60 minutes or longer), so you may need to check back
> periodically. You can see more details of the progress so far by
> selecting the fine-tuning job and viewing its **Monitor** tab.
>
> ![](./media/image21.png)
>
> ![](./media/image22.png)

## Task 3: Chat with a base model

1.  In the left pane, select **Deployments** and then select
    the **gpt-5** base model you deployed previously.

> ![](./media/image23.png)

2.  In the chat pane, enter the prompt !!**What can you do?!!** and view
    the response.

> ![](./media/image24.png)
>
> The answers may be fairly generic. Remember we want to create a chat
> application that inspires people to travel.
>
> ![](./media/image25.png)

3.  Change the model **Instructions** to the following prompt:

> !!You are an AI assistant that helps people plan their travel.!!
>
> ![](./media/image26.png)

4.  In the chat window, enter the query !!**What can you do?!!** again,
    and view the response.

> ![](./media/image27.png)
>
> As a response, the assistant may tell you that it can help you book
> flights, hotels and rental cars for your trip. You want to avoid this
> behavior.
>
> ![](./media/image28.png)

5.  In the **Instructions** field, enter a new prompt:

> **You are an AI travel assistant that helps people plan their trips.
> Your objective is to offer support for travel-related inquiries, such
> as visa requirements, weather forecasts, local attractions, and
> cultural norms.**
>
> **You should not provide any hotel, flight, rental car or restaurant
> recommendations.**
>
> **Ask engaging questions to help someone plan their trip and think
> about what they want to do on their holiday.**
>
> ![](./media/image29.png)

6.  Continue testing the model to review its behavior. For example, ask
    the following questions and note the model’s answers, paying
    particular attention to the tone and writing style that the model
    uses to respond:

> **!!Where in Rome should I stay?!!**
>
> ![](./media/image30.png)
>
> ![](./media/image31.png)
>
> !!I'm mostly there for the food. Where should I stay to be within
> walking distance of affordable restaurants?!!
>
> ![](./media/image32.png)
>
> ![](./media/image33.png)
>
> **!!What are some local delicacies I should try?!!**
>
> ![](./media/image34.png)
>
> !! When is the best time of year to visit in terms of the weather?!!
>
> ![](./media/image35.png)
>
> !! What's the best way to get around the city?!!
>
> ![](./media/image36.png)

## Task 4: Review the training file

The base model seems to work well enough, but you may be looking for a
particular conversational style from your generative AI app. The
training data used for fine-tuning offers you the chance to create
explicit examples of the kinds of response you want.

1.  Open the JSONL file you downloaded previously (you can open it in
    any text editor)

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image37.png)

2.  Examine the list of the JSON documents in the training data file.
    The first one should be similar to this (formatted for readability):

code

{"messages": \[

{"role": "system", "content": "You are an AI travel assistant that helps
people plan their trips. Your objective is to offer support for
travel-related inquiries, such as visa requirements, weather forecasts,
local attractions, and cultural norms. You should not provide any hotel,
flight, rental car or restaurant recommendations. Ask engaging questions
to help someone plan their trip and think about what they want to do on
their holiday."},

{"role": "user", "content": "What's a must-see in Paris?"},

{"role": "assistant", "content": "Oh la la! You simply must twirl around
the Eiffel Tower and snap a chic selfie! After that, consider visiting
the Louvre Museum to see the Mona Lisa and other masterpieces. What type
of attractions are you most interested in?"}

\]}

![A close up of a text AI-generated content may be
incorrect.](./media/image38.png)

Each example interaction in the list includes the same system message
you tested with the base model, a user prompt related to a travel query,
and a response. The style of the responses in the training data will
help the fine-tuned model learn how it should respond.

## Task 5: Deploy the fine-tuned model

When fine-tuning has successfully completed, you can deploy the
fine-tuned model.

1.  Navigate to the **Fine-tuning** page under **Optimize** to find your
    fine-tuning job and its status. If it’s still running, you can opt
    to continue chatting with your deployed base model or take a break.
    If it’s completed, you can continue.

**Tip**: Use the **Refresh** button in the fine-tuning page to refresh
the view. If the fine-tuning job disappears entirely, refresh the page
in the browser.

![](./media/image39.png)

2.  Select the fine-tuning job link to open its details page. Then,
    select the **Logs**tab and explore the fine-tune metrics.

> ![](./media/image40.png)
>
> ![](./media/image41.png)

3.  In the **Models** section, select the **gpt-5** model, click
    **Deploy**, and then choose **Deploy a fine-tuned model** from the
    drop-down menu.

> ![](./media/image42.png)

4.  Click on **Deploy**

> ![](./media/image43.png)
>
> ![](./media/image44.png)
>
> ![](./media/image45.png)

5.  Select the fine-tuned model to open it in the model playground.

> ![](./media/image46.png)

6.  Update the **Instructions** to be the same as you tested with the
    base model:

**You are an AI travel assistant that helps people plan their trips.
Your objective is to offer support for travel-related inquiries, such as
visa requirements, weather forecasts, local attractions, and cultural
norms.**

**You should not provide any hotel, flight, rental car or restaurant
recommendations.**

**Ask engaging questions to help someone plan their trip and think about
what they want to do on their holiday.**

> ![](./media/image47.png)

7.  Test your fine-tuned model to assess whether its behavior is more
    consistent than the base model. For example, ask the following
    questions again and explore the model’s answers:

> !!**Where in Rome should I stay?**!!
>
> ![](./media/image48.png)
>
> ![](./media/image49.png)
>
> !!I'm mostly there for the food. Where should I stay to be within
> walking distance of affordable restaurants?!!
>
> ![](./media/image50.png)
>
> !!What are some local delicacies I should try?!!
>
> ![](./media/image51.png)
>
> !!When is the best time of year to visit in terms of the weather?!!
>
> ![](./media/image52.png)
>
> !!What's the best way to get around the city?!!
>
> ![](./media/image53.png)

## Task 6: **Delete resources**

If you’ve finished exploring Foundry, you should delete the resources
you’ve created to avoid unnecessary Azure costs.

1.  In the Azure portal, on the **Home** page, select **Resource
    groups**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image54.png)

2.  Carefully select all resources that you’ve created.

> ![A screenshot of a computer AI-generated content may be
> incorrect.](./media/image55.png)

3.  In the Resource group page, navigate to the command bar and click
    on **Delete**.

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image56.png)

4.  In the **Delete Resources** pane that appears on the right side,
    enter the **delete** and click on **Delete** button.

![A screenshot of a screenshot of a computer AI-generated content may be
incorrect.](./media/image57.png)

![A screenshot of a computer AI-generated content may be
incorrect.](./media/image58.png)

**Summary**

In this usecase, you deployed, fine-tuned, and evaluated a custom GPT
model using Microsoft Foundry. You began by experimenting with a base
GPT-4o model to observe its default behavior and limitations. After
preparing and uploading a training dataset, you fine-tuned the model to
reflect the friendly, inspirational tone needed for a travel-planning
assistant—while ensuring it avoids restricted tasks like booking flights
or hotels. Once deployed, you compared the fine-tuned model’s responses
with the base model to confirm improvements in consistency, personality,
and domain alignment.

By completing this exercise, you gained practical experience in
fine-tuning LLMs, deploying them in Azure AI projects, and validating
their behavior—an essential skill for building tailored,
production-ready conversational applications
