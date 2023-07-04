![image](media/OpenAI_DDiB.png)

# Azure OpenAI Service DREAM Demo

Azure OpenAI Service offers large-scale generative AI models with a deep understanding of language to enable new reasoning and comprehension capabilities for building cutting-edge applications. These models can be applied to a variety of use cases, such as writing assistance, code generation, and reasoning over data. You can also detect and mitigate harmful use of AI with built-in responsible AI and access enterprise-grade Azure security.

In this demo, you will see the Azure OpenAI Service based assistant for Enterprise Data in action. This will be followed by an AI - generated Social Media Campaign Recommendation demo using DALL-E 2, Florence and Azure OpenAI Service. And finally, you will see text summarization in a contact center scenario using Azure OpenAI with Speech Service.

----

## Products and Technologies showcased:

**1.	Azure OpenAI Service**

- Azure OpenAI Service provides REST API access to OpenAI's powerful language models. These models can be easily adapted to your specific task including but not limited to content generation, summarization, semantic search, and natural language to code translation.
    
- The models used by Azure OpenAI use natural language instructions and examples provided during the generation call to identify the task being asked and skill required.
    
- With Azure OpenAI, customers get the security capabilities of Microsoft Azure while running the same models as OpenAI. Azure OpenAI offers private networking, regional availability, and responsible AI content filtering.

**2.	DALL.E 2**

- DALL·E 2 is an AI system that can create original, realistic images and art from a text description in natural language. It can combine concepts, attributes, and styles. 
    
- DALL·E 2 can make realistic edits to existing images from a natural language caption. It can add and remove elements while taking shadows, reflections, and textures into account. It can also create different variations of it inspired by the original.

**3.	Project Florence (AI)**
    
- Project Florence is a Microsoft AI Cognitive Services initiative, to advance the state-of-the-art computer vision technologies and develop the next generation framework for visual recognition.

----

## Pre-requisites

