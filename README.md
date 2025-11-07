https://colab.research.google.com/drive/1Djnq6MgwaaujuIQ972Q4DdY9aGv1YB05?usp=sharing







# 📘 ** – Gemini-Powered Text Summarizer & PDF Generator**

## 🧠 Overview

**Watching the Code** is a smart, Gemini-powered summarization pipeline built in Google Colab. It allows users to input long-form text (such as transcripts, articles, or essays), generate a concise summary using Google's Gemini 2.5 Pro model, and export the result as a clean, readable PDF. This project combines the power of generative AI with practical document creation — ideal for students, researchers, and educators.

---

## 🚀 Features

- ✨ **Gemini 2.5 Pro Integration**: Uses Google’s cutting-edge generative model to produce intelligent summaries.
- 📄 **PDF Export**: Automatically converts the AI-generated summary into a downloadable PDF using `fpdf`.
- 🎥 **YouTube Transcript Support** *(optional)*: Includes setup for extracting transcripts using `youtube-transcript-api`.
- 🔐 **Secure API Access**: Uses `google.colab.userdata` to safely retrieve your Gemini API key.
- 📦 **Modular Workflow**: Clean separation of summarization, formatting, and export logic.

---

## 📦 Installation

Run the following commands in your Colab notebook to install required packages:

```python
!pip install google-generativeai
!pip install -q youtube-transcript-api
!pip install fpdf
!pip install PyPDF2
```

---

## 🔑 API Setup

Make sure your Gemini API key is stored securely in Colab:

```python
from google.colab import userdata
import google.generativeai as genai

GOOGLE_API_KEY = userdata.get('Gemini_API_Key')
genai.configure(api_key = GOOGLE_API_KEY)
```

---

## 📝 How It Works

1. **User Input**: You enter the text manually or extract it from a YouTube video.
2. **Prompt Definition**: A summarization prompt is defined to guide Gemini.
3. **Gemini Summarization**: The model generates a summary in bullet points (max 550 words).
4. **PDF Creation**: The summary is split into lines and written into a PDF using `fpdf`.
5. **Download**: The final PDF is saved and offered for download.

---

## 📂 File Output

- `summary.pdf`: Contains the AI-generated summary in clean, readable format.

---

## 💡 Example Use Cases

- Summarizing lecture transcripts for study notes
- Creating executive summaries of long articles
- Generating teacher-friendly handouts from raw text
- Preparing certification-ready content with minimal effort

---

## 🛠️ Code Snippet Highlights

```python
model = genai.GenerativeModel("gemini-2.5-pro")
response = model.generate_content(prompt + transcript_text)
summary = response.text
```

```python
pdf = FPDF()
pdf.add_page()
pdf.set_font("Arial", size = 12)
for line in summary.split('\n'):
    pdf.cell(200, 10, txt = line, ln = True, align = 'L')
pdf.output("summary.pdf")
```

---

## 📥 Download

```python
from google.colab import files
files.download('summary.pdf')
```

---

## 🙌 Credits

- Built using **Google Generative AI (Gemini)**
- PDF generation via **fpdf**
- Transcript extraction via **youtube-transcript-api**
- Developed in **Google Colab** for ease of use and sharing

- Colab file link is https://colab.research.google.com/drive/1Djnq6MgwaaujuIQ972Q4DdY9aGv1YB05?usp=sharing

---


