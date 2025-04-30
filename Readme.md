# Zomato RAG Chatbot – Nuggets Assignment

This project implements a Retrieval-Augmented Generation (RAG) chatbot capable of answering natural language queries about restaurants using real-world scraped data. The goal is to simulate how Zomato users might search for information about menus, dietary options, pricing, and more through an intelligent AI assistant.

---

## Features

- Scrapes data from real restaurant websites (name, location, menu, prices, dietary features).
- Converts scraped data into a structured JSON-based knowledge base.
- Indexes the data using FAISS for semantic retrieval.
- Uses Google's `flan-t5-large` model via Hugging Face Transformers for response generation.
- Accepts user questions through a simple Gradio interface.
- Handles various types of queries such as:
  - "Which restaurant offers vegan options?"
  - "Compare desserts at Restaurant A vs B."
  - "Does ABC have gluten-free appetizers?"

---

## Project Structure

<pre> ## Project Structure ``` Zomato-Nuggets-_Task/ ├── Zomato_RAG_Chatbot.ipynb # Full pipeline (scraper, retriever, generator, UI) ├── restaurant_data.json # Structured output of scraped data ├── requirements.txt # Python dependencies ├── README.md # Project overview and instructions ├── technical_doc.md # Detailed system design and architecture └── demo_video_link.txt # Link to 3-minute walkthrough video ``` </pre>

### Step 1: Clone the repository

```bash
git clone https://github.com/srivastavaapurb/Zomato-Nuggets-_Task.git
cd Zomato-Nuggets-_Task

### Step 2: Install dependencies

pip install -r requirements.txt

### Step 3: Launch the notebook

jupyter notebook Zomato_RAG_Chatbot.ipynb
