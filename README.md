
# 🚀 Cold Email Generator

**AI-powered outreach tool that analyzes job descriptions and automatically generates personalized cold emails.**

This project demonstrates practical applications of **Large Language Models (LLMs)**, **vector databases (ChromaDB)**, and **web scraping (LangChain)** — all wrapped in a clean and interactive **Streamlit** interface.
[![Python](https://img.shields.io/badge/Python-3.10-blue.svg)](https://www.python.org/)
[![LangChain](https://img.shields.io/badge/LangChain-Framework-blueviolet)](https://www.langchain.com/)
[![Streamlit](https://img.shields.io/badge/Streamlit-Web_App-red)](https://streamlit.io/)
[![ChromaDB](https://img.shields.io/badge/ChromaDB-Vector_Database-orange)](https://www.trychroma.com/)
[![Status](https://img.shields.io/badge/Status-Active-brightgreen)]()

---

## 🌟 Why This Project

Recruiters, business owners, and freelancers often struggle to craft customized emails for multiple job postings.
This project solves that by:

* Extracting job details directly from URLs 🧩
* Identifying required skills using an AI chain 🤖
* Matching those skills with personal portfolio projects stored in a **vector database** 📊
* Automatically writing compelling and human-like emails tailored to the opportunity ✉️

---

## 🧠 Key Features

✅ **AI-driven job extraction** — Uses an LLM chain (`Chain` class) to understand job listings and extract key details like position, responsibilities, and skills.

✅ **Skill-based portfolio matching** — Stores your past projects and skills in a **ChromaDB vectorstore** (`Portfolio` class). It intelligently recommends your most relevant projects for each job.

✅ **Automatic cold email generation** — Writes custom emails highlighting matching projects and skills using your LLM.

✅ **Streamlit UI** — Simple interface where you just paste a job posting URL and click “Submit”.

✅ **Data cleaning pipeline** — The `clean_text()` utility removes HTML, special characters, and clutter for precise text processing.

---

## 🧩 Tech Stack

| Component            | Technology Used                       |
| -------------------- | ------------------------------------- |
| Frontend UI          | Streamlit                             |
| AI/LLM Engine        | LangChain                             |
| Vector Database      | ChromaDB                              |
| Web Data Loader      | LangChain Community (`WebBaseLoader`) |
| Data Cleaning        | Regex + Python text processing        |
| Programming Language | Python 3.10+                          |

---

## 🏗️ Architecture Overview

```
                ┌──────────────────────┐
                │  Job Post URL Input  │
                └─────────┬────────────┘
                          │
                          ▼
                ┌──────────────────────┐
                │  WebBaseLoader (LangChain) │
                └─────────┬────────────┘
                          │
                          ▼
             ┌───────────────────────────┐
             │   clean_text() Function    │
             └─────────┬─────────────────┘
                          │
                          ▼
              ┌────────────────────────┐
              │    LLM (Chain class)   │
              │  → Extract job details │
              │  → Generate email      │
              └─────────┬──────────────┘
                          │
                          ▼
         ┌──────────────────────────────────┐
         │ Portfolio (ChromaDB Collection)   │
         │ → Query based on job skills       │
         │ → Retrieve matching projects      │
         └──────────────────────────────────┘
                          │
                          ▼
                 ┌────────────────┐
                 │ Final Email ✉️ │
                 └────────────────┘
```

---

## ⚙️ How to Run Locally

1️⃣ **Clone the repo**

```bash
git clone https://github.com/<yourusername>/cold-email-generator.git
cd cold-email-generator
```

2️⃣ **Create a virtual environment**

```bash
python -m venv venv
venv\Scripts\activate  # on Windows
# OR
source venv/bin/activate  # on Mac/Linux
```

3️⃣ **Install dependencies**

```bash
pip install -r requirements.txt
```

4️⃣ **Run the Streamlit app**

```bash
streamlit run app.py
```

5️⃣ **Input any job post URL**
Paste a job listing (e.g., from LinkedIn) and get your customized email instantly!

---

## 📂 Project Structure

```
📁 ColdEmailGenerator/
│
├── app.py                  # Main Streamlit app
├── chains.py               # LLM pipeline for job extraction & email generation
├── portfolio.py            # Vectorstore setup using ChromaDB
├── utils.py                # Text cleaning utilities
├── sample_portfolio.csv    # Your personal project data
└── requirements.txt        # Dependencies
```

---

## 📊 Sample Portfolio CSV

| Skill 1          | Skill 2      | Skill 3    | Project Link                                                         |
| ---------------- | ------------ | ---------- | -------------------------------------------------------------------- |
| Python           | Flask        | REST API   | [https://github.com/user/project1](https://github.com/user/project1) |
| Machine Learning | Scikit-learn | Regression | [https://github.com/user/project2](https://github.com/user/project2) |

Each row represents one of your projects, its key skills, and its GitHub/portfolio link.

---

## 💡 Example Output

**Input:**

> [https://careers.microsoft.com/job/software-engineer-ai](#)

**Output:**

```markdown
Subject: AI Engineer Role – Leveraging My ML & NLP Expertise  

Hi [Recruiter Name],  

I came across your posting for an **AI Engineer** role at **Microsoft**, and I was immediately interested.  
With experience in building **ML models** and deploying them using **Flask APIs**, I’ve worked on projects like:  
- [Customer Churn Predictor](https://github.com/user/churn-predictor)  
- [Text Summarization using Transformers](https://github.com/user/nlp-summarizer)  

I’d love to discuss how my background can contribute to your team’s ongoing AI initiatives.  

Warm regards,  
**Anshul Raj**  
```

---

## 🌍 Future Improvements

🔹 Integrate **Groq API** for ultra-fast LLM inference
🔹 Add multi-URL batch processing
🔹 Implement custom email tone options (formal / casual / concise)
🔹 Deploy the app on **Streamlit Cloud** or **Hugging Face Spaces**

---
