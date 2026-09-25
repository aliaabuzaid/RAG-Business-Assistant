# RAG WhatsApp Business Assistant

An AI-powered WhatsApp business assistant that uses Retrieval-Augmented Generation (RAG), structured business data, and workflow automation to provide accurate customer support and sales assistance.

## Overview

This project demonstrates how an AI agent can combine:

* WhatsApp conversations
* Business knowledge through RAG
* Real-time data from a database
* Workflow automation
* Product and stock information
* Delivery information
* Customer and order workflows

The goal is to build a practical AI assistant that can answer customer questions while using reliable business data instead of relying only on the language model.

## Business Flow

```text
Customer
   ↓
WhatsApp
   ↓
Evolution API
   ↓
n8n
   ↓
AI Agent
   ├── RAG Knowledge Base
   ├── Product Data
   ├── Stock Tool
   ├── Delivery Tool
   └── Business Data
   ↓
Customer Response
```

## Key Features

### WhatsApp AI Assistant

* Handles customer conversations through WhatsApp
* Uses simple and natural Arabic
* Provides short and helpful responses
* Understands common customer questions
* Supports sales and customer-service conversations

### RAG Knowledge Base

The assistant can retrieve business information such as:

* Brand information
* Products and services
* Payment methods
* Delivery policies
* Return policies
* Frequently asked questions
* Customer-service information

The knowledge base is stored as documents with vector embeddings and retrieved when relevant information is needed.

### Real-Time Business Data

Operational information is kept in structured database tables instead of the RAG knowledge base.

Examples include:

* Products
* Product variants
* Stock
* Delivery zones
* Distributors
* Customers
* Orders

This separation helps keep frequently changing business data up to date.

### Delivery Information

Delivery fees and delivery times are retrieved from structured delivery-zone data.

The AI assistant should not invent delivery prices when the requested location is unavailable.

### Sales Workflow

The assistant can:

1. Understand the customer's request
2. Search for relevant product information
3. Check product availability
4. Provide delivery information
5. Collect required order details
6. Confirm the order with the customer
7. Process the order through the automation workflow

Orders are created only after explicit customer confirmation.

## RAG Architecture

```text
Business Documents
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
WhatsApp Response
```

## Database Architecture

Structured operational data is separated from the knowledge base.

```text
Supabase
│
├── Products
├── Product Variants
├── Customers
├── Orders
├── Order Items
├── Delivery Zones
├── Distributors
└── Documents + Embeddings
```

## Automation Architecture

```text
WhatsApp
   ↓
Evolution API
   ↓
Webhook
   ↓
n8n
   ↓
Customer Processing
   ↓
AI Agent
   ├── RAG Retrieval
   ├── Stock Check
   ├── Delivery Check
   └── Business Tools
   ↓
Response
   ↓
WhatsApp
```

## Tech Stack

| Technology    | Purpose                      |
| ------------- | ---------------------------- |
| n8n           | Workflow automation          |
| OpenAI        | AI model and embeddings      |
| Supabase      | Database and vector storage  |
| PostgreSQL    | Structured business data     |
| pgvector      | Vector similarity search     |
| Evolution API | WhatsApp integration         |
| RAG           | Business knowledge retrieval |
| REST APIs     | External integrations        |
| Webhooks      | Event-driven automation      |

## Important Design Principles

### Use RAG for Knowledge

Stable business information such as policies, FAQs, and brand information can be stored in the knowledge base.

### Use Database Tools for Live Data

Frequently changing information such as:

* Stock
* Delivery fees
* Product availability
* Customers
* Orders

should be retrieved from structured database tables.

### Do Not Invent Business Information

The AI assistant should not guess:

* Product prices
* Stock quantities
* Delivery fees
* Policies
* Order information

When information is unavailable, the assistant should clearly communicate that it needs confirmation or additional information.

## Example Conversation

```text
Customer:
عايز كريم للترطيب

AI Assistant:
أكيد 🌸 عندنا كريم ريحانة للترطيب.
تحبي أعرفك بالسعر والتفاصيل؟

Customer:
أيوه

AI Assistant:
السعر  ... 
والكمية المتوفرة حاليًا ...

Customer:
عايزة واحد

AI Assistant:
تمام. ممكن ترسلي الموقع ورقم التواصل عشان نجهز الطلب؟

Customer:
تمام، أكّد الطلب

AI Assistant:
تم تأكيد طلبك بنجاح.
```

## Security

This repository is intended for portfolio demonstration.

Do not store:

* API keys
* Database passwords
* WhatsApp credentials
* Webhook secrets
* Real customer information
* Production credentials

Credentials should be managed through n8n credentials, environment variables, or secure secret management.

## Project Purpose

This project demonstrates how RAG, AI agents, structured business data, and workflow automation can be combined to build practical WhatsApp business assistants.

---

### Built by Alia Abuzaid

AI Automation Developer | AI Agents | n8n | RAG | WhatsApp Automation
