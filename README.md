![image](media/OpenAI_DDiB.png)

# Azure OpenAI Dream Demo

Azure OpenAI Service offers large-scale generative AI models with a deep understanding of language to enable new reasoning and comprehension capabilities for building cutting-edge applications. These models can be applied to a variety of use cases, such as writing assistance, code generation, and reasoning over data. You can also detect and mitigate harmful use of AI with built-in responsible AI and access enterprise-grade Azure security.

In this demo, you will see the Azure OpenAI Service based assistant for Enterprise Data Demo, in action. This will be followed by a generated Social Media Campaign Recommendation demo using DALL-E 2, Florence and Azure OpenAI Service. And finally, you will see text summarization in a contact center scenario using Azure OpenAI with Speech Service.

## Products and Technologies showcased:

1.	Azure OpenAI Service

    •	Azure OpenAI Service provides REST API access to OpenAI's powerful language models. These models can be easily adapted to your specific task including but not limited to content generation, summarization, semantic search, and natural language to code translation.
    
    •	The models used by Azure OpenAI use natural language instructions and examples provided during the generation call to identify the task being asked and skill required.
    
    •	With Azure OpenAI, customers get the security capabilities of Microsoft Azure while running the same models as OpenAI. Azure OpenAI offers private networking, regional availability, and responsible AI content filtering.

2.	DALL.E2

    •	DALL·E 2 is an AI system that can create original, realistic images and art from a text description in natural language. It can combine concepts, attributes, and styles. 
    
    •	DALL·E 2 can make realistic edits to existing images from a natural language caption. It can add and remove elements while taking shadows, reflections, and textures into account. It can also create different variations of it inspired by the original.

3.	Project Florence (AI)
    
    •	Project Florence is a Microsoft AI Cognitive Services initiative, to advance the state-of-the-art computer vision technologies and develop the next generation framework for visual recognition.

## Running this repo

You have multiple options to execute this demo:

