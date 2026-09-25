# RAG Business Assistant

An AI-powered business assistant that uses Retrieval-Augmented Generation (RAG) to retrieve relevant information from a business knowledge base and provide grounded, context-aware answers.

## Overview

This project demonstrates how RAG can be used to connect an AI assistant with a company's internal knowledge.

Instead of relying only on the language model's general knowledge, the assistant retrieves relevant business documents and uses them as context before generating a response.

The project focuses on:

* Knowledge retrieval
* Semantic search
* Vector embeddings
* Context-aware AI responses
* Business knowledge management
* WhatsApp as a conversational interface

## How It Works

```text
Business Knowledge
       ↓
Documents
       ↓
Text Processing
       ↓
OpenAI Embeddings
       ↓
Vector Database
       ↓
Semantic Search
       ↓
Relevant Context
       ↓
AI Agent
       ↓
Grounded Response
       ↓
WhatsApp
```

## Key Features

### Knowledge Base

The assistant can work with business information such as:

* Company information
* Products and services
* Frequently asked questions
* Policies
* Payment information
* Delivery policies
* Return policies
* Customer support information

### Semantic Search

User questions are converted into embeddings and compared with stored document embeddings to retrieve the most relevant information.

This allows the assistant to find relevant content even when the customer's wording does not exactly match the original document.

### Grounded AI Responses

Retrieved documents are provided to the AI agent as context.

The assistant is instructed to:

* Use retrieved information when answering
* Avoid inventing business information
* Distinguish unavailable information
* Ask for clarification when necessary
* Keep responses concise and natural

### WhatsApp Interface

WhatsApp is used as the conversational interface for interacting with the assistant.

```text
Customer
   ↓
WhatsApp
   ↓
Evolution API
   ↓
n8n
   ↓
RAG Retrieval
   ↓
AI Agent
   ↓
Response
   ↓
WhatsApp
```

## RAG Architecture

```text
                 ┌──────────────────────┐
                 │  Business Documents  │
                 └──────────┬───────────┘
                            ↓
                 ┌──────────────────────┐
                 │   Text Processing    │
                 └──────────┬───────────┘
                            ↓
                 ┌──────────────────────┐
                 │  OpenAI Embeddings   │
                 └──────────┬───────────┘
                            ↓
                 ┌──────────────────────┐
                 │ Supabase + pgvector  │
                 └──────────┬───────────┘
                            ↑
                            │
                     Semantic Search
                            ↑
                            │
                 ┌──────────┴───────────┐
                 │     User Question    │
                 └──────────┬───────────┘
                            ↓
                 ┌──────────────────────┐
                 │      AI Agent        │
                 └──────────┬───────────┘
                            ↓
                 ┌──────────────────────┐
                 │   Grounded Answer    │
                 └──────────────────────┘
```

## Knowledge vs. Operational Data

One of the main design principles of this project is separating **knowledge** from **live business data**.

### Knowledge Base

RAG is suitable for relatively stable information such as:

```text
Company Information
FAQs
Policies
Payment Methods
Return Policy
Service Information
Delivery Policy
```

### Operational Data

Frequently changing information should remain in structured database tables or dedicated tools.

Examples:

```text
Stock
Orders
Customers
Delivery Fees
Product Availability
Transactions
```

This separation helps keep the knowledge base clean and prevents outdated operational information from being treated as permanent knowledge.

## Example Query

```text
Customer:
ما هي سياسة الاسترجاع؟

        ↓

Question Embedding

        ↓

Vector Search

        ↓

Relevant Policy Document

        ↓

AI Agent

        ↓

Answer based on retrieved context
```

## Example Knowledge Retrieval

```text
Query:
هل يمكنني إرجاع المنتج بعد استلامه؟

Retrieved Context:
Return Policy
- Customers can request a return according to the
  company's return conditions.
- Return requests must follow the stated policy.

AI Response:
أكيد. يمكن طلب الاسترجاع وفقًا لسياسة الاسترجاع
والشروط المحددة من الشركة.
```

## Tech Stack

| Technology    | Purpose                     |
| ------------- | --------------------------- |
| n8n           | Workflow automation         |
| OpenAI        | LLM and embeddings          |
| Supabase      | Database and vector storage |
| PostgreSQL    | Structured data             |
| pgvector      | Vector similarity search    |
| Evolution API | WhatsApp integration        |
| RAG           | Knowledge retrieval         |
| REST APIs     | System integration          |
| Webhooks      | Event-driven communication  |

## Automation Workflow

```text
WhatsApp Message
       ↓
Evolution API
       ↓
n8n Webhook
       ↓
Process User Question
       ↓
Generate Embedding
       ↓
Search Vector Database
       ↓
Retrieve Relevant Documents
       ↓
Pass Context to AI Agent
       ↓
Generate Response
       ↓
Send Response to WhatsApp
```

## Design Principles

### 1. Retrieve Before Generating

The assistant retrieves relevant business information before generating an answer.

### 2. Do Not Invent Information

If the required information cannot be found in the knowledge base, the assistant should not fabricate an answer.

### 3. Separate RAG from Live Data

RAG handles business knowledge, while structured tools and database queries handle frequently changing operational information.

### 4. Keep Responses Grounded

The AI should base its answers on the retrieved business context whenever the question relates to company-specific information.

### 5. Keep the Knowledge Base Maintainable

Business documents should be organized so that information can be updated without changing the AI agent's core logic.

## Security

This repository is intended for portfolio demonstration.

Do not store:

* API keys
* Database passwords
* WhatsApp credentials
* Webhook secrets
* Private business information
* Real customer data

Credentials should be managed through secure n8n credentials, environment variables, or secret management systems.

## Project Purpose

This project demonstrates how Retrieval-Augmented Generation can connect AI assistants to real business knowledge.

It focuses on the architecture behind reliable AI knowledge retrieval rather than building a complete sales or order-management system.

---

### Built by Alia Abuzaid

AI Automation Developer | AI Agents | n8n | RAG | Business Automation
