# Azure-Cosmos-MongoDB-vcore-Chatbot
Comprehensive Guide to Creating an Azure Chatbot Using Your CSV/Excel/JSON with Azure Cosmos MongoDB vCore
Prerequisites
Active Azure Subscription

Ensure you have an active Azure subscription to proceed.
Request Azure OpenAI Service

You need access to the Azure OpenAI service. Fill out the request form provided by Microsoft to gain access. (The form is attached in the notebook file.)
Create an Embedding Model

Inside Azure, create an embedding model using text-embedding-ada-002.
Collect the endpoint, key, and API version for this model.
Setting Up the Database
Create Azure Cosmos MongoDB vCore Database
Set up a Cosmos MongoDB vCore database in your Azure portal.
Access and note down the connection string for the database.
Instructions
Install Required Libraries

Ensure you have the necessary Python libraries installed. You can install them using:
bash
Copy code
pip install azure-cosmos pymongo pandas openai
Configure Your Environment

Store your Azure OpenAI model endpoint, key, API version, and Cosmos MongoDB connection string securely. You can use environment variables for this purpose.
Prepare Your Data

Ensure your data is in CSV, Excel, or JSON format. Load this data into a Pandas DataFrame for processing.
Run the Jupyter Notebook

Open the provided Jupyter Notebook file and follow the steps to:
Connect to your Cosmos MongoDB database.
Create a collection within the database.
Generate and store vector indices using the embedding model.
Load your CSV/Excel/JSON data into the database.
Create the Chatbot

Develop the chatbot logic to query the database and retrieve relevant information.
Use the Azure OpenAI model to process and respond to user queries.
Code Example
Here's a brief example to get you started:

python sample code
import pandas as pd
from azure.cosmos import CosmosClient
import openai

# Load your data
data = pd.read_csv('your_data.csv')

# Connect to Cosmos DB
cosmos_url = "YOUR_COSMOS_DB_URL"
cosmos_key = "YOUR_COSMOS_DB_KEY"
client = CosmosClient(cosmos_url, credential=cosmos_key)
database = client.get_database_client('your_database_name')
container = database.get_container_client('your_container_name')

# Example to insert data into Cosmos DB
for index, row in data.iterrows():
    container.upsert_item(dict(row))

# Initialize OpenAI
openai.api_type = "azure"
openai.api_base = "YOUR_OPENAI_ENDPOINT"
openai.api_key = "YOUR_OPENAI_KEY"
openai.api_version = "YOUR_API_VERSION"

# Example query to the embedding model
response = openai.Embedding.create(
    input="your text to embed",
    engine="text-embedding-ada-002"
)

print(response)
Additional Resources
Azure Cosmos DB Documentation
Azure OpenAI Service Documentation
Feel free to reach out if you have any questions or need further assistance!


