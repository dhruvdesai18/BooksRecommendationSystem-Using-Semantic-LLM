# 📚 Book Recommendation System using LLM(Semantic)

## 👤 About Me

Hi, I'm **Dhruv Atul Desai**, a Computer Engineering graduate with a strong interest in **Data Science, Machine Learning**, and building intelligent systems that solve real-world problems. I enjoy working on projects that combine **NLP, recommendation systems, and LLMs** to create intuitive user experiences.

---

## 🚀 Project Overview

This project is a **Book Recommendation System** that utilizes **semantic search** to suggest books based on user queries and category filters. It leverages modern NLP tools such as **LangChain**, **FAISS vector store**, and **Hugging Face Sentence Transformers** to enable **efficient, local, and cost-free querying** of book data.

Users can:
- Search for books using keywords
- Filter by categories (like "Fiction", "Suspense", etc.)
- Get context-aware recommendations instantly via a web interface (built using Gradio)

---

## 🧠 Tech Stack

- **LangChain**: Framework for working with language models and vectorstores
- **FAISS**: Local vector similarity search (fast and free)
- **Hugging Face Embeddings**: `all-MiniLM-L6-v2` for semantic vectorization
- **Gradio**: For building the user interface
- **Pandas**: For data handling and preprocessing

---

## 💡 How It Works

1. Book data is loaded from a `.csv` file and cleaned.
2. Documents are chunked using `RecursiveCharacterTextSplitter`.
3. Each chunk is embedded using `sentence-transformers/all-MiniLM-L6-v2`.
4. Embedded vectors are stored and indexed in a FAISS vectorstore.
5. On search, user input is embedded and queried against FAISS to return the most semantically similar books.

---

## ❌ Challenges Faced

### 1. **Slow Performance with OpenAI Embeddings**
- Initially used `OpenAIEmbeddings` which caused high latency due to network calls and API rate limits.
- ✅ **Solution**: Switched to `HuggingFaceEmbeddings` with FAISS for local, high-speed embeddings — removed the need for API keys and cut down processing time drastically.

### 2. **Sorting Category Errors**
- Got the error: `TypeError: '<' not supported between instances of 'float' and 'str'` while sorting book categories.
- ✅ **Solution**: Used `fillna("Unknown")` to handle `NaN` values and ensure all entries are strings before sorting.

### 3. **Gradio Search Crashes**
- Crashed when empty input or invalid data was passed during search.
- ✅ **Solution**: Added input validation and string coercion to avoid runtime crashes.

### 4. **Deprecation Warning for HuggingFaceEmbeddings**
- LangChain deprecated the original `HuggingFaceEmbeddings` import.
- ✅ **Solution**: Migrated to the new `langchain-huggingface` package as recommended.

---



## 📸 Screenshots

<img width="1440" alt="Screenshot 2025-05-06 at 1 18 47 PM" src="https://github.com/user-attachments/assets/ef36e196-df6c-409f-aa8a-6286f85bcac1" />

<img width="1440" alt="Screenshot 2025-05-06 at 1 19 07 PM" src="https://github.com/user-attachments/assets/55cca2da-2539-453e-bf47-c28d28a908ab" />

<img width="1440" alt="Screenshot 2025-05-06 at 1 19 55 PM" src="https://github.com/user-attachments/assets/38483c21-2fd1-4028-a033-c603d11fbaa4" />


---

## 🛠️ Installation & Run

```bash
# Clone the repo
git clone https://github.com/dhruvdesai18/BooksRecommendationSystem-Using-Semantic-LLM

cd BooksRecommendationSystem-Using-Semantic-LLM

# Set up virtual environment
python -m venv .venv
source .venv/bin/activate  # on Mac/Linux
# .venv\Scripts\activate    # on Windows

# Install dependencies
pip install -r requirements.txt

# Run the app
python app.py
