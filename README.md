#ChatDroid – AI Chatbot SaaS Platform

https://chatdroid.netlify.app/
https://chatdroid-bot.netlify.app/

ChatDroid is a lightweight SaaS platform that allows businesses to deploy AI-powered customer service chatbots on their websites.

The system includes:

a FastAPI backend connected to the OpenAI API
a Stripe-powered subscription system
a marketing website hosted on Netlify
an embeddable chatbot widget
a demo business website (Dean Dental)

This project demonstrates how a small AI SaaS product can be built using modern web technologies.

System Architecture
Business Website
(with embedded chatbot)
        │
        ▼
   ChatDroid API
   (FastAPI backend)
        │
        ▼
     OpenAI API

Billing and onboarding are handled through a separate marketing website.

Customer
   │
   ▼
ChatDroid Website
(Netlify)
   │
   ▼
Stripe Checkout
   │
   ▼
Customer receives chatbot setup
Components
1. Chatbot Backend

Built using FastAPI.

Responsibilities:

process user chat messages
apply client-specific prompts
communicate with OpenAI
enforce rate limits
return responses to embedded chat widgets

Example endpoint:

POST /chat

Example request:

{
  "client_id": "dean_dental",
  "message": "Do you offer Invisalign?"
}
2. Multi-Client Prompt System

Each business chatbot uses a custom prompt.

Example:

PROMPT_LIBRARY = {
   "dean_dental": "You are the AI receptionist for Dean Dental..."
}

This allows a single backend to serve multiple businesses simultaneously.

3. Stripe Subscription System

Customers subscribe through a Stripe checkout page embedded in the ChatDroid marketing site.

After subscribing they receive instructions for embedding the chatbot.

Pricing model:

$20 / month subscription
4. Marketing Website

A static HTML landing page deployed to Netlify.

Features:

product explanation
pricing
Stripe subscription integration
demo chatbot preview
5. Demo Business Website

A fictional dental clinic website used to demonstrate the chatbot.

Example business:

Dean Dental

The chatbot is embedded directly on the page to simulate a real client deployment.

Tech Stack

Backend

Python
FastAPI
OpenAI API
SlowAPI (rate limiting)
Pydantic

Frontend

HTML
CSS
JavaScript

Infrastructure

Netlify (frontend hosting)
Render (backend hosting)
Stripe (subscription billing)
Security

Sensitive credentials are stored using environment variables:

OPENAI_API_KEY

API keys are not stored in the repository.

Future Improvements
multi-tenant client dashboard
chatbot analytics
conversation history
automated client onboarding
vector database knowledge retrieval
usage-based billing
What this project demonstrates
AI API integration
SaaS product architecture
Stripe billing integration
multi-client backend design
REST API development
chatbot embedding systems
