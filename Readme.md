# Technical Documentation – Zomato RAG Chatbot

## System Architecture Overview

The project follows a modular Retrieval-Augmented Generation (RAG) architecture, consisting of:

1. **User Interface**: A simple chatbot interface built using Gradio that allows users to input natural language questions.
2. **Retriever**: A FAISS-based similarity search index retrieves relevant text chunks from a preprocessed knowledge base.
3. **Generator**: Google's `flan-t5-large` model generates final answers based on the retrieved context and the user query.
4. **Knowledge Base**: A structured JSON dataset built from scraped restaurant data, including menus, features, pricing, and more.

### High-Level Flow:

- User submits a query via the Gradio chatbot.
- FAISS retrieves the most semantically relevant chunks from the indexed restaurant data.
- The top-k retrieved chunks, along with the original query, are sent to the language model (`flan-t5-large`).
- The model generates a natural, informative response.
- The final response is returned to the user.

---

## Implementation Details and Design Decisions

### Web Scraping

- The scraper uses `requests` and `BeautifulSoup` to fetch and parse HTML content from 5–10 restaurant websites.
- Data collected includes restaurant name, location, menu items, prices, dietary labels, operating hours, and contact information.
- Scraping respects `robots.txt` policies and includes error handling.
- Output is saved in a structured JSON format (`restaurant_data.json`) for downstream processing.

### Preprocessing and Indexing

- Text chunks are extracted from the scraped data and cleaned for redundancy.
- Sentence embeddings are generated using the `sentence-transformers/all-MiniLM-L6-v2` model.
- FAISS is used to index the embeddings and enable fast, vector-based retrieval.
- Each chunk is stored with metadata (restaurant name, category) to support detailed queries.

### RAG Chatbot

- Retrieval uses FAISS to get the top-k relevant chunks.
- The user query and top documents are formatted into a prompt for the `flan-t5-large` model from Hugging Face.
- The chatbot is designed to answer diverse query types, such as dietary restrictions, menu comparisons, and price-based filtering.
- Ambiguous or out-of-scope queries are handled with default fallback messages.
- The interface is built using Gradio for ease of testing and demonstration.

---

## Challenges Faced and Solutions Implemented

| Challenge                                  | Solution                                                                 |
|-------------------------------------------|--------------------------------------------------------------------------|
| Some sites had anti-scraping measures     | Selected scrape-friendly websites; handled failures gracefully          |
| Inconsistent formatting across menus      | Wrote custom parsers and normalization logic                            |
| No GPU for model inference                | Used flan-t5-large for a balance of quality and CPU compatibility       |
| Ambiguous or broad queries                | Used top-k FAISS retrieval and fallback handling                        |
| Limited data variety                      | Augmented dataset across different cuisines and formats                 |

---

## Future Improvement Opportunities

### Model and Response Quality

- Use more advanced LLMs like `flan-t5-xl`, `LLaMA 2`, or `GPT-4` for improved fluency and context understanding.
- Fine-tune models specifically on food/restaurant-related datasets for higher relevance.

### Scalability and Deployment

- Move retrieval and inference to GPU-backed cloud infrastructure.
- Use cloud-hosted FAISS alternatives like Pinecone or Weaviate for horizontal scaling.

### Data and Feature Expansion

- Expand scraping to hundreds or thousands of restaurants using asynchronous scraping frameworks.
- Integrate APIs (e.g., Zomato if available) for real-time menus and availability.

### UI and Experience

- Add voice input and multilingual support.
- Store session history for contextual multi-turn conversations.
- Implement feedback-based retraining using user thumbs-up/down.

---

## Conclusion

This solution demonstrates how to combine traditional web scraping with modern NLP techniques to create an intelligent restaurant query assistant. It is modular, reproducible, and scalable with further enhancements. With richer data and more compute, it could evolve into a production-ready Zomato chatbot or in-app assistant.

