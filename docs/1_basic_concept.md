# Partner Frontier AI Workshop

## Understanding Microsoft Agent Framework Basic Concepts with Code Samples

### Creating Microsoft Foundry

Azure AI Foundry was rebranded to Microsoft at Microsoft Ignite in November. In this step, we will create a Microsoft Foundry resource in the Azure Portal and deploy the GPT-4.1 model.

1. Enter Microsoft Foundry in the Azure Portal search bar.

    <img src="images/step1-01.png" width="400"/>

2. Create a Microsoft Foundry resource.

    <img src="images/step1-02.png" width="720"/>

3. Select and enter the subscription, resource group, and resource name, and choose "East US" for the region. Leave the project name as default. Set other tabs like network to default values and click the "Create" button to create the resource.

    <img src="images/step1-03.png" width="600"/>

4. Once creation is complete, you will be directed to the default project. You can see the Endpoint and Key values of the Microsoft Foundry Project. Click "Models + endpoints" in the left menu to deploy a model.

    <img src="images/step1-04.png" width="720"/>

5. In this lab, we will use the gpt-4.1 model. If your subscription lacks sufficient quota, you can use other AOAI models such as gpt-4.1-mini.

    <img src="images/step1-05.png" width="600"/>

6. Select "Global Standard" for Deployment type, choose defaults for other values, and deploy. Select "gpt-4.1" as the deployed model name, or if you change the name, record that name. You will need it in the code samples later.

    <img src="images/step1-06.png" width="500"/>

7. Once the model deployment is complete, you can test the model in the Chat Playground. Click "Chat playground" in the left menu. Select the model name you just deployed from the model name dropdown, enter "Hello, Microsoft Foundry!" in the prompt, and click the "Submit" button.

    <img src="images/step1-07.png" width="720"/>

8. Click the "View code" button to see the Azure OpenAI endpoint. Record this value and use it in the environment variable setup in the next step.

    <img src="images/step1-08.png" width="600"/>

### Creating Bing Grounding

In this step, we will create a Bing Grounding resource. Bing Grounding is a web search tool provided by the Microsoft Agent Framework that helps agents search for real-time information.

1. Enter Bing Resource in the Azure Portal search bar.

    <img src="images/step2-01.png" width="400"/>

2. Click the "+Add" button and select "Grounding with Bing Search" to create a Bing Grounding resource.

    <img src="images/step2-02.png" width="400"/>

3. Select and enter the subscription, resource group, and resource name, and choose "Global" for the region. Select the default pricing tier and click the "Review + create" button to create the resource.

    <img src="images/step2-03.png" width="600"/>

4. Once resource creation is complete, click the "Go to resource" button to navigate to the resource page. Since the Bing Grounding resource is used in the Microsoft Foundry Portal, navigate to the Foundry Portal.

    <img src="images/step2-04.png" width="600"/>

5. Click "Management Center" in the Foundry Portal.

    <img src="images/step2-05.png" width="600"/>

6. Select "Connected Resources" from the left menu and click the "Create Connection" button.

    <img src="images/step2-06.png" width="600"/>

7. Select "Bing Grounding" from the Asset type.

    <img src="images/step2-07.png" width="600"/>

8. Select the Bing Grounding resource you created in the previous step and click the "Add connection" button.

    <img src="images/step2-08.png" width="600"/>

9. Once the connection is complete, you can see the Bing Grounding connection you just created in the connected resources list. Click on the Grounding Name to view detailed information.

    <img src="images/step2-09.png" width="600"/>

10. Record the Connection ID of the connected Bing Grounding resource. You will need it in the code samples later.

### Implementing Agent Framework in Code

Now that you have created all the Azure resources you will use, move on to the step of implementing the Microsoft Agent Framework in code.

1. Setting Environment Variables

In this step, set the information of the Microsoft Foundry and Bing Grounding resources created earlier as environment variables. Change the ./1_basic_agent/.env.sample file to ./1_basic_agent/.env and enter the Azure OpenAI, Foundry Project, and Bing Grounding information.

2. Running Code Samples

The code samples are provided in Jupyter Notebook format. Open the 1_basic-concept-with-msaf.ipynb file and execute each cell in order to understand the basic concepts of the Microsoft Agent Framework. In this lab, we cover the following three cases:

* Case 1: Creating and Running Basic Agents
* Case 2: Agents Using Custom Tools/Functions
* Case 4: Enterprise Tools Using Azure AI Agent Client

The [original repository](https://github.com/Azure/agent-innovator-lab/blob/main/0_basic-agent/AgentFramework/README.md) also includes Case 3: Understand the differences b/w Agent Clients (Azure OpenAI Chat Client vs Azure AI Agent Client), so we recommend practicing the entire code when you have time.

If you have executed all the code in the 1_basic-concept-with-msaf.ipynb file, you can proceed to Part 2.

## Next Steps

* [Hands-on Lab 0 – Setup](2_00_setup.md)

## Lab Sequence

### Part 1
* [Microsoft Agent Framework Basic Concept HoL](00_basic_concept.md)

### Part 2
* [Hands-on Lab 0 – Setup](2_00_setup.md)
* [Hands-on Lab 1 – MCP Server](2_01_mcp_uv.md)
* [Hands-on Lab 2 – Backend](2_02_backend_uv.md)
* [Hands-on Lab 3 – Frontend](2_03_frontend.md)
