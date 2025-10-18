Here is a step-by-step beginner project guide to build a Retrieval-Augmented Generation (RAG) copilot on Azure using Azure AI Foundry:

1. **Set up your Azure AI Foundry project and environment:**
   - Create a hub-based project in Azure AI Foundry.
   - Deploy two necessary models: the Azure OpenAI chat model `gpt-4o-mini` and the embedding model `text-embedding-ada-002`.
   - Create an Azure AI Search service with a Basic or higher pricing tier to index your knowledge base.
   - Connect the Azure AI Search service to your AI Foundry project.

2. **Set up your local development environment:**
   - Install Python 3.9 or higher.
   - Create and activate a Python virtual environment.
   - Create a `requirements.txt` file with these packages:
     ```
     azure-ai-projects==1.0.0b10
     azure-ai-inference[prompts]
     azure-identity
     azure-search-documents
     pandas
     python-dotenv
     opentelemetry-api
     ```
   - Install the packages using `pip install -r requirements.txt`.
   - Create a helper script `config.py` for environment variables and logging setup.

3. **Configure environment variables:**
   - Create a `.env` file with your Azure AI Foundry project connection string and model/search names, for example:
     ```
     AIPROJECT_CONNECTION_STRING=<your-connection-string>
     AISEARCH_INDEX_NAME="example-index"
     EMBEDDINGS_MODEL="text-embedding-ada-002"
     INTENT_MAPPING_MODEL="gpt-4o-mini"
     CHAT_MODEL="gpt-4o-mini"
     EVALUATION_MODEL="gpt-4o-mini"
     ```

4. **Install Azure CLI and login:**
   - Install Azure CLI for your OS.
   - Login using `az login` or device code login.
   - Keep the terminal open to run your Python scripts.

5. **Next steps (not included here):**
   - Build and configure your RAG copilot chat app with the SDK and deployed models.
   - Index your knowledge documents in Azure AI Search.
   - Implement retrieval and query logic to augment responses with relevant knowledge from your indexed data.

6. **Clean up:**
   - Delete any created Azure resources after finishing to avoid unnecessary costs.

This project teaches how to combine Azure OpenAI chat and embeddings models with Azure AI Search for a custom knowledge-augmented chatbot, following Azure's recommended SDK and project structure for 2025 development. The detailed code and instructions are available on Microsoft Learn's Azure AI Foundry tutorials [1].

Sources
[1] Part 1: Set up project and development environment to build a ... https://learn.microsoft.com/en-us/azure/ai-foundry/tutorials/copilot-sdk-create-resources
