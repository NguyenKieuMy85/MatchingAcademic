# MatchingAcademic
This project aims to build a matching system that connects students and lecturers in academic environments based on their technical skills, research interests, and domain compatibility. It leverages Content-Based Filtering, TF-IDF vectorization, and cosine similarity to recommend suitable supervisors for students working on research or graduation projects.
## 📂 Dataset
### 📘 Lecturer Dataset
Source: https://httt.uit.edu.vn/en_US/nghien-cuu-khoa-hoc/publications
Content: Metadata of 69 publications from 5 lecturers in the Information Systems department, UIT.
Processed Files:
**lecturer_profiles_summarized.json:** Contains keywords, expertise descriptions, and grouped interest topics for each lecturer.

### 🧑‍🎓 Student Dataset
Source: https://httt.uit.edu.vn/category/research/
Content: 5 student profiles with names, IDs, departments, and curated skill sets derived from project titles and descriptions.
Processed Files:
**students.json:** Basic student info (ID, name, department)
**student_skills.json:** Technical skills and topics associated with each student

### 🔧 Processing Pipeline
The following steps summarize how raw data is transformed and used for generating matches:

⚙️ **Step 1:** Data Preprocessing
- Normalize names (remove diacritics, lowercase)
- Generate abstract summaries for lecturer publications using LLM
- Extract keywords & skills using keyword grouping and summarization
- Clean and tokenize skills (students) and interests (lecturers)

**🧠 Step 2:** Vectorization
- Apply TF-IDF vectorizer to lecturer keywords and student skills
- Represent both as numeric vectors

**🔍 Step 3:** Matching
Use cosine similarity to compute match score between each student and all lecturers
Filter matches using a similarity threshold (e.g., top 75 percentile)
Select top-K (e.g., 3) best-matching lecturers per student

**📊 Step 4:** Output Generation
Save results to raw_matching_results.json
![image](https://github.com/user-attachments/assets/deb347db-3027-46db-a694-516b9d22db47)

### 🛠 Technologies Used
Python: pandas, scikit-learn, nltk, matplotlib
NLP: Gemini/ChatGPT for abstract generation & profile summarization
Vectorization: TF-IDF
Matching Algorithm: Cosine similarity
Visualization: Streamlit, matplotlib, seaborn

### 🚀 Future Improvements
Expand dataset with more profiles across departments
Add collaborative filtering & hybrid models
Enable feedback loop from real student-lecturer interactions
Integrate BERT/SentenceTransformer embeddings for semantic matching

Visualize matches using Streamlit or Python plots

**📈 Matching Pipeline Overview**
![image](https://github.com/user-attachments/assets/3436f06e-860b-42f7-a2ee-b09560c1fc50)

🧪 Output Sample
![image](https://github.com/user-attachments/assets/fa6437c3-3c49-4f73-a053-1a4ae4e98130)
