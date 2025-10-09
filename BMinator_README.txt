
BMINATÖR (DeepPersona): WORD-LEVEL TRANSFORMER TABANLI KİŞİLİK ODAKLI METİN ÜRETİMİ
====================================================================================

GENEL AÇIKLAMA
--------------
BMinatör, kullanıcıya ait 25 boyutlu "persona vektörü" ile eğitilmiş, Word-level Transformer mimarisi kullanan 
kişilik odaklı bir metin üretim sistemidir. Bu sistem, bireyin karakteristik özelliklerine göre dil çıktısı üretir. 
Sesli yanıt veya yüz animasyonu **bulunmamaktadır**.

YAZAR
-----
👩‍💻 Büşra Mina Al  
📧 busraminaa@gmail.com  
🎓 Ostim Teknik Üniversitesi – Yapay Zeka Mühendisliği & Endüstri Mühendisliği (ÇAP)  
🧠 Uzmanlık: NLP, Üretken Yapay Zeka, Kişilik Odaklı AI Modelleri  

------------------------------------------------------------------------------------
1. BAŞLATMA TALİMATLARI
------------------------------------------------------------------------------------

✅ GEREKSİNİMLER:
-----------------
- Python 3.10+
- PyTorch
- NumPy
- scikit-learn

🧩 GEREKLİ KURULUM:
-------------------

# Adım 1: Repository'yi klonla
git clone https://github.com/kullanici/bminator.git
cd bminator

# Adım 2: Gereksinimleri kur
pip install -r requirements.txt

🚀 EĞİTİMİ BAŞLATMA:
--------------------

python train_word_transformer.py \
  --epochs 150 \
  --batch_size 64 \
  --save_dir checkpoints/

✍️ METİN ÜRETİMİ:
------------------

python generate_word_level.py \
  --vector_file "sample.vec" \
  --model_checkpoint "checkpoints/model_150.pt"

📁 ÇIKTI:
---------
- Üretilen kelime dizisi: outputs/generated_text.txt

------------------------------------------------------------------------------------
2. MODEL TEKNİK DETAYLARI
------------------------------------------------------------------------------------

📌 GİRDİLER:
-----------
- vector → 25 float değerlik kişilik vektörü
- text_ids → vocab.json’dan gelen token ID dizisi (maks. 60 uzunluk)

📌 TRANSFORMER MİMARİSİ:
-------------------------
- 4 adet Transformer blok
- 8 başlıklı Self-Attention
- Word Embedding boyutu: 128
- Dropout: %20
- Aktivasyon: ReLU
- Normalizasyon: LayerNorm
- Loss: CrossEntropy
- Optimizer: Adam (lr=0.0005)

📌 VERİ FORMATLARI:
-------------------
- word_vocab.json: Kelime-ID sözlüğü (ilk 5000 kelime)
- worddata_partX.json: Her satır { "vector": [...], "text_ids": [...] } biçiminde

------------------------------------------------------------------------------------
3. NOTLAR & GELİŞTİRME HEDEFLERİ
------------------------------------------------------------------------------------

✅ Tamamlananlar:
- Word-level üretken Transformer modeli
- 20.000 örnekten oluşan 4 parçalı dataset
- Eğitim ve inference döngüsü

🧪 Planlananlar:
- Görsel girdiden otomatik persona çıkarımı
- Duygu durumu temelli üretim vektörü
- Gradio / Streamlit tabanlı web arayüzü

------------------------------------------------------------------------------------
4. LİSANS
------------------------------------------------------------------------------------

Bu proje MIT lisansı ile lisanslanmıştır. Ticari veya akademik amaçlarla serbestçe kullanılabilir.

Telif Hakkı © 2025 Büşra Mina Al
