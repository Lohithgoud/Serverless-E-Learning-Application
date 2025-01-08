# Serverless e-Learning Application Using Amazon Bedrock

This project implements a Serverless e-Learning Application that leverages Amazon Bedrock for knowledge retrieval and natural language response generation. The application is designed to answer user questions based on a robust knowledge base, such as technical documentation or training materials. It is particularly suited for educational and training environments.

---

## 🖋️ Project Overview
This application provides instant, accurate answers to user queries by combining multiple AWS services. It processes questions, retrieves relevant content, and generates responses based on stored documents, making it ideal for environments requiring detailed topic-specific answers (e.g., Amazon EBS storage queries).

---

## 🛠️ Key Components and Workflow

### 1. User Prompt (Question)
- Users interact via Streamlit, submitting questions like:
  - “Which EBS volume to use for high IOPS?”
- The question is sent into the system for processing.

### 2. AWS API Gateway
- Acts as a secure entry point for the user’s question.
- Handles HTTP requests and forwards them to AWS Lambda for processing.

### 3. AWS Lambda
- The core processing unit that:
  - Receives the user’s question.
  - Calls the RetrieveAndGenerate API to query the Knowledge Base.
  - Returns the generated response to the API Gateway.

### 4. Knowledge Base for Bedrock
- **Components:**
  - **S3 Bucket:**
    - Stores source documents (e.g., PDFs containing product guides or specifications).
  - **Chunking:**
    - Documents are divided into smaller "chunks" for efficient retrieval.
  - **Vector Store (AWS OpenSearch):**
    - Stores document chunks in a vector database for similarity-based retrieval.
  - **Amazon Titan (RAG - Retrieval-Augmented Generation):**
    - Retrieves relevant chunks and combines them for response generation.

### 5. Claude FM on Amazon Bedrock
- A large language model (LLM) hosted on Amazon Bedrock.
- Processes relevant chunks from the Knowledge Base.
- Generates accurate, natural language responses using the retrieved context.

---

## 🔄 Process Flow Summary
1. **User submits a question via Streamlit → API Gateway forwards it to AWS Lambda.**
2. **AWS Lambda:**
   - Processes the question.
   - Calls the RetrieveAndGenerate API.
3. **The RetrieveAndGenerate API queries the Knowledge Base:**
   - AWS OpenSearch finds relevant chunks using vector similarity.
   - Amazon Titan combines retrieval and generation.
4. **Claude FM processes the context and generates the response.**
5. **AWS Lambda returns the response to API Gateway, which delivers it to the user.**

---

## 🌟 Features

- **Serverless architecture:** Scales automatically with demand.
- **Knowledge retrieval:** Efficiently retrieves only relevant sections of documents.
- **Natural language processing:** Generates user-friendly responses.
- **Cost-effective:** Utilizes pay-as-you-go AWS services.

---

## 🚀 Getting Started

### Prerequisites
- AWS account with access to services like S3, API Gateway, Lambda, OpenSearch, and Amazon Bedrock.
- Streamlit installed locally for frontend development.

### Deployment Steps

#### 1. Set up AWS services:
- Create an S3 bucket and upload your source documents (e.g., PDFs).
- Set up API Gateway and Lambda function.
- Configure OpenSearch and Bedrock access.

#### 2. Build and deploy the Streamlit app:
- Clone the repository and navigate to the project directory.
- Run `streamlit run app.py` to start the local development server.

