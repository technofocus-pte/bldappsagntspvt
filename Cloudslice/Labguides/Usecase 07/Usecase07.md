# Use case 07 - Moderate text and images with content safety in Azure AI Content Safety Studio

**Introduction**

Azure AI Content Safety detects harmful user-generated and AI-generated
content in applications and services. Azure AI Content Safety includes
text and image APIs that allow you to detect material that is harmful.
Microsoft Azure also has an interactive Content Safety Studio that
allows you to view, explore and try out sample code for detecting
harmful content across different modalities.

Content filtering software can help your app comply with regulations or
maintain the intended environment for your users.

[Azure AI Content Safety
Studio](https://contentsafety.cognitive.azure.com/) is an online tool
designed to handle potentially offensive, risky, or undesirable content
using cutting-edge content moderation ML models. It provides templates
and customized workflows, enabling users to choose and build their own
content moderation system. Users can upload their own content or try it
out with the provided sample content.

In Content Safety Studio, the following Azure AI Content Safety service
features are available:

- **Moderate Text Content**: With the text moderation tool, you can
  easily run tests on text content. Whether you want to test a single
  sentence or an entire dataset, this tool offers a user-friendly
  interface that lets you assess the test results directly in the
  portal.

- **Moderate Image Content**: With the image moderation tool, you can
  easily run tests on images to ensure that they meet your content
  standards.

- **Monitor Online Activity**: The powerful monitoring page allows you
  to easily track your moderation API usage and trends across different
  modalities. With this feature, you can access detailed response
  information, including category and severity distribution, latency,
  error, and blocklist detection. This information provides you with a
  complete overview of your content moderation performance, enabling you
  to optimize your workflow and ensure that your content is always
  moderated to your exact specifications.

**Objectives**

- To deploy an Azure AI Content Safety resource.

- To create Azure AI Resource and Explore Content Safety.

- To set up Azure AI resource in Azure AI Studio and explore content
  safety features, emphasizing text and image moderation.

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

![](./media/image1.png)

3.  Ensure that **Enhanced Mode** is enabled in the Tools section before
    proceeding with the lab tasks

> ![](./media/image2.png)

\[!Alert\] **Important:** Make sure you create all your resources under
this Resource group

## Task 1: Create Azure AI Content Safety resource

1.  Open your browser, navigate to the address bar, type or paste the
    following URL: +++<https://portal.azure.com/+++> then press
    the **Enter** button.

![](./media/image3.png)

2.  In the **Sign in** window, enter the **Username** and click on
    the **Next** button.

![](./media/image4.png)

3.  Then, enter the password and click on the **Sign in** button.

![](./media/image5.png)

4.  In **Stay signed in?** window, click on the **Yes** button.

![](./media/image6.png)

5.  In Azure portal, search box, type +++Foundry+++ and then click on
    the Microsoft Foundry.

![](./media/image7.png)

6.  In Microsoft Foundry page, select **Content safety**

![](./media/image8.png)

7.  Click on **+Create**

![](./media/image9.png)

8.  In the **Create Azure OpenAI** window, under the **Basics** tab,
    enter the following details and click on
    the **Review+create** button.

[TABLE]

9.  ![](./media/image10.png)

10. In the **Review+submit** tab, once the Validation is Passed, click
    on the **Create** button.

![](./media/image11.png)

11. Wait for the deployment to complete. The deployment will take around
    2-3 minutes.

12. Once the deployment completes, select **Go to resource**.

13. Select **Access control (IAM)** on the left hand panel.

14. Select **Add role assignment**.

> ![](./media/image12.png)

15. Search for !!**Cognitive Services User!!**, select the **Cognitive
    Services User** role, and then select **Next**.

> ![](./media/image13.png)
>
> ![](./media/image14.png)

16. Select **User, group, or service principal**.

17. Select **+ Select members**.

> ![](./media/image15.png)

18. In the **Select members** pane, search for your user and select it.

> ![](./media/image16.png)

19. Select **Review + assign**.

> ![](./media/image17.png)
>
> ![](./media/image18.png)
>
> ![](./media/image19.png)

## Task 2: Analyze text content

1.  Open your browser, navigate to the address bar, type or paste the
    following
    URL:+++<https://contentsafety.cognitive.azure.com/+++> then press
    the Enter button.

2.  Select **Sign In** on the top right of menu bar.

3.  Select the **@lab.CloudPortalCredential(User1).Username** account.

4.  In the **Content Safety** page, navigate to **Moderate text
    content** tile, click on **Try it
    out** link. ![](./media/image20.png)

5.  Select Choose a different resource. ![](./media/image21.png)

6.  In **Settings** pane,
    select [**AOAI-ContentSafety@lab.LabInstance.Id**](mailto:AOAI-ContentSafety@lab.LabInstance.Id) and
    click on **Use resource**.

![](./media/image22.png)

7.  In the **Content Safety** page, navigate to **Moderate text
    content** tile, click on **Try it out** link.

![](./media/image20.png)

8.  Under **Run a simple test** tab, select **Safe content** tile as
    shown in the below image.

![](./media/image23.png)

9.  Optionally, you can use slide controls in the **Configure
    filters** tab to modify the allowed or prohibited severity levels
    for each category. Then, click on **Run test** button.

![](./media/image24.png)

![](./media/image25.png)

10. Scroll down to view the results. The service returns all the
    categories that were detected, the severity level for each (0-Safe,
    2-Low, 4-Medium, 6-High), and a
    binary **Allowed** or **Reject** judgment. The result is based on
    the filters that you’ve configured.

![](./media/image26.png)

11. Scroll down and click on **View Code** button as shown in the below
    image to view and copy the sample code, which includes configuration
    for severity filtering, blocklists, and moderation functions. You
    can then deploy the code on your end.

![](./media/image27.png)

![](./media/image28.png)

**Task 3: Detect user input attacks**

1.  Go back to the **Content Safety Studio**

![](./media/image29.png)

2.  In the **Content Safety** page, under **Explore safety solutions for
    Gen-AI** navigate to **Prompt Shields** tile, click on **Try it
    out** link.

![](./media/image30.png)

3.  Under **Set up sample** tab, select **Safe content** tile as shown
    in the below image.

![](./media/image31.png)

4.  Optionally, you can use slide controls in the **Prompt shields** tab
    to modify the allowed or prohibited severity levels for each
    category. Then, click on **Run test** button.

![](./media/image32.png)

5.  Scroll down and click on **View Code** button as shown in the below
    image to view and copy the sample code, which includes configuration
    for severity filtering, blocklists, and moderation functions. You
    can then deploy the code on your end.

![](./media/image33.png)

![](./media/image34.png)

6.  Under **Set up sample** tab, select **User prompt attack
    content** tile and click on **Run test** as shown in the below
    image.

![](./media/image35.png)

![](./media/image36.png)

**Task 4: Analyze image content**

1.  Under the Prompt Shields pane , click on **Back**

![](./media/image37.png)

2.  In **Content Safety** page, navigate to **Moderate image
    content** tile and click on **Try it out** link.

![](./media/image38.png)

3.  Under select a sample or upload your own section, navigate and click
    on **Browse for a file** link.

![](./media/image39.png)

\[!Note\]: The maximum size for image submissions is 4 MB, and image
dimensions must be between 50 x 50 pixels and 2,048 x 2,048 pixels.
Images can be in JPEG, PNG, GIF, BMP, TIFF, or WEBP formats.

4.  Navigate to **C:\Lab Files** location and select **car-accident
    image**, then click on **Open** button.

![](./media/image40.png)

5.  Optionally, you can use slide controls in the **Configure
    filters** tab to modify the allowed or prohibited severity levels
    for each category.

6.  Click on **Run test** button.

![](./media/image41.png)

7.  Scroll down to view the results of the test. The service returns all
    the categories that were detected, the severity level for each
    (0-Safe, 2-Low, 4-Medium, 6-High), and a
    binary **Accept** or **Reject** judgment. The result is based on the
    filters that you’ve configured

![](./media/image42.png)

8.  Scroll down and click on **View Code** button as shown in the below
    image to view and copy the sample code, which includes configuration
    for severity filtering, blocklists, and moderation functions. You
    can then deploy the code on your end.

![](./media/image43.png)

![](./media/image44.png)

**Task 5: Delete the resource group**

1.  Navigate to Azure portal home page, type **Resource groups** in the
    Azure portal search bar, navigate and click on **Resource
    groups** under **Services**.

![](./media/image45.png)

2.  Select **Resource Group**.

3.  Select **@lab.CloudResourceGroup(ResourceGroup1).Name**.

4.  Select all the reosources
    in **@lab.CloudResourceGroup(ResourceGroup1).Name**.

5.  Select **Delete resource group**.

6.  Enter <+++@lab.CloudResourceGroup>(ResourceGroup1).Name+++ in the
    text box to confirm deletion.

7.  Select **Delete**.
