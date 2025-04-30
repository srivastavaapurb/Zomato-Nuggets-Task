# Zomato RAG Chatbot – Gen AI Assignment

This project is an end-to-end Retrieval-Augmented Generation (RAG) chatbot designed to answer natural language questions about restaurants using real, scraped data. It simulates how Zomato users could ask detailed queries about restaurant menus, dietary options, prices, and more—and receive smart, contextual responses.

---

## Features

- ✅ Scrapes restaurant data (name, location, menu, features, etc.)
- ✅ Builds a structured knowledge base for retrieval
- ✅ Uses FAISS to index and retrieve relevant restaurant info
- ✅ Generates responses using Google's `flan-t5-large` model
- ✅ Includes a Gradio interface for chatbot interaction
- ✅ Handles dietary, price, and menu-related queries

---

## Sample Questions the Bot Can Answer

- “Which restaurant has a particular dish xyz?”
- “Price of a dish B in restaurant A?”
- “What is the most affordable restaurant for a particular dish?”
- “Is Veg food available at a restaurant?”

---

## Project Structure

Zomato_RAG_Chatbot/ ├── scraper/ │ └── scrape.py # Web scraping logic ├── data/ │ └── restaurant_data.json # Cleaned scraped data ├── rag_chatbot/ │ ├── chatbot.py # RAG chatbot logic │ └── vector_index.faiss # Vector index for retrieval ├── Zomato_RAG_Chatbot.ipynb # Jupyter notebook (full workflow) ├── requirements.txt └── README.md

##  How to Run

git clone https://github.com/srivastavaapurb/Zomato-Nuggets-_Task.git
cd Zomato-Nuggets-_Task
pip install -r requirements.txt
