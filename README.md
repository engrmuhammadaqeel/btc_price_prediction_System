# BTC Price Prediction Dashboard - Deployment Guide

Yeh folder Streamlit Community Cloud pe deploy karne ke liye ready hai.

## Files
- `dashboard.py` — Main Streamlit app
- `rf_btc_prediction_model.pkl` — Trained Random Forest model
- `rf_scaler.pkl` — StandardScaler (price normalize/denormalize karne ke liye)
- `requirements.txt` — Python dependencies (UTF-8, sklearn version pinned)
- `Procfile` — Heroku ke liye (Streamlit Cloud isay ignore karega, koi masla nahi)
- `.gitignore` — Git ke liye unnecessary files ignore karne ke liye

## Deploy Steps (Streamlit Community Cloud)

1. GitHub par naya repository banayen (public ya private, dono chalega).
2. Is folder ki tamam files (dashboard.py, rf_btc_prediction_model.pkl, rf_scaler.pkl, requirements.txt) us repo mein upload/push karen.
   - Agar GitHub web UI se kar rahe hain: "Add file" -> "Upload files" -> in sab files ko drag karen -> commit karen.
   - Agar git command line use kar rahe hain:
     ```
     git init
     git add .
     git commit -m "Initial deployment"
     git branch -M main
     git remote add origin <your-repo-url>
     git push -u origin main
     ```
3. https://share.streamlit.io par jayen aur GitHub account se login karen.
4. "New app" par click karen.
5. Apni repository select karen, branch "main" rakhen, aur main file path `dashboard.py` likhen.
6. "Deploy" par click karen.
7. 2-3 minute mein app live ho jayega aur aapko ek public URL milega jo aap kisi ko bhi share kar sakte hain.

## Important Note
- Model file size ~26 MB hai — GitHub par normal push se chala jayega (GitHub ki limit 100 MB per file hai), koi Git LFS ki zarurat nahi.
- Agar future mein app "model load error" de, to confirm karen ke `rf_btc_prediction_model.pkl` aur `rf_scaler.pkl` dono `dashboard.py` ke barabar (same folder) mein hain — koi subfolder nahi.
