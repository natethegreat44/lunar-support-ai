# Lunar Support AI

Lunar Support AI is a service chatbot built on Google Cloud. It it meant to be used as an example and re-purposed with your own customizations and wrapped in your own prod security, organizational standards, and best practices. It leverages Google's Gemini LLM to provide grounded and curated responses to customer inquiries. The chatbot is designed to integrate with your own knowledge bases and vector stores, ensuring that your customer questions get answered based on grounded information.

## Features

- **AI-Powered Responses**: Utilize Google's Gemini model to generate natural and context-aware responses.
- **Custom Knowledge Base Integration**: Retrieve information from your own custom knowledge bases to provide tailored support.
- **Vector Store Integration**: Access and search through vector stores for complex queries, improving response accuracy.
- **Scalable Infrastructure**: Built on Google Cloud, ensuring high availability and scalability to meet your business needs.
- **Easy Deployment**: Simple setup and deployment process using Google Cloud services.

## Getting Started

### Prerequisites

Before you begin, ensure you have the following:

- A Google Cloud account
- Access to Google Cloud's Vertex AI
- Access to the Gemini API
- A custom knowledge base or vector store (optional, but recommended)
- Google Cloud SDK installed on your dev environment

### Quickstart

1. **Clone the Repo**

   ```bash
   git clone https://github.com/zaratsian/lunar-support-ai.git
   cd lunar-support-ai
   ```

2. Copy the `.env.sample` and set the env vars

   ```bash
   # Copy .env.sample
   cp .env.sample .env

   # TODO: Update the .env with your own GCP project details, images, and other variables.

   # Set the env vars
   . .env
   ```

3. Create BigQuery Dataset

   ```bash
   bq --location=us-central1 mk --dataset ${BQ_DATASET_ID}
   ```

4. Retrieve and load your web data

   ```bash
   cd scripts
   python3 load_data_website.py <url>
   ```

5. Retrieve and load your article data

   ```bash
   cd scripts
   python3 load_data_articles.py <url>
   ```

6. Setup BQ Vertex AI Connection and Embeddings Model

   ```bash
   cd scripts
   ./bq_embeddings_setup.sh
   ```

7. Deploy application

   ```bash
   cd app
   ./deploy_run.sh
   ```

Once the app is deployed, you'll see the service running within Cloud Run, then you'll be able to go to that URL in your browser and test out the application. 

Note: Depending on your organization's policies, Cloud Run services may not be exposed publicly as unauthenticated services. Always exercise caution with publicly accessible URLs and applications.

### License

This project is licensed under the Apache License 2.0. You are free to clone, modify, and use this project as-is, in accordance with the terms of the license.


### Disclaimer

This repository is provided "as-is" under the Apache License 2.0. We assume no liability for any damages or issues that may arise from its use. It is your responsibility to test the code thoroughly before deploying it in a production environment.


### Contributing

Contributions are welcome! Please fork the repository and create a pull request with your changes. Make sure to update tests as appropriate.