* [Azure Developer CLI](https://aka.ms/azure-dev/install)
* [Python 3+](https://www.python.org/downloads/)
  * **Important**: Python and the pip package manager must be in the path in Windows for the setup scripts to work.
  * **Important**: Ensure you can run `python --version` from console. On Ubuntu, you might need to run `sudo apt install python-is-python3` to link `python` to `python3`.
* [Node.js](https://nodejs.org/en/download/)
* [Git](https://git-scm.com/downloads)
* [Powershell 7+ (pwsh)](https://github.com/powershell/powershell) - For Windows users only.
  * **Important**: Ensure you can run `pwsh.exe` from a PowerShell command. If this fails, you likely need to upgrade PowerShell.
* [Clone the repository to your local](https://dev.azure.com/daidemos/Microsoft%20Data%20and%20AI%20DREAM%20Demos%20and%20DDiB/_git/DreamDemoInABox?version=GBopen-ai-ddib&anchor=execution-through-webapp-scenario-1&path=/artifacts)
* [Visual Studio Code](https://code.visualstudio.com/download)
* [Azure Account](https://portal.azure.com/)
* [Postman](https://www.postman.com/downloads/)


>**NOTE:** Your Azure Account must have `Microsoft.Authorization/roleAssignments/write` permissions, such as [User Access Administrator](https://learn.microsoft.com/azure/role-based-access-control/built-in-roles#user-access-administrator) or [Owner](https://learn.microsoft.com/azure/role-based-access-control/built-in-roles#owner).  

>**Note:** If you see any pop-up on VS Code to download extensions for executing the Python function apps, make sure you download and install it before executing the code.

----

## Running this repo

There are two ways to execute this demo:

-   [Method 1 - Executing the code on local machine in Python using Postman](#method-1-executing-the-code-on-local-machine-in-python-using-postman)

    -   [PDF INDEXER](#pdf-indexer)
    -   [Search Horizontal](#search-horizontal)
    -   [Campaign Generation](#campaign-generation)
    -   [Recommend Images](#recommend-images)
    -   [Regenerate Images with DALL-E 2](#regenerate-images-with-dall-e-2)

-   [Method 2 - Executing the demo through demo web app](#method-2-executing-the-demo-through-demo-web-app)

    -   [Scenario 1 - Azure OpenAI Service and Azure Cognitive Search powered chatbot for Enterprise data](#scenario-1-azure-openai-service-and-azure-cognitive-search-powered-chatbot-for-enterprise-data)
        -   [Steps to configure function app used in Scenario 1](#steps-to-configure-function-app-used-in-scenario-1)    

    -   [Scenario 2 - Social Media Campaign and Product Recommendation](#scenario-2-social-media-campaign-and-product-recommendation)
        -   [Steps to configure function app used in Scenario 2](#steps-to-configure-function-app-used-in-scenario-2) 

    -   [Scenario 3 - Azure OpenAI with Speech Service](#scenario-3-azure-openai-with-speech-service)
        -   [Steps to configure app service used in scenario 3](#steps-to-configure-app-service-used-in-scenario-3) 

-   [Appendix](#appendix)
    -   [Training the Knowledge Base using Postman and Python](#training-the-knowledge-base-using-postman-and-python)
----

## Method 1 - Executing the code on local machine in Python using Postman

### Steps to execute the code on a local machine to test the function_app.py:

1. **Start** VS Code on your loacal machine. The following screen will appear.
    ![VS Code landing page](media/vs_code_landing_page.png)

2. **Open** the locally cloned repository (mentioned in pre-requisites) in VS Code. You should be able to see all the necessary files as given in the screenshot below. Make sure that you extract all the zipped folder marked 3 in the screenshot. In the next steps, we will execute function app for all these folders one- by -one.
    
    ![Artifacts Folder Structure](media/folder_structure.png)

----

## PDF INDEXER
This function-app indexes an uploaded PDF file into the number of pages in the PDF.

### Steps to generate POST URL for 'PDF Indexer' function app:

1. Under the **func-pdf-indexer** folder, select function_app.py.
   
    ![PDF Indexer explorer](media/select_function_app.png)

2. **Open** a new terminal. In the next command line, **execute** the following code for the function to start.

    ```
    func start
    ```

    ![Start the function](media/func_start.png)

3. Once the execution is complete, the function will give the following URLs to perform DELETE and INDEXING operations. **Copy** the 'pdfindexer' URL for further use.

    ![URLs](media/urls_pdf_indexer.png)


4. **Open** the Postman application, then **select** the "New" button to create a new request.

    ![Select new request.](media/select_new_request.png)

5. In the pop up window, **select** HTTP request.

    ![Select HTTP request.](media/select_http.png)

6.  In the new request page, **select** "POST" method from the dropdown as shown in the screenshot.

   ![Select POST request.](media/select_post1.png)

7. **Paste** the 'pdfindexer' URL copied earlier from the VS Code terminal in the text field next to POST. (Copied in step numner 3). 
8. **Select** the Body tab to add other parameters.

    ![Paste POST URL.](media/post_url.png)

9. **Select** “form-data”.
10. **Provide** the required key-value pair as given below.

| Key | Value |
|--------------|-------------|
| index_name | prod-responsibleai-search |
| container_name |knowledge-base-responsibleai |
| pdf | [Select the PDF 'Microsoft-Responsible-AI-Standard-v2-General-Requirements.pdf' shared with you in the package] |

11. Click **Send**.

 ![Fill in form-data](media/form_body.png)

12.  **View** the response.

 ![Response for PDF Indexer](media/response_pdf.png)


 **ENVIRONMENT VARIABLES (PDF indexer):**

| APP Setting  | Value  | Note |
|--------------|-------------|---------------|
| AZURE_SEARCH_SERVICE_NAME |YOUR_AZURE_SEARCH_SERVICE_NAME   | Your Azure Cognitive Search service name. Fetch it from the Azure Portal.|
| AZURE_SEARCH_KEY		    | YOUR_AZURE_SEARCH_KEY | Your Azure Cognitive Search key. Fetch it from the Azure Portal|
| AZURE_STORAGE_ACCOUNT_KEY     | YOUR_AZURE_STORAGE_ACCOUNT_KEY   | Your Azure Storage Account Key. Fetch it from the Azure Portal |
| AZURE_STORAGE_ACCOUNT_NAME |  YOUR_AZURE_STORAGE_ACCOUNT_NAME | Your Azure Storage Account Name. Fetch it from the Azure Storage Account Name |
| FORM_RECOGNIZER_KEY  | YOUR_FORM_RECOGNIZER_KEY         | Azure Form Recognizer Key, Fetch it from the Azure Portal | 

> **Note:**  Using the code snippet below, you can test the environment variables by configuring them locally inside pdfindexer.py. Please add the name of the services and keys after the word “or” for the respective variables.

```
search_service_name = os.environ.get("SEARCH_SERVICE_NAME") or "" 

search_service_key = os.environ.get("SEARCH_SERVICE_KEY") or "" 

storage_account_key = os.environ.get("STORAGE_ACCOUNT_KEY") or "" 

storage_account_name = os.environ.get("STORAGE_ACCOUNT_NAME") or "" 

form_recognizer_key = os.environ.get("FORM_RECOGNIZER_KEY") or "" 

FormRecognizerService = os.environ.get("FormRecognizerService") or "" 

form_recognizer_header = os.environ.get("form_recognizer_header") or "" 
```

>**Note:** The other function apps in this demo can be tested in a similar way by only changing the URL and form-data body in the POST request.
 ----
## Search Horizontal

 This function app is used to search the response to any custom query related to the pdf indexed by the function pdfindexer function app.4
 ** Path to build:** 'artifacts/binaries/func-search-horizontal.zip' 

### Steps to generate POST URL for 'Search Horizontal' function app:

1. Under the **func-search-horizontal** folder, **select** function_app.py.

![PDF Indexer explorer](media/select_function_app.png)

2. **Repeat steps** from step number 2 to step number 12 for func-search-horizontal in the similar way as performed for PDF Indexer.

3. Use the following values for POSTMAN requests:

**POST URL:**
```
http://localhost:7071/api/chat
```

**BODY > raw:**
```
 {
    "approach": "rrr",
    "enableExternalDomain": "False",
    "history":
     [
        {
            "user": (str) —>YOUR QUESTION TO CHATBOT,
        }
    ]
}
```

**Return:**
```
{
    **"data_points"**: [],
    "answer": "Ensuring that AI systems align with human values and ethical principles is a complex and ongoing process. Here are some steps that can be taken:\n\n1. Develop ethical guidelines: Organizations and governments can develop ethical guidelines for the development and use of AI systems. These guidelines should be based on human values and principles, such as fairness, transparency, accountability, and privacy.\n\n2. Incorporate ethical considerations into the design process: Ethical considerations should be incorporated into the design process of AI systems. This includes considering the potential impact of the system on different groups of people and ensuring that the system is designed to be fair and unbiased.\n\n3. Test and evaluate AI systems: AI systems should be tested and evaluated to ensure that they are aligned with ethical principles. This includes testing the system for bias and ensuring that it is transparent and accountable.\n\n4. Involve diverse stakeholders: Diverse stakeholders, including experts in ethics, social scientists, and representatives from different communities, should be involved in the development and deployment of AI systems. This can help ensure that the systems are aligned with human values and ethical principles.\n\n5. Regularly review and update ethical guidelines: Ethical guidelines should be regularly reviewed and updated to ensure that they remain relevant and effective in guiding the development and use of AI systems.",
    "thoughts": ""
}
```

**Example raw-data when searching from the knowledge base:**
```
{
    "approach": "rrr",
    "enableExternalDomain": "False",
    "history":
     [
        {
            "user": "How can we ensure AI systems align with human values and ethical principles?"
        }
    ]
}
```

**Example raw-data when searching from any other uploaded documents:**
```
{
    "history": 
    [
        {
            "user": "Provide approximate nutritional composition per serving for Contoso Product?"
        }
    ],
    "approach": "rrr",
    "overrides": {},
    "enableExternalDomain": false,
    "container": "95780f6b-1687436130606",
    "index": "c0375bf8-1687436130606"
}
```

**ENVIRONMENT VARIABLES (Search Horizontal):**

| APP Setting | Value         | Note |
|---------|----------|-----------------------|
| AZURE_SEARCH_SERVICE_NAME | YOUR_AZURE_SEARCH_SERVICE_NAME   | Your Azure Cognitive Search service name. Fetch it from the Azure Portal.|
| AZURE_SEARCH_KEY	| YOUR_AZURE_SEARCH_KEY            | Your Azure Cognitive Search key. Fetch it from the Azure Portal|
| AZURE_STORAGE_ACCOUNT_KEY   | YOUR_AZURE_STORAGE_ACCOUNT_KEY   | Your Azure Storage Account Key. Fetch it from the Azure Portal |
| AZURE_STORAGE_ACCOUNT_NAME |  YOUR_AZURE_STORAGE_ACCOUNT_NAME | Your Azure Storage Account Name. Fetch it from the Azure Portal |
| FORM_RECOGNIZER_KEY                   | YOUR_FORM_RECOGNIZER_KEY         | Azure Form Recognizer Key, Fetch it from the Azure Portal |
| AZURE_OPENAI_GPT_DEPLOYMENT           | YOUR_AZURE_OPENAI_GPT_DEPLOYMENT | Get Azure openai GPT Deployment name from Azur Portal |
| AZURE_OPENAI_KEY                      | YOUR_OPENAI_KEY                  | Get OpenAI key from Azure Portal |
| AZURE_OPENAI_SERVICE                  | YOUR_OPENAI_SERVICE              | Get OpenAI service Name |
| AZURE_SEARCH_SERVICE_PROD_KEY        | YOUR_SEARCH_SERVICE_PROD_KEY      | Get Prod key from Azure Portal |
|
> **NOTE:** Using the below code snippet, you can test the environment variables by configuring them locally inside “function_app.py”. Please add the name of the services and keys after the word “or” for respective variable.


```
AZURE_STORAGE_ACCOUNT = os.environ.get("AZURE_STORAGE_ACCOUNT") or "" 

AZURE_STORAGE_CONTAINER = os.environ.get("AZURE_STORAGE_CONTAINER") or "" 

AZURE_SEARCH_SERVICE = os.environ.get("AZURE_SEARCH_SERVICE") or "" 

AZURE_SEARCH_INDEX = os.environ.get("AZURE_SEARCH_INDEX") or "" 

AZURE_OPENAI_SERVICE = os.environ.get("AZURE_OPENAI_SERVICE") or "" 

AZURE_OPENAI_GPT_DEPLOYMENT = os.environ.get("AZURE_OPENAI_GPT_DEPLOYMENT") or "" 

AZURE_OPENAI_CHATGPT_DEPLOYMENT = os.environ.get("AZURE_OPENAI_CHATGPT_DEPLOYMENT") or "" 

AZURE_OPENAI_SERVICE_KEY = os.environ.get("AZURE_OPENAI_SERVICE_KEY") or "" 

AZURE_SEARCH_SERVICE_KEY = os.environ.get("AZURE_SEARCH_SERVICE_KEY") or "" 

AZURE_SEARCH_SERVICE_PROD_KEY = os.environ.get("AZURE_SEARCH_SERVICE_PROD_KEY") or "" 

AZURE_STORAGE_ACCOUNT_KEY = os.environ.get("AZURE_STORAGE_ACCOUNT_KEY") or "" 
```
   
    
----
## Campaign Generation

This function app is used to generate Instagram or Email campaigns related to the description passed in the body.

**Path to build:** 'artifacts/binaries/func-campaign-generation.zip'

### Steps to generate POST URL for 'Campaign Generation' function app:

1. Under the **func-campaign-generation** folder, select function_app.py.

![PDF Indexer explorer](media/select_function_app.png)

2. **Repeat steps** from step number 2 to step number 12 for func-campaign-generation in the similar way as performed for PDF Indexer.

3. Use the following values for POSTMAN requests.

**POST URL:**
```
http://localhost:7071/api/CampGen
```

**BODY**: raw -> JSON
```
{
	creative_factor : (Float) —> Value between 0 to 1,
	description : (str) —> description of campaign,
	type : (str)  → type(instagram/email)
}
```

**Return:** 
```
{
    prompt: (str),
    campaign: (str),
    title : (str)
}
```

**Example Values:**

The below example is for a new Instagram campaign generation.

**BODY:**
```
{
"creative_factor": "0.8",

"description": "Write an Instagram post for a company called Contoso. The post is for a promotion for a 50% discount on the launch of a new line of clothing. The new line focuses on minimalism. The post should include the following:\n1. A headline for the Instagram post.\n2. Choose words that communicate minimalism.\n3. A poem about how the line of clothing demonstrates minimalism.\n4. Include appropriate emojis in the post.\n5. Include relevant Hashtags.\n6. Post should contain at least 40 words.\nConsidering everything described above, give me an Instagram post with a post title, post content with appropriate hashtags and emojis. Close the post with a relevant poem as described above.",

"type": "instagram"
}
```

**Return:**
```
{
    "prompt": "Create instagram campaign on following info:Write an Instagram post for a company called Contoso. The post is for a promotion for a 50% discount on the launch of a new line of clothing. The new line focuses on minimalism. The post should include the following:\n1. A headline for the Instagram post.\n2. Choose words that communicate minimalism.\n3. A poem about how the line of clothing demonstrates minimalism.\n4. Include appropriate emojis in the post.\n5. Include relevant Hashtags.\n6. Post should contain at least 40 words.\nConsidering everything described above, give me an Instagram post with a post title, post content with appropriate hashtags and emojis. Close the post with a relevant poem as described above..",

    "campaign": "#StayMinimal 🤍 \nIntroducing our new line of minimalistic clothing from Contoso! We're celebrating the launch with a 50% discount! 🤩🎉 \n\nFocusing on subtle details, our minimalist clothing line is designed to make sure you always look on-trend. From sophisticated cuts to unique patterns, our clothing speaks for itself. 💯 \n\n#minimalismissimplicity 🤍 #Contosominimalclothing 🤍 #minimalismlifestyle 🤍 \n\nLess is more, they say,\nWe focus on the details,\nCreating a timeless look,\nIn every occasion we prevail. 🤍 #Contosominimalclothing",

    "title": "Less is More: Timeless Minimalism with ContosoMinimalClothing"
}
```

**ENVIRONMENT VARIABLES:**


| App Setting | Value  | Note |
| ----------- | ------ | ---- |
| AZURE_OPENAI_SERVICE_KEY| YOUR_AZURE_SEARCH_SERVICE_NAME | Your Azure Cognitive Search service name. Get it in the Azure Portal |
| AZURE_OPENAI_SERVICE | YOUR_OPENAI_SERVICE | Get openAI service Name |  
| AZURE_OPENAI_GPT_DEPLOYMENT | YOUR_AZURE_OPENAI_GPT_DEPLOYMENT | Get Azure openAI model deployment name |

> **Note:**  Inside "__init__.py", you can configure the environment variable locally to test as given in the below code snippet. Please add the name of the services and keys after “or” for the respective variables.

 ```
 AZURE_OPENAI_SERVICE_KEY = os.environ.get("AZURE_OPENAI_SERVICE_KEY") or "" 

AZURE_OPENAI_SERVICE = os.environ.get("AZURE_OPENAI_SERVICE") or "" 

AZURE_OPENAI_GPT_DEPLOYMENT = os.environ.get("AZURE_OPENAI_CHATGPT_DEPLOYMENT") or "" 

AZURE_OPENAI_CHATGPT_DEPLOYMENT = os.environ.get("AZURE_OPENAI_CHATGPT_DEPLOYMENT") or ""
 ```
 ----
## Recommend Images

This function app is used to recommend similar images with respect to the image passed in the body.
** Path to build:** 'artifacts/binaries/func-recommend-image.zip' 

### Steps to generate POST URL for 'Recommend Images' fucntion app:

1. Under the **func-recommend-image** folder, select function_app.py.

![PDF Indexer explorer](media/select_function_app.png)

2. **Repeat steps** from step number 2 to step number 12 for func-recommend-image in the similar way as performed for PDF Indexer.

3. Use the following values for POSTMAN requests.

**POST URL:**

```
http://localhost:7071/api/recommendFromImage_V2
```

**BODY:** raw -> JSON
```
{
"image_url": (str)-->url,
"image_num": (Integer)
}
```

**Return:** 
```
{
    "productDescription": -->(str),
    "recommendedItems": {
        "Recommended Item 1": (str)--> url,
        "Recommended Item 2": (str) --> url,
        "Recommended Item 3": (str) --> url,
        "Recommended Item 4": (str) --> url,
    },
    "background_removed_image": (str) --> url,

    "major color": (str),

    "colors": (str),

    "caption": (str),

    "summary of caption": (str),

    "prompt": (str)
}
```

**Example raw-data for recommendations from image:**
```
{
"image_url":"https://i.ibb.co/SvSp7F7/minimalist.png",
"image_num":"1"
}
```

**Return:**
```
{
    "productDescription": "a pink and purple fabric",
    "recommendedItems": {

        "Recommended Item 1": "https://stopenaias2606xigcnuub6l.blob.core.windows.net/data2/gper5he.jpg",

        "Recommended Item 2": "https://stopenaias2606xigcnuub6l.blob.core.windows.net/data2/oetpvam.jpg",

        "Recommended Item 3": "https://stopenaias2606xigcnuub6l.blob.core.windows.net/data2/jgc2rrb.jpg",

        "Recommended Item 4": "https://stopenaias2606xigcnuub6l.blob.core.windows.net/data2/f83n1by.jpg"
    },

    "background_removed_image": "https://stopenaias2606xigcnuub6l.blob.core.windows.net/data2/elxbscj.jpg",

    "major color": "lightcyan,",

    "colors": "lightcyan, dullyellow, celadon",

    "caption": "1. A table with a blue cloth and shoes on it.\n2. A table with a silver object on it.\n3. A close-up of a yellow fabric.\n4. A close up of a pair of glasses.\n5. A blue and white background.\n6. A close-up of a metal object.\n7. A blue fabric draped over a white surface.\n8. A blurry image of a person's head.\n9. A close up of a bird's head.",

    "summary of caption": "The items having a probability of more than 40% in this data are:\n\n- a close-up of a yellow fabric\n- a close up of a pair of glasses\n- a close-up of a metal object\n- a blue fabric draped over a white surface\n- a blurry image of a person's head\n- a close up of a bird's head\n- a table with a blue cloth and shoes on it\n- a table with a blue cloth and shoes on it",

    "prompt": "Generate a digital artwork with a plain gradient background that seamlessly blends sea green and sky blue colors, complementing a central element with a reflective or metallic appearance"
}
```

**ENVIRONMENT VARIABLES**


| APP Setting | Value | Note |
|--------|------|------|
| CONTAINER_NAME   | YOUR_AZURE_CONTAINER_NAME  | Your Azure Container Name. Get it in the Azure Portal.       |
| OPENAI_API_KEY        | YOUR_AZURE_SEARCH_KEY             | Your Azure OpenAI Key             |
| CONGNITIVE_KEY     	| YOUR_COGNITIVE_KEY                | Your Azure Cognitive Key          |
| OPENAI_API_TYPE		| YOUR_OPENAI_TYPE                  | Your OpenAI Type                  |
| ENGINE                | YOUR_AZURE_ENGINE                 | Your Engine Name used                  
| STORAGE_ACCOUNT       | YOUR_AZURE_STORAGE_ACCOUNT        | Your Azure Storage Account Name. Get it in the Azure Portal      |
| STORAGE_CONTAINER     | YOUR_AZURE_STORAGE_CONTAINER      | Your Azure Storage Container Name. Get it in the Azure Portal      |    
| STORAGE_ACCOUNT_KEY   | YOUR_STORAGE_ACCOUNT_KEY          | Your Azure Storage Account Key. Get it in the Azure Portal      |
| COGNITIVE_SERVICE_API | YOUR_COGNITIVE_SERVICE_API        | Your Cognitive Service API. Get it in the Azure Portal      |
| CONNECT_STR           | YOUR_CONNECT_STRING  | Your Connect String. Get it in the Azure Portal      |
 

> **NOTE:**  Inside "function_app.py", you can configure the environment variable locally to test as given in the below code snippet. Please add the name of the services and keys after “or” for the respective variables.

```
container_name = os.environ.get("container_name") or "" 

AZURE_OPENAI_KEY = os.environ.get("openai.api_key") or "" 

AZURE_COGNITIVE_KEY = os.environ.get("cognitive_key") or "" 

connect_str_key = os.environ.get("connect_str") or "" 

AZURE_OPENAI_type = os.environ.get("openai.api_type") or "" 

AZURE_OPENAI_BASE = os.environ.get("openai.api_base") or "" 

openai.api_version = "2023-03-15-preview" 

ENGINE = os.environ.get("ENGINE") or "" 

STORAGE_ACCOUNT = os.environ.get("STORAGE_ACCOUNT") or "" 

connect_str_key = os.environ.get("connect_str") or "" 

STORAGE_CONTAINER = os.environ.get("STORAGE_CONTAINER") or "" 

STORAGE_ACCOUNT_KEY = os.environ.get("STORAGE_ACCOUNT_KEY") or "" 

COGNITIVE_SERVICE_API = os.environ.get("COGNITIVE_SERVICE_API") or "" 

COGNITIVE_SERVICE = os.environ.get("COGNITIVE_SERVICE") or "" 
```

 ----
 
 ## Regenerate Images with DALL-E 2

This function app uses DALL-E to regenerate images according to the description passed in the body in accordance with the given images.
** Path to build:** 'artifacts/binaries/func-regenerate-dalle.zip' 

 ### Steps to generate POST URL for 'Regenerate images with DALL-E 2' function app:

1. Under the **func-regenerate-dalle** folder, select function_app.py.

![PDF Indexer explorer](media/select_function_app.png)

2. Repeat steps from step number 2 to step number 12 for func-regenerate-dalle in the similar way as performed for PDF Indexer.

3. Use the following values for POSTMAN requests.

**POST URL:**
```
http://localhost:7071/api/dalleimage_generation 
```

**BODY:** raw--> JSON
```
{
"dalle_prompt": (str) --> prompt for the image to be generated
}
```

**Return:**
```
{
    "dalle_prompt": (str)--> prompt for gnerating image,

    "recommendedItems": {
        "Recommended Item 1": (str) --> url of image,

        "Recommended Item 2":(str) --> url of image,,

        "Recommended Item 3": (str) --> url of image
    }
}
```

**Example raw-data for dalle images generation:**
```
{
"dalle_prompt":"Generate a realistic image of a convertible orange sports car on a road in a cloudy day"
}
```

**Return:**
```
{
    "dalle_prompt": "Generate a realistic image of a convertible orange sports car on a road in a cloudy day",

    "recommendedItems": {
        "Recommended Item 1": "https://dalleproduse.blob.core.windows.net/private/images/c17970e9-00ac-40f5-a1a5-84f025b97aae/generated_00.png?se=2023-06-27T17%3A55%3A40Z&sig=BtwZZUR%2B5KYwFzKFbBnKz8RUc5AsPwwnVSU4%2BIPMtAw%3D&ske=2023-06-30T15%3A41%3A20Z&skoid=09ba021e-c417-441c-b203-c81e5dcd7b7f&sks=b&skt=2023-06-23T15%3A41%3A20Z&sktid=33e01921-4d64-4f8c-a055-5bdaffd5e33d&skv=2020-10-02&sp=r&spr=https&sr=b&sv=2020-10-02",

        "Recommended Item 2": "https://dalleproduse.blob.core.windows.net/private/images/8c9f6deb-7dd4-40d3-9518-00c499fa1daa/generated_00.png?se=2023-06-27T17%3A55%3A46Z&sig=oYGsONLYx0aXdNaISrb6MtwmX%2FTL%2FIagjtCu9%2F3tjZU%3D&ske=2023-06-29T14%3A56%3A07Z&skoid=09ba021e-c417-441c-b203-c81e5dcd7b7f&sks=b&skt=2023-06-22T14%3A56%3A07Z&sktid=33e01921-4d64-4f8c-a055-5bdaffd5e33d&skv=2020-10-02&sp=r&spr=https&sr=b&sv=2020-10-02",

        "Recommended Item 3": "https://dalleproduse.blob.core.windows.net/private/images/ba05ce5c-2dfa-4d95-8f6b-584be6e7121d/generated_00.png?se=2023-06-27T17%3A55%3A52Z&sig=tk66mFA4uigTUkWB%2BqBdMPZNWunAwajUjzAQ3C%2BgZro%3D&ske=2023-06-30T15%3A41%3A20Z&skoid=09ba021e-c417-441c-b203-c81e5dcd7b7f&sks=b&skt=2023-06-23T15%3A41%3A20Z&sktid=33e01921-4d64-4f8c-a055-5bdaffd5e33d&skv=2020-10-02&sp=r&spr=https&sr=b&sv=2020-10-02"
    }
}
```

**ENVIRONMENT VARIABLES:**

Here is the explanation of the Parameters:

| APP Setting  | Value  | Note |
|----------|-----------|-----------|
| OPENAI_API_ENDPOINT | YOUR_OPENAI_API_ENDPOINT | Get your OpenAI API Endpoint   |
| OPENAI_KEY  | YOUR_OPENAI_KEY | Get OpenAI key from Azure Portal |
    
> **NOTE:**  Inside image_generation.py, you can configure the environment variable locally to test as given in the below code snippet. Please add the name of the services and keys after “or” for the respective variables.
```
API_KEY = os.environ.get("OPENAI_API_KEY") or "" 

API_ENDPOINT = os.environ.get("OPENAI_API_ENDPOINT") or "" 
```
---

## Method 2: Executing the demo through demo web app

>**Note:** It is important to execute all the steps in the "Setup-Document.md" before performing the following steps.

1. In the Azure Portal, under resource group **search** for "app-open-ai" and **click** on the app service.

    ![image](media/scenario1_ui7.png)

2. **Scroll down** in the left pane, **click** on "Configuration", make sure you are under "Application settings" and then **click** on "Advanced edit".

    ![image](media/scenario3_ui1.png)

3. In the Advanced Edit tab values of "Config__pdfUploadApi" and "Config__endPointURL" are used for the 1st Scenario which corresponds to function app of "pdf-indexer" and "search-horizontal" respectively.

    ![image](media/webapp1.png)

4. In the Advanced Edit tab values of "Config__florenceAdApi", "Config__florenceDallEApi" and "Config__dalleRegenerateAPI" are used for the 2nd Scenario which corresponds to function app of "campaign-generator", "recommend-images" and "regenerate-dalle" respectively.

    ![image](media/webapp2.png)

5. In the Advanced Edit tab values of "Config__summarizeConversationAPI" and "Config__summarizeConversationAPIKey" are used for the 3rd Scenario which corresponds to "OpenaAI service endpoint" and "OpenaAI service key" respectively.

    ![image](media/webapp3.png)

---

## Scenario 1 - Azure OpenAI Service and Azure Cognitive Search powered chatbot for Enterprise data

This first scenario is a great example of how enterprises can use Azure OpenAI Service to quickly gain insights from their unstructured data.
Spencer, Contoso’s new CEO, dreams of a search tool where he can simply ask a question related to a specific document or documents and receive a quick, trustworthy answer. 
Let’s see how the power of Azure OpenAI Service and Azure Cognitive Search combine to create this solution.

1. In the Azure Portal, under resource group **search** for "app-open-ai" and **click** on the app service.

    ![image](media/scenario1_ui7.png)

2. **Click** on "Browse".

    ![image](media/scenario1_ui8.png)

3. From the left navigation bar **click** on "Azure OpenAI Chatbot for Enterprise Data".
 
 ![A portion of the Azure Portal home screen is displayed with the + Create a resource tile highlighted.](media/predefined2.png)

4. Below are the questions from the pretrained knowledge base for Azure OpenAI Chatbot for Enterprise Data.

5. **Click** on one of the queries.
 
 ![A portion of the Azure Portal home screen is displayed with the + Create a resource tile highlighted.](media/predefined1.png)

6. **View** the answer for the selected query. 

 ![A portion of the Azure Portal home screen is displayed with the + Create a resource tile highlighted.](media/predefined21.png) 

7. If you want to query your custom data then **click** on the button infront of "try your own data".

 ![A portion of the Azure Portal home screen is displayed with the + Create a resource tile highlighted.](media/predefined20.png)

8. **Click** on the "Select files..." button.  
 
 ![A portion of the Azure Portal home screen is displayed with the + Create a resource tile highlighted.](media/predefined28.png)
 
9. **Select** the required "pdf" file and **Click** on open.

 ![A portion of the Azure Portal home screen is displayed with the + Create a resource tile highlighted.](media/predefined30.png)

10. **Click** on the "Upload" button.
 
 ![A portion of the Azure Portal home screen is displayed with the + Create a resource tile highlighted.](media/predefined25.png)

11. **Type** your query, then **click** on the send button.  
 
  ![A portion of the Azure Portal home screen is displayed with the + Create a resource tile highlighted.](media/predefined26.png)

12. **View** the AI generated response. 
 
 ![A portion of the Azure Portal home screen is displayed with the + Create a resource tile highlighted ](media/predefined27.png)


### Steps to configure function app used in Scenario 1:

1. **Goto** Azure Portal, in the resource group search for "func-openai-search-horizontal" and **click** on the function app resource.

    ![image](media/scenario1_ui.png)

2. **Scroll down** in the left pane, **click** on "Configuration", make sure you are under "Application settings" and then **click** on "Advanced edit".

    ![image](media/scenario1_ui2.png)

3. **Replace** the values as shown below according to your requirement.

|   name    |   value   |
| --------- | --------- |
| AZURE_OPENAI_SERVICE | Your openAI service name |
| AZURE_OPENAI_SERVICE_KEY | Your openAI service key |
| AZURE_OPENAI_GPT_TURBO_DEPLOYMENT | Your gpt-35-turbo model deployment name |
| AZURE_OPENAI_TEXT_DAVINCI_DEPLOYMENT | Your text-davinci-003 model deployment name |
| AZURE_SEARCH_SERVICE | Your search service name |
| AZURE_SEARCH_SERVICE_KEY | Your search service key |
| AZURE_SEARCH_SERVICE_PROD_KEY | Your search service key |
| AZURE_STORAGE_ACCOUNT | Your storage account name |
| AZURE_STORAGE_ACCOUNT_KEY | Your storage account key |
| AZURE_SEARCH_INDEX | Pretrained knowledge base index name |
| AZURE_STORAGE_CONTAINER | Pretrained knowledge base container name |
    
4. **Click** on "OK" button.

    ![image](media/scenario1_ui3.png)

5. **Click** on "Save".

    ![image](media/scenario1_ui4.png)

6. **Click** on "Continue".

    ![image](media/scenario1_ui5.png)

7. Scroll up, **select** "Overview" and **click** on "Restart".

    ![image](media/scenario1_ui6.png)

8. Now the function app will use the updated resources.

9. **Repeat** the steps from step number 13 to step number 19 to customize "func-pdf-indexer".

10. **Replace** the values as shown below:

|   name    |   value   |
| --------- | --------- |
| FormRecognizerService | Your form recognizer resource name |
| FORM_RECOGNIZER_KEY | Your form recognizer primary key |
| SEARCH_SERVICE_NAME | Your search service name |
| SEARCH_SERVICE_KEY | Your search service key |
| STORAGE_ACCOUNT_NAME | Your storage account name |
| STORAGE_ACCOUNT_KEY | Your storage account key |

----

## Scenario 2 - Social Media Campaign and Product Recommendation

In this use case, we are using Azure OpenAI’s powerful language models to automatically generate campaign title and description from user prompt. Computer Vision and Florence-based AI models remove the background from the original image and extract dense captions. After that, we are generating abstract background images by providing a prompt using DALL.E2 in Azure OpenAI Service. And finally, we are merging the image which does not include the original background with the generated background to create the final result.

**In the web app:**

1. From the left navigation bar **click** on "Social Media Campaign & Product Recomendation".

    ![image](media/scenario2_ui1.png)

2. **Click** on the "Dropdown" and **select** "Sports Car".

    ![image](media/scenario2_ui2.png)

3. **Scroll down** and **click** on "Process".

    ![image](media/scenario2_ui3.png)

4. The response 1 is an Instagram Campaign and response 2,3 are Recommended Image generated using ResponsibleAI.

    ![image](media/scenario2_ui4.png)

5. **Click** on "Show Prompt" at right top of the screen.

    ![image](media/scenario2_ui5.png)

6. The default prompt would be "Generate a realistic image of a convertible orange sports car on a road in a sunny day"

7. **Click** on the "Edit" button.

    ![image](media/scenario2_ui6.png)

8. **Replace** the prompt with custom data for e.g. "sunny day" with "rainy day" and **click** on the "Send" button.

    ![image](media/scenario2_ui7.png)

9. The response is generated using "DALL-E 2".

    ![image](media/scenario2_ui8.png)

### Steps to configure function app used in Scenario 2:

1. **Go to** the Azure Portal.

2. In the resource group search field, **type** "func-campaign-generator" and **select** the function app.

    ![image](media/scenario2_1.png)

3. In the left pane, **scroll down** and **click** on "Configuration".

    ![image](media/scenario2_2.png)

4. Under "Application settings", **select** "Advanced edit".

    ![image](media/scenario2_3.png)

5. **Replace** the values as shown below:

| Name  |  Value |
| ----- | ------ |
| AZURE_OPENAI_SERVICE | Your OpenAI service name |
| AZURE_OPENAI_SERVICE_KEY | Your OpenAI service key |
| AZURE_OPENAI_GPT_DEPLOYMENT | Your OpenAI service model deployment name |
| AZURE_OPENAI_CHATGPT_DEPLOYMENT | Your openAI model's engine Name |

6. **Click** on "OK" button.

    ![image](media/scenario2_4.png)

7. **Click** on "Save" button.

    ![image](media/scenario2_5.png)

8. **Click** on "Continue" button.

    ![image](media/scenario2_6.png)

9. Wait for the changes to save, **scroll up** on the left pane, **click** on "Overview" and **click** on "Restart".

    ![image](media/scenario2_7.png)

10. Repeat the above steps for **func-recommend-images** and **func-regenerate-dalle** function apps. 

**Replace** the values as shown below for **func-recommend-images** :

| Name  |  Value |
| ----- | ------ |
| COGNITIVE_SERVICE_API | Your cognitive service endpoint |
| cognitive_key | Your cognitive service key |
| ENGINE | Your openAI service deployment model name |
| OPENAI_API_ENDPOINT | Your openAI service endpoint |
| OPENAI_API_KEY | Your openAI service key |

**Replace** the values as shown below for **func-regenerate-dalle** :


| Name  |  Value |
| ----- | ------ |
| OPENAI_API_ENDPOINT | Your openAI service endpoint |
| OPENAI_API_KEY | Your openAI service key |

----

## Scenario 3 - Azure OpenAI with Speech Service

In this scenario, we will see a live conversation between a customer and a contact center agent being translated into machine readable format. After each question asked by the customer, Azure OpenAI Service offers intelligent and relevant suggested answers to the agent in near real-time! 
We can track customer sentiment. Azure OpenAI can create a natural language summary of this conversation which can be reviewed for script improvement suggestions, or adding specific notes.  

**In the web app:**

1. From the left navigation bar, **hover** over "Azure OpenAI with Speech Service" and **click** on "Customer Conversation".

![A portion of the Azure Portal home screen is displayed with the + Create a resource tile highlighted.](media/image_callcentre_1.png)

2. **Click** on the play button.

![A portion of the Azure Portal home screen is displayed with the + Create a resource tile highlighted.](media/image_callcentre_2.png)

3. Once the conversation is complete, **click** on "Summarize Conversation".

![A portion of the Azure Portal home screen is displayed with the + Create a resource tile highlighted.](media/image_callcentre_3.png)

4. **View** the summarized conversation.

![A portion of the Azure Portal home screen is displayed with the + Create a resource tile highlighted.](media/image_callcentre_4.png)

5. **Click** on "Send to Application".

![A portion of the Azure Portal home screen is displayed with the + Create a resource tile highlighted.](media/image_callcentre_5.png)

6. **View** the Call Transcript.

![A portion of the Azure Portal home screen is displayed with the + Create a resource tile highlighted.](media/image_callcentre_6.png)

7. **Click** on Generate Summary.

![A portion of the Azure Portal home screen is displayed with the + Create a resource tile highlighted.](media/image_callcentre_7.png)

8. **View** the Generated Result.

![A portion of the Azure Portal home screen is displayed with the + Create a resource tile highlighted.](media/image_callcentre_8.png)

### Steps to configure app service used in scenario 3:

1. **Go to** the Azure Portal.
2. In the resource group search field **type** "app-open-ai" and **select** the app service.

    ![image](media/scenario1_ui7.png)

3. **Scroll down** in the left pane, **click** on "Configuration".
4. Under "Application settings", **select** "Advanced edit".

    ![image](media/scenario3_ui1.png)

5. **Replace** the values as shown below according to your requirement.

|   Name    |   Value   |
| --------- | --------- |
| Config__summarizeConversationAPI | Your openAI service name |
| Config__summarizeConversationAPIKey | Your openAI service key |
    
>**Note:** Value for Config__summarizeConversationAPI will be in the format "https://#OPENAI_SERVICE#.openai.azure.com/openai/deployments/text-davinci-003/completions?api-version=2022-12-01".
You just need to replace "#OPENAI_SERVICE#" with Your openAI service name.

6. **Click** on "OK" button.

    ![image](media/scenario3_ui2.png)

7. **Click** on "Save".

    ![image](media/scenario3_ui3.png)

8. **Click** on "Continue".

    ![image](media/scenario1_ui5.png)

9. Scroll up, **select** "Overview" and **click** on "Restart".

    ![image](media/scenario3_ui4.png)

10. Now the web app will use the updated resources.

----
## Appendix
----

### Training the Knowledge Base using Postman and Python

To train the knowledge base for Scenario 1: "Azure OpenAI Service and Azure Cognitive Search powered chatbot for Enterprise data", we have used an automation script "openAISetup.ps1". However, the knowledge base can also be trained using the following steps:

### Steps to train the Knowledge Base:

1. **Start** VS Code on your loacal machine. The following screen will appear.
    ![VS Code landing page](media/vs_code_landing_page.png)

2. **Open** the locally cloned repository (mentioned in pre-requisites) in VS Code. You should be able to see all the necessary files as given in the screenshot below. Make sure that you extract all the zipped folder marked #3 in the screenshot. In the next steps, we will execute function app for all these folders one- by -one.
    
    ![Artifacts Folder Structure](media/folder_structure.png)

### Steps to generate POST URL for 'PDF Indexer' function app:

This function-app indexes an uploaded PDF file into the number of pages in the PDF.

1. Under the **func-pdf-indexer** folder, select function_app.py.
   
    ![PDF Indexer explorer](media/select_function_app.png)

2. **Open** a new terminal. In the next command line, **execute** the following code for the function to start.

    ```
    func start
    ```

    ![Start the function](media/func_start.png)

3. Once the execution is complete, the function will give the following URLs to perform DELETE and INDEXING operations. **Copy** the 'pdfindexer' URL for further use.

    ![URLs](media/urls_pdf_indexer.png)


4. **Open** the Postman application, then **select** the "New" button to create a new request.

    ![Select new request.](media/select_new_request.png)

5. In the pop up window, **select** HTTP request.

    ![Select HTTP request.](media/select_http.png)

6.  In the new request page, **select** "POST" method from the dropdown as shown in the screenshot.

   ![Select POST request.](media/select_post1.png)

7. **Paste** the 'pdfindexer' URL copied earlier from the VS Code terminal in the text fiels next to POST. (Copied in step #18). 
8. Select the Body tab to add other parameters.

    ![Paste POST URL.](media/post_url.png)

9. **Select** the "Body" option , **select**  “form-data”.
10. Provide the required key-value pair as given below.

| Key | Value |
|--------------|-------------|
| index_name | prod-responsibleai-search |
| container_name |knowledge-base-responsibleai |
| pdf | [Select the PDF 'Microsoft-Responsible-AI-Standard-v2-General-Requirements.pdf' shared with you in the package] |

11. Click on **Send**.

 ![Fill in form-data](media/form_body.png)

12.  **View** the response.

 ![Response for PDF Indexer](media/response_pdf.png)

13. Our Knowledge Base has been trained on "Microsoft-Responsible-AI-Standard-v2-General-Requirements.pdf".

14. **Repeat** step number 10, by replacing the "PDF" with the rest of the ResponsibleAI PDFs available in the package, to train the knowledge base completely.
----
----
<p style="text-align: center;"><b>Demo End</p>


----
----
