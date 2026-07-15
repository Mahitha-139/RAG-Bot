Local RAG Chatbot with LangChain & Gemini
A lightweight, local Retrieval-Augmented Generation (RAG) chatbot. It reads a local text file, converts the content into vector embeddings, and answers user queries strictly using the provided context via the Google Gemini API.
🚀 Features
Local Knowledge Base: Reads and processes any custom knowledge.txt file.
Smart Text Splitting: Uses RecursiveCharacterTextSplitter to handle long documents efficiently.
Free Local Embeddings: Converts text to vectors using the HuggingFace all-MiniLM-L6-v2 model.
Vector Storage: Stores data locally using a lightweight Chroma DB instance.
Context-Strict Answers: Prompts Gemini to only answer using your provided document data.
📋 Prerequisites
Before running the project, ensure you have:
Python 3.9 or higher installed.
A Google Gemini API Key. You can get one from Google AI Studio.
🛠️ Installation & Setup
Clone the repository:
bash
git clone https://github.com
cd YOUR_REPO_NAME
Use code with caution.
Install the required libraries:
bash
pip install langchain-google-genai langchain-community langchain-text-splitters chromadb sentence-transformers
Use code with caution.
Add your knowledge base:
Create a file named knowledge.txt in the root directory.
Paste the custom text data or articles you want the chatbot to know inside this file.
Add your API Key:
Open the Python script.
Replace "YOUR_GEMINI_API_KEY" with your actual Google Gemini API key:
python
os.environ["GOOGLE_API_KEY"] = "AIzaSy..."
Use code with caution.
💻 Usage
Run the chatbot script from your terminal:
bash
python main.py
Use code with caution.
Example Interaction:
text
Reading document...
Converting text into math vectors...

--- RAG Chatbot is Ready! ---

Ask a question (or type 'exit'): What is the company's holiday policy?

Bot: The company offers 25 days of paid annual leave, which must be approved by your manager two weeks in advance.
Use code with caution.
⚙️ How It Works
Load: TextLoader imports your raw text data.
Split: The text is broken down into chunks of 500 characters to fit LLM context limits.
Embed: HuggingFaceEmbeddings translates text chunks into mathematical vectors.
Store: Chroma database saves these vectors locally for instant semantic searching.
Retrieve & Query: The system fetches the top 2 most relevant text chunks matching the user's question and passes them to gemini-1.5-flash to generate a strict context-based answer.
