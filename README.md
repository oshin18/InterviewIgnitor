# 🧠 Interview Ignitor (AI Interview Agent)

**Interview Ignitor** is a smart, modular assistant designed to help job seekers prepare for interviews with personalized cover letters and mock sessions based on their **resume** and the **job description** of their target role. The Interview bot evaluates your answer and provides feedback with the sample answer to learn from.

Powered by **Azure OpenAI** and **Semantic Kernel**, this app analyzes a candidate’s profile, matches it with job requirements, generates tailored interview questions, evaluates responses, and provides actionable feedback — all in one streamlined tool.

---

## Demonstration 
[Demo Video](https://youtu.be/ZcjfaqMfdz0)

---

## Process Flow
![Process flow](docs/ProcessFlow.png)

---

## 🔍 Features

- **Resume Analyzer**  
  Parses and summarizes key insights from resumes using natural language understanding.

- **Resume Skills Extractor**  
  Parses the unstructured resume to fetch the candidate's skills.

- **Job Description Analyzer**  
  Extracts required skills, responsibilities, and key expectations from job postings.

- **Cover Letter Generator**  
  Creates cover letter tailored to the candidate's experience and job requirements.

- **Question Generator From Resume and Job Description**  
  Creates interview questions tailored to the candidate's experience and job requirements.

- **Resume Skills Question Generator**  
  Creates interview questions tailored to the candidate's experience and skills mentioned in his resume.

- **Answer Evaluator**  
  Analyzes candidate responses for clarity, relevance, and alignment with role expectations.

- **Feedback Provider**  
  Offers constructive, context-aware feedback to help candidates improve their answers.

- **Sample Answer Generator**  
  Provides sample answer to help candidate learn.

- **Fully Modular**  
  Each component is built as a Semantic Kernel plugin, making it easy to extend, swap, or enhance.

---

## 💼 Ideal For

- Job seekers aiming for technical or behavioral interviews  
- Career coaches looking for smart tools to assist their clients  
- Developers building personalized AI interview prep platforms

---

## 🛠️ Tech Stack

- [Streamlit](https://streamlit.io/)  
- [Azure OpenAI](https://azure.microsoft.com/en-us/products/cognitive-services/openai-service/)  
- [Semantic Kernel](https://github.com/microsoft/semantic-kernel)  
- Python 3.10+

---

## 📉 Architecture Overview

![Architecture](docs/Architecture.png)

```plaintext
            +---------------------+
            |  Streamlit Frontend |
            +----------+----------+
                       |
                       v
         +-------------+--------------+
         |   Homepage (Entrypoint)    |
         |   CoverLetter (Sidebar)    |
         |   MockInterview (Sidebar)  |
         +-------------+--------------+
                       |
                       v
     +-----------------+--------------------+
     |   Semantic Kernel Agents (Skills)    |
     |   - ResumeAnalyzerAgent              |
     |   - ResumeSkillAnalyzerAgent         |
     |   - JDAnalyzerAgent                  |
     |   - CoverLetterGeneratorAgent        |
     |   - QuestionGeneratorAgent           |
     |   - SkillQuestionGeneratorAgent      |
     |   - AnswerEvaluatorAgent             |
     |   - SampleAnswerGeneratorAgent       |
     +-----------------+--------------------+
                       |
                       v
               +-------+-------+
               |  Azure OpenAI |
               +---------------+
```

---

## 📂 Code Layout

```plaintext
AIInterviewAgent/
│
├── Homepage.py                       # Main Streamlit application (Homepage)
│
├── skills/
│   ├── resume_analyzer/              # Resume summarization skill
│   ├── jd_analyzer/                  # Job description analysis skill
│   ├── cover_letter_generator        # Cover letter generation skill
│   ├── question_generator/           # Dynamic question generation skill
│   ├── answer_evaluator/             # Answer evaluation and feedback
│   └── sample_answer_generator/      # Sample answer generation skill
│
├── utils/                            # Helpers and wrappers for file processing and random question generation
│
├── configs/                          # Configuration files
│   ├── kernel.py                     # Kernel configurations
│   └── agents.py                     # Multiple Agent configurations
│
├── services/                         # Services files
│   └── agents.py                     # Multiple Agent functions 
│   
├── pages/                            # Steemlit Pages for sidebar
│   ├── 1_Cover_Letter_Generator.py                    
│   └── 2_Mock_Interview_Bot
│ 
├── docs/                             # Documents 
│   ├── ApplicationFlow/              # Application Flow Screenshots 
│   ├── Interview_Ignitor_demo.mp4    # Application Demo 
│   ├── ProcessFlow.png               # Application Process Flow
│   └── Architecture.png              # Application Architecture diagram
│ 
├── sample-docs/                      # Example resume and job description files
│
├── .env.example                      # Sample Environment variables (e.g., OpenAI key)
├── requirements.txt                  # Python dependencies
└── README.md                         # You're here!
```

---

## 🚀 Getting Started

Clone the repo and follow the [Setup Guide](#%EF%B8%8F-setup-guide) to deploy locally or on the cloud.

```bash
git clone https://github.com/oshin18/AIInterviewAgent.git
cd AIInterviewAgent
```

---

## ⚙️ Setup Guide

### 🔧 Prerequisites

- Python 3.9+
- Azure OpenAI Service (with GPT-4o or GPT-4 deployed)
- Get your Azure credentials from the [Azure Portal](https://portal.azure.com/):
  - `AZURE_OPENAI_APIKEY`
  - `AZURE_OPENAI_ENDPOINT`
  - `AZURE_OPENAI_DEPLOYMENT`

### 🛠️ Installation

```bash
# Clone the repository
$ git clone https://github.com/oshin18/AIInterviewAgent.git
$ cd AIInterviewAgent

# (Optional) Create and activate a virtual environment
$ python -m venv venv
$ source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install Python dependencies
$ pip install -r requirements.txt

# Set up environment variables
# Copy the example .env file and update it with your credentials
$ cp .env.example .env

# Open the .env file and add your Azure OpenAI API credentials
$ nano .env  # or use your preferred text editor

# Inside the .env file, add the following:
# AZURE_OPENAI_APIKEY=your-api-key
# AZURE_OPENAI_ENDPOINT=https://your-resource.openai.azure.com/
# AZURE_OPENAI_DEPLOYMENT=gpt-4  # or your deployment name

# Run the Streamlit application
$ streamlit run Homepage.py
```

---

## 📀 Next Steps

- Voice-based interview simulation  
- Analytics dashboard for progress tracking  
- Integration with ATS platforms
- Orchestration and Planner implementation for Agents
```