-   [Running everything locally in Python using Postman](#running-everything-locally-in-python-using-postman)

    -   [Pdf Indexer](#pdf-indexer)
    -   [Search Horizontal](#search-horizontal)
    -   [Campaign Generation](#campaign-generation)
    -   [Recommend Image](#recommend-image)
    -   [Regenerate DALL E](#regenerate-dall-e)

-   [Execution through Web App](#execution-through-web-app)

    -   [Scenario 1 : Azure OpenAI and Cognitive Search](#scenario-1-azure-openai-and-cognitive-search)

        -   [Training the Knowledge Base](#training-the-knowledge-base)
        -   [Webapp Scenario 1](#webapp-scenario-1)
        -   [Configuring Function App for Scenario 1](#configuring-function-app-for-scenario-1)    

    -   [Scenario 2 : Social Media Campaign and Product Recommendation](#scenario-2-social-media-campaign-and-product-recommendation)
        -   [Webapp Scenario 2](#webapp-scenario-2)
        -   [Configuring Function App for Scenario 2](#configuring-function-app-for-scenario-2) 

    -   [Scenario 3 : Azure OpenAI with Speech Service](#scenario-3-azure-openai-with-speech-service)
        -   [Webapp Scenario 3](#webapp-scenario-3)
        -   [Configuring Web App for Scenario 3](#configuring-web-app-for-scenario-3) 


### Running everything locally in Python using Postman

*Prerequisites:*
* Clone the repository to your local - [Link](https://dev.azure.com/daidemos/Microsoft%20Data%20and%20AI%20DREAM%20Demos%20and%20DDiB/_git/DreamDemoInABox?version=GBopen-ai-ddib&anchor=execution-through-webapp-scenario-1&path=/artifacts)
* Visual Studio Code - [Download VS Code](https://code.visualstudio.com/download)
* Azure Account - [Azure Portal](https://portal.azure.com/)
* Postman - [Download Postman](https://www.postman.com/downloads/)


**General steps to locally run and test the function_app.py**

1. **Open** the code in Visual Studio and Create an azure function using the V2 programming model in visual studio code and open the build.

  ![A portion of the Azure Portal home screen is displayed with the + Create a resource tile highlighted.](media/img11.png)

2. **Run**  the "function_app.py" code in visual studio using the command **func start** or **fn+F5** and click **enter**.

 ![A portion of the Azure Portal home screen is displayed with the + Create a resource tile highlighted.](media/image_search_2.png)

3. **Copy** the chat URL generated in the terminal (as indicated by the red box in this example). 

```
a. http://localhost:7071/api/chat  - This URL will be used to test "Search Horizontal Function App".

b. http://localhost:7071/api/pdfindexer  - This URL will be used to test "Pdf Indexer Function App".

c. http://localhost:7071/api/CampGen  - This URL can be used to test Campaign Generation Function APP

d. http://localhost:7071/api/recommendFromImage_V2 - This URL can be used to test Recommendations from Images Function APP

e. http://localhost:7071/api/dalleimage_generation - This URL can be used to test Generation of Images using Function APP 

```

 ![A portion of the Azure Portal home screen is displayed with the + Create a resource tile highlighted.](media/image_search_3.png)

4. **Open** the Postman application, then **click** the "New" button to create a new "POST" request.

 ![A portion of the Azure Portal home screen is displayed with the + Create a resource tile highlighted.](media/image_search_4.png)

5. **Paste** the chat URL (copied from the visual studio terminal during step 1.3). 

 ![A portion of the Azure Portal home screen is displayed with the + Create a resource tile highlighted.](media/image_search_5.png)

6. **Go to** the "Body" option , **select**  “raw”, and **enter** the "request body", then **click** on the “Send” button.

 ![A portion of the Azure Portal home screen is displayed with the + Create a resource tile highlighted.](media/img22.png)

7. **View** the response.

 ![A portion of the Azure Portal home screen is displayed with the + Create a resource tile highlighted.](media/image_search_7.png)

> **Note:**  Any function app can be tested in a similar way. Just the URL and payload body will change. Please find the sample payloads for the all function apps used the demo.

### Pdf Indexer

This function app is used to index any pdf uploaded, into the number of pages the pdf consists of.

*Path to build:* 'artifacts/binaries/func-pdf-indexer.zip'

Extract the zip and continue with the steps below.

**Sample payload to test “pdfindexer” from the backend using Postman:**

*POST:* 
``` 
http://localhost:7071/api/pdfindexer 
```

*BODY:* form-data
``` 
{
    index_name : (str) —> YOUR_INDEX_NAME,
	container_name : (str) —> CONTAINER_NAME,
	pdf : {FILE}  → YOUR_PDF
}
```

*Return:*
```
{
    "index_name": "YOUR_INDEX_NAME",
    "container_name": "CONTAINER_NAME"
}
```

*Example Values:*

* The below example is for uploading PDFs as "Knowledge Base."
```
    index_name: “prod-responsibleai-search”
    container_name: “knowledge-base-responsibleai”
    pdf: (str) --> path-to-your-pdf-file
```

* The below example is for uploading any general PDFs from the user. Here, the index name and container name will be randomly generated by the webapp.

```
    index_name: "46a0175b-1687428489218”
    container_name: “4184f94f-1687428489218”
    pdf: (str) --> path-to-your-pdffile
```

**ENVIRONMENT VARIABLES (pdf indexer):**

* Here is the explanation of the Parameters:

	| APP Setting  | Value  | Note |
	|--------------|-------------|---------------|
	| AZURE_SEARCH_SERVICE_NAME |YOUR_AZURE_SEARCH_SERVICE_NAME   | Your Azure Cognitive Search service name. Fetch it from the Azure Portal.|
	| AZURE_SEARCH_KEY		    | YOUR_AZURE_SEARCH_KEY | Your Azure Cognitive Search key. Fetch it from the Azure Portal|
	| AZURE_STORAGE_ACCOUNT_KEY     | YOUR_AZURE_STORAGE_ACCOUNT_KEY   | Your Azure Storage Account Key. Fetch it from the Azure Portal |
	| AZURE_STORAGE_ACCOUNT_NAME |  YOUR_AZURE_STORAGE_ACCOUNT_NAME | Your Azure Storage Account Name. Fetch it from the Azure Storage Account Name |
    | FORM_RECOGNIZER_KEY  | YOUR_FORM_RECOGNIZER_KEY         | Azure Form Recognizer Key, Fetch it from the Azure Portal | 

> **Note:**  The below code snippet shows how you can test the environment variables by configuring them locally inside pdfindexer.py. Please add the name of the services and keys after the word “or” for each respective variable.

 ![A portion of the Azure Portal home screen is displayed with the + Create a resource tile highlighted.](media/image_env_1.png)

### Search Horizontal

This function app is used to search the response to any custom query related to the pdf indexed by the function pdfindexer function app.

*Path to build:* 'artifacts/binaries/func-search-horizontal.zip'

Extract the zip and continue with the steps below.

>**Note:** To test search horizontal, we need to have a knowledge base in the container and a search index, therefore it is mandatory to run pdf indexer before running search horizontal.

**Sample payload to test “search-horizontal” from the backend using Postman:**

*POST:*
```
http://localhost:7071/api/chat
```

*BODY:* form-data
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

*Return:* 
```
{
    **"data_points"**: [],
    "answer": "Ensuring that AI systems align with human values and ethical principles is a complex and ongoing process. Here are some steps that can be taken:\n\n1. Develop ethical guidelines: Organizations and governments can develop ethical guidelines for the development and use of AI systems. These guidelines should be based on human values and principles, such as fairness, transparency, accountability, and privacy.\n\n2. Incorporate ethical considerations into the design process: Ethical considerations should be incorporated into the design process of AI systems. This includes considering the potential impact of the system on different groups of people and ensuring that the system is designed to be fair and unbiased.\n\n3. Test and evaluate AI systems: AI systems should be tested and evaluated to ensure that they are aligned with ethical principles. This includes testing the system for bias and ensuring that it is transparent and accountable.\n\n4. Involve diverse stakeholders: Diverse stakeholders, including experts in ethics, social scientists, and representatives from different communities, should be involved in the development and deployment of AI systems. This can help ensure that the systems are aligned with human values and ethical principles.\n\n5. Regularly review and update ethical guidelines: Ethical guidelines should be regularly reviewed and updated to ensure that they remain relevant and effective in guiding the development and use of AI systems.",
    "thoughts": ""
}
```

**Example payload when searching from the knowledge base:**
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

**Example payload when searching from any uploaded documents:**
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

**ENVIRONMENT VARIABLES (search horizontal):**

* Here is the explanation of the Parameters:

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

> **NOTE:**  The below code snippet shows how you can test the environment variables by configuring them locally inside “function_app.py”. Please add the name of the services and keys after the word “or” for each respective variable.

### Campaign Generation

This function app is used to generate Instagram or Email campaigns related to the description passed in the body.

**Sample payload to test “Campaign Generation” from the backend using Postman:**

*POST:*
```
http://localhost:7071/api/CampGen
```

*BODY*: raw -> JSON
```
{
	creative_factor : (Float) —> Value between 0 to 1,
	description : (str) —> description of campaign,
	type : (str)  → type(instagram/email)
}
```

*Return:* 
```
{
    prompt: (str),
    campaign: (str),
    title : (str)
}
```

*Example Values:*

The below example is for Campaign Generation.
```
{
"creative_factor": "0.8",

"description": "Write an Instagram post for a company called Contoso. The post is for a promotion for a 50% discount on the launch of a new line of clothing. The new line focuses on minimalism. The post should include the following:\n1. A headline for the Instagram post.\n2. Choose words that communicate minimalism.\n3. A poem about how the line of clothing demonstrates minimalism.\n4. Include appropriate emojis in the post.\n5. Include relevant Hashtags.\n6. Post should contain at least 40 words.\nConsidering everything described above, give me an Instagram post with a post title, post content with appropriate hashtags and emojis. Close the post with a relevant poem as described above.",

"type": "instagram"
}
```

*Return:*
```
{
    "prompt": "Create instagram campaign on following info:Write an Instagram post for a company called Contoso. The post is for a promotion for a 50% discount on the launch of a new line of clothing. The new line focuses on minimalism. The post should include the following:\n1. A headline for the Instagram post.\n2. Choose words that communicate minimalism.\n3. A poem about how the line of clothing demonstrates minimalism.\n4. Include appropriate emojis in the post.\n5. Include relevant Hashtags.\n6. Post should contain at least 40 words.\nConsidering everything described above, give me an Instagram post with a post title, post content with appropriate hashtags and emojis. Close the post with a relevant poem as described above..",

    "campaign": "#StayMinimal 🤍 \nIntroducing our new line of minimalistic clothing from Contoso! We're celebrating the launch with a 50% discount! 🤩🎉 \n\nFocusing on subtle details, our minimalist clothing line is designed to make sure you always look on-trend. From sophisticated cuts to unique patterns, our clothing speaks for itself. 💯 \n\n#minimalismissimplicity 🤍 #Contosominimalclothing 🤍 #minimalismlifestyle 🤍 \n\nLess is more, they say,\nWe focus on the details,\nCreating a timeless look,\nIn every occasion we prevail. 🤍 #Contosominimalclothing",

    "title": "Less is More: Timeless Minimalism with ContosoMinimalClothing"
}
```

**ENVIRONMENT VARIABLES:**

* Here is the explanation of the Parameters

    | App Setting | Value  | Note |
	| ----------- | ------ | ---- |
	| AZURE_OPENAI_SERVICE_KEY| YOUR_AZURE_SEARCH_SERVICE_NAME | Your Azure Cognitive Search service name. Get it in the Azure Portal |
    | AZURE_OPENAI_SERVICE | YOUR_OPENAI_SERVICE | Get openAI service Name |  
    | AZURE_OPENAI_GPT_DEPLOYMENT | YOUR_AZURE_OPENAI_GPT_DEPLOYMENT | Get Azure openAI model deployment name |

> **Note:**  Inside "__init__.py", you can configure the environment variable locally to test as given in the below code snippet. Please add the name of the services and keys after “or” for the respective variables.

 ![A portion of the Azure Portal home screen is displayed with the + Create a resource tile highlighted.](media/img_env_1.png)

### Recommend Image

This function app is used to recommend similar images with respect to the image passed in the body.

**Sample payload to test “recommend from image” from the backend using Postman:**

*POST:* 
```
http://localhost:7071/api/recommendFromImage_V2
```

*BODY:* raw -> JSON
```
{
"image_url": (str)-->url,
"image_num": (Integer)
}
```

*Return:* 
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

*Example payload for recommendations from image:*
```
{
"image_url":"https://i.ibb.co/SvSp7F7/minimalist.png",
"image_num":"1"
}
```

*Return for Example Payload*
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

* Here is the explanation of the Parameters
    
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

 ![A portion of the Azure Portal home screen is displayed with the + Create a resource tile highlighted.](media/img_env_2.png)

### Regenerate DALL E

This function app uses DALL-E to regenerate images according to the description passed in the body in accordance with the given images.

**Sample payload to test “dalle image generation” from the backend using Postman:**

*POST:* 
```
http://localhost:7071/api/dalleimage_generation 
```

*BODY:* raw--> JSON
```
{
"dalle_prompt": (str) --> prompt for the image to be generated
}
```

*Return:* 
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

*Example payload for dalle images generation:*
```
{
"dalle_prompt":"Generate a realistic image of a convertible orange sports car on a road in a cloudy day"
}
```

*Return for Example Payload:*
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

    | APP Setting  | Value  | Note |
	|----------|-----------|-----------|
	| OPENAI_API_ENDPOINT | YOUR_OPENAI_API_ENDPOINT | Get your OpenAI API Endpoint   |
    | OPENAI_KEY  | YOUR_OPENAI_KEY | Get OpenAI key from Azure Portal |
    
> **NOTE:**  Inside image_generation.py, you can configure the environment variable locally to test as given in the below code snippet. Please add the name of the services and keys after “or” for the respective variables.

 ![A portion of the Azure Portal home screen is displayed with the + Create a resource tile highlighted.](media/img_env_3.png)


### Execution through Web App

### Scenario 1 : Azure OpenAI and Cognitive Search

### Training the Knowledge Base

1. Open the code in Visual Studio and Create an azure function using the V2 programming model in visual studio code and open the build for "func-pdf-indexer".
 
  ![A portion of the Azure Portal home screen is displayed with the + Create a resource tile highlighted.](media/image_pdf_2.png)

2. Run the function_app.py code in the visual studio using the command **“func start”** or **fn+F5** and **press** Enter key.

 ![A portion of the Azure Portal home screen is displayed with the + Create a resource tile highlighted.](media/image_pdf_2.png)

3. **Copy** the "pdfindexer" URL generated in the terminal (as indicated by the red box in this example).

```
http://localhost:7071/api/pdfindexer  - This URL can be used to test pdfindexer function app as well
```

 ![A portion of the Azure Portal home screen is displayed with the + Create a resource tile highlighted.](media/image_pdf_3.png)

4. **Open** the Postman application and **click** the "New" button to create a new "POST" request.

 ![A portion of the Azure Portal home screen is displayed with the + Create a resource tile highlighted.](media/image_pdf_4.png)

5. **Paste** the chat URL (copied from the visual studio terminal during step 3). 

 ![A portion of the Azure Portal home screen is displayed with the + Create a resource tile highlighted.](media/image_pdf_5.png)

6. **Goto** to the body option, select  “raw”, **enter** the request body and **click** on the “Send” button.

7. Make sure to provide index_name as "prod-responsibleai-search", container_name as "knowledge-base-responsibleai"and pdf as "Microsoft-Responsible-AI-Standard-v2-General-Requirements.pdf"

>**Note:** Whatever value you are providing as "index_name" and "container_name", the same should be given in the "search-horizontal" function app AppSettings

 ![A portion of the Azure Portal home screen is displayed with the + Create a resource tile highlighted.](media/image_pdf_6.png)

8. **View** the Response.

 ![A portion of the Azure Portal home screen is displayed with the + Create a resource tile highlighted.](media/image_pdf_7.png)

9. Our Knowledge Base has been trained on "Microsoft-Responsible-AI-Standard-v2-General-Requirements.pdf".

10. **Repeat** step #7, by replacing the "pdf" with the rest of the ResponsibleAI pdfs available in the package, to train the Knowledge Base completely.

### Webapp Scenario 1

1. In the Azure Portal, under resource group **search** for "app-open-ai" and **click** on the app service.

    ![image](media/scenario1_ui7.png)

2. **Click** on "Browse".

    ![image](media/scenario1_ui8.png)

3. From the left navigation bar **click** on "Azure OpenAI Chatbot for Enterprise Data".
 
 ![A portion of the Azure Portal home screen is displayed with the + Create a resource tile highlighted.](media/predefined2.png)

4. Below are the questions from the pretrained knowledge base for Azure OpenAI Chatbot for Enterprise Data.

5. **Click** on one of the queries.
 
 ![A portion of the Azure Portal home screen is displayed with the + Create a resource tile highlighted.](media/predefined1.png)

6. We will view the answer for the selected query. 

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

12. **View** the AI response. 
 
 ![A portion of the Azure Portal home screen is displayed with the + Create a resource tile highlighted ](media/predefined27.png)


### Configuring Function App for Scenario 1

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

9. **Repeat** the steps from step #13 to #19 to customize "func-pdf-indexer".

> Table for "func-pdf-indexer"

|   name    |   value   |
| --------- | --------- |
| FormRecognizerService | Your form recognizer resource name |
| FORM_RECOGNIZER_KEY | Your form recognizer primary key |
| SEARCH_SERVICE_NAME | Your search service name |
| SEARCH_SERVICE_KEY | Your search service key |
| STORAGE_ACCOUNT_NAME | Your storage account name |
| STORAGE_ACCOUNT_KEY | Your storage account key |


### Scenario 2 : Social Media Campaign and Product Recommendation

### Webapp Scenario 2

1. In the Azure Portal, under resource group **search** for "app-open-ai" and **click** on the app service.

    ![image](media/scenario1_ui7.png)

2. **Click** on "Browse".

    ![image](media/scenario1_ui8.png)

3. From the left navigation bar **click** on "Social Media Campaign & Product Recomendation".

    ![image](media/scenario2_ui1.png)

4. **Click** on the "Dropdown" and **select** "Sports Car".

    ![image](media/scenario2_ui2.png)

5. **Scroll down** and **click** on "Process".

    ![image](media/scenario2_ui3.png)

6. The response 1 is an Instagram Campaign and response 2,3 are Recommended Image generated using ResponsibleAI.

    ![image](media/scenario2_ui4.png)

7. **Click** on "Show Prompt" at right top of the screen.

    ![image](media/scenario2_ui5.png)

8. The default prompt would be "Generate a realistic image of a convertible orange sports car on a road in a sunny day"

9. **Click** on the "Edit" button.

    ![image](media/scenario2_ui6.png)

10. **Replace** the prompt with custom data for e.g. "sunny day" with "rainy day" and **click** on the "Send" button.

    ![image](media/scenario2_ui7.png)

11. The response is generated using "DALL-E 2".

    ![image](media/scenario2_ui8.png)

### Configuring Function App for Scenario 2

1. **Goto** the Azure Portal, in the resource group, **search** for "func-campaign-generator" and **click** on the function app.

    ![image](media/scenario2_1.png)

2. In the left pane, **scroll down** and **click** on "Configuration".

    ![image](media/scenario2_2.png)

3. Make sure you are on "Application settings" and **click** on "Advanced edit".

    ![image](media/scenario2_3.png)

4. **Replace** the values as shown below:

    | name  |  value |
    | ----- | ------ |
    | AZURE_OPENAI_SERVICE | Your OpenAI service name |
    | AZURE_OPENAI_SERVICE_KEY | Your OpenAI service key |
    | AZURE_OPENAI_GPT_DEPLOYMENT | Your OpenAI service model deployment name |
    | AZURE_OPENAI_CHATGPT_DEPLOYMENT | Your openAI model's engine Name |

5. **Click** on "OK" button.

    ![image](media/scenario2_4.png)

6. **Click** on "Save" button.

    ![image](media/scenario2_5.png)

7. **Click** on "Continue" button.

    ![image](media/scenario2_6.png)

8. Wait for the changes to save, **scroll up** on the left pane, **click** on "Overview" and **click** on "Restart".

    ![image](media/scenario2_7.png)

9. Similarly we can make changes to all the values for different function apps for this scenario accordingly.

10. Repeat step #12 to step #19 for other two function apps used in this scenario namely "func-recommend-images" and "func-regenerate-dalle", 

    >Table for "func-recommend-images"

    | name  |  value |
    | ----- | ------ |
    | COGNITIVE_SERVICE_API | Your cognitive service endpoint |
    | cognitive_key | Your cognitive service key |
    | ENGINE | Your openAI service deployment model name |
    | OPENAI_API_ENDPOINT | Your openAI service endpoint |
    | OPENAI_API_KEY | Your openAI service key |

    >Table for "func-regenerate-dalle"

    | name  |  value |
    | ----- | ------ |
    | OPENAI_API_ENDPOINT | Your openAI service endpoint |
    | OPENAI_API_KEY | Your openAI service key |


### Scenario 3 : Azure OpenAI with Speech Service

### Webapp Scenario 3

1. From the left navigation bar, **hover** over "Azure OpenAI with Speech Service" and **click** on "Customer Conversation".

![A portion of the Azure Portal home screen is displayed with the + Create a resource tile highlighted.](media/image_callcentre_1.png)

2. **Click** on the play button.

![A portion of the Azure Portal home screen is displayed with the + Create a resource tile highlighted.](media/image_callcentre_2.png)

3. **Click** on "Summarize Conversation".

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

### Configuring Web App for Scenario 3

1. In the Azure Portal, under resource group **search** for "app-open-ai" and **click** on the app service.

    ![image](media/scenario1_ui7.png)

2. **Scroll down** in the left pane, **click** on "Configuration", make sure you are under "Application settings" and then **click** on "Advanced edit".

    ![image](media/scenario3_ui1.png)

3. **Replace** the values as shown below according to your requirement.

    |   name    |   value   |
    | --------- | --------- |
    | Config__summarizeConversationAPI | Your openAI service name |
    | Config__summarizeConversationAPIKey | Your openAI service key |
    
>**Note:** Value for Config__summarizeConversationAPI will be in the format "https://#OPENAI_SERVICE#.openai.azure.com/openai/deployments/text-davinci-003/completions?api-version=2022-12-01". You just need to replace "#OPENAI_SERVICE#" with Your openAI service name.

4. **Click** on "OK" button.

    ![image](media/scenario3_ui2.png)

5. **Click** on "Save".

    ![image](media/scenario3_ui3.png)

6. **Click** on "Continue".

    ![image](media/scenario1_ui5.png)

7. Scroll up, **select** "Overview" and **click** on "Restart".

    ![image](media/scenario3_ui4.png)

8. Now the web app will use the updated resources.





