# LangChain Text Splitters Demo

This project demonstrates different approaches to **text splitting** using LangChain.  
Text splitting is important for preparing documents so that LLMs can process them efficiently.

---

## 📂 Project Structure

- **length_based.py** → Splits a PDF into fixed-size chunks (by character length).
- **python_code_splitting.py** → Splits Python source code using language-aware splitting.
- **semantic_meaning_based.py** → Splits text based on semantic meaning using embeddings.
- **text_structure_based.py** → Splits text into chunks based on structure (paragraphs).

Other files:
- `dl-curriculum.pdf` → Sample PDF used in demos.
- `requirements.txt` → Dependencies list.
- `.env` → Environment variables (OpenAI API key).
- `.gitignore` → Ignore virtual environment, cache, and secrets.

---

## ⚙️ Setup

1. Clone the repo:
   ```bash
   git clone https://github.com/<username>/Langchain-text-splitters.git
   cd Langchain-text-splitters

2. Create a virtual environment:
   ```bash
python -m venv .venv
.venv\Scripts\activate   # Windows

3. Install dependencies:
   ```bash
pip install -r requirements.txt

4. Add your OpenAI API key in .env:
.env
OPENAI_API_KEY=sk-xxxxxx

▶️ How to Run
================
Each file can be run individually:

1. Length-based splitting
   ```bash
python length_based.py
Loads dl-curriculum.pdf and splits into chunks of 200 characters.

2. Python code splitting
   ```bash
python python_code_splitting.py
Splits a Python class definition into logical code chunks using Language.PYTHON.

3. Semantic meaning-based splitting
   ```bash
python semantic_meaning_based.py
Uses SemanticChunker with OpenAIEmbeddings to split text based on semantic meaning.

4. Text structure-based splitting
   ```bash
python text_structure_based.py
Splits text into chunks of 500 characters, preserving paragraph structure.


📌 Explanation of Each File:
=================================
1. length_based.py
- Loader: PyPDFLoader → loads PDF file.
- Splitter: CharacterTextSplitter → splits text by fixed length (200 chars).
- Output: Prints cleaned chunk (newline replaced with spaces).

2. python_code_splitting.py
- Splitter: RecursiveCharacterTextSplitter.from_language(Language.PYTHON)
- Purpose: Splits Python code intelligently (functions, classes).
- Output: Number of chunks + one chunk of code.

3. semantic_meaning_based.py
- Splitter: SemanticChunker → uses embeddings to detect semantic breakpoints.
- Embeddings: OpenAIEmbeddings.
- Output: Number of semantic chunks + their content.

4. text_structure_based.py
- Splitter: RecursiveCharacterTextSplitter.
- Purpose: Splits text into chunks of 500 characters, keeping paragraph boundaries.
- Output: Number of chunks + full chunk list.


📌 Types of Splitters Used:
-------------------------------
1. CharacterTextSplitter → fixed length chunks.
2. RecursiveCharacterTextSplitter → language-aware splitting.
3. SemanticChunker → meaning-based splitting using embeddings.