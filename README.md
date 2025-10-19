  
# 🎮 Steam Game Popularity Analysis using Machine Learning & IBM Granite AI

## 🧭 Project Overview
Proyek ini bertujuan untuk **memprediksi popularitas game di platform Steam** berdasarkan faktor seperti **genre, kategori, harga, dan jumlah DLC**, serta menghasilkan **insight otomatis menggunakan model AI IBM Granite**.  

Proyek ini menggabungkan dua pendekatan utama:
1. **Machine Learning (Random Forest Regressor)** untuk memprediksi jumlah pemain (estimated owners).
2. **AI Summarization (IBM Granite)** untuk membuat ringkasan otomatis yang menjelaskan hasil analisis dan tren popularitas game.  

Melalui pendekatan ini, Game Developer dapat memahami:
- Genre dan kategori yang paling diminati.
- Kisaran harga ideal untuk meningkatkan popularitas.
- Kombinasi fitur yang paling berpengaruh terhadap kepemilikan game.

---

## 📂 Raw Dataset Link
Dataset diambil dari sumber publik **Steam Store Dataset (Kaggle)**  
🔗 [Steam Games Dataset on Kaggle](https://www.kaggle.com/datasets/fronkongames/steam-games-dataset)

---

## 📊 Insight & Findings
1. **Genre Populer**
   - Genre *Action*, *Adventure*, dan *Indie* memiliki rata-rata jumlah pemain tertinggi.
   - Kategori *Single-player* dan *Co-op* lebih sering muncul pada game populer.

2. **Harga Ideal**
   - Game berbayar dengan harga **$5–$15** menunjukkan popularitas optimal.
   - Game gratis (Free-to-Play) menarik banyak pemain, tetapi tingkat retensinya lebih rendah.

3. **Faktor Dominan**
   - Berdasarkan feature importance dari model Random Forest, **Genre** dan **Category** adalah faktor paling berpengaruh terhadap popularitas.
   - Fitur seperti DLC dan diskon memiliki pengaruh menengah terhadap jumlah pemain.

4. **Insight Otomatis (Granite AI)**
   - Model Granite mengidentifikasi bahwa kombinasi *Action F2P Multiplayer* dan *Adventure Casual* adalah pola paling konsisten untuk menarik pemain baru.
   - Rekomendasi AI: fokus pada gameplay yang mudah diakses, harga kompetitif, dan dukungan komunitas aktif untuk meningkatkan engagement pemain.

---

## 🤖 AI Support Explanation
### **1. Machine Learning Model**
Model yang digunakan adalah:
```
python
from sklearn.ensemble import RandomForestRegressor

model = RandomForestRegressor(n_estimators=200, random_state=42)
model.fit(X_train, y_train)
```

### **2. AI Summarization Model (IBM Granite)**
Model ibm-granite/granite-3.3-8b-instruct digunakan melalui API Replicate untuk menghasilkan insight otomatis dari hasil analisis.
```
prompt = f"""
Analyze Steam game popularity by genre and category:

{summary_text}

Provide:
1. Most popular genre-category combinations
2. Ideal price range
3. Key insights and developer recommendations
"""
response = granite.invoke(prompt)
print(response)
```
### **3. Contoh Output**
```
### 1. Most Popular Game Combinations
- Action, Free-to-Play, Multiplayer → *High engagement and accessibility*

### 2. Ideal Price Range
- $5–$15 for paid games → *Balanced between accessibility and perceived value*

### 3. Developer Recommendations
- Combine multiplayer and community-driven gameplay
- Maintain frequent updates and support accessibility features
```

