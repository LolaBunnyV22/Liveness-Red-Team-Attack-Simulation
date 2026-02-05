# 🛡️ Biyometrik Canlılık Analizi - Red Team Saldırı Simülasyonu

Bu proje, statik vesikalık fotoğrafları derin öğrenme modelleri kullanarak canlandırmak ve biyometrik güvenlik sistemlerinin (liveness detection) bu sentetik videolara karşı tepkisini ölçmek amacıyla geliştirilmiştir.

## 🚀 Teknik Altyapı
* **Model:** Thin-Plate Spline Motion Model (TPS)
* **Donanım:** Tesla T4 GPU (Google Colab üzerinden)
* **Hız:** 7.14 it/s (Yaklaşık saniyede 7 kare işleme)

## 🛠️ Nasıl Çalışıyor?
Sistem iki ana girdiyle çalışır:
1. **Kaynak Görüntü (Source):** Canlandırılacak olan durağan fotoğraf.
2. **Sürücü Video (Driving):** Fotoğrafa aktarılacak olan yüz hareketlerinin kaynağı.

`demo.py` scripti, fotoğraf üzerindeki kilit noktaları (landmarks) belirler ve Thin-Plate Spline deformasyonu kullanarak sürücü videodaki hareketleri bu noktalara milimetrik olarak uygular.

## 📊 Test Bulguları ve Analiz
* **Başarı Oranı:** Şu anki testlerde %80 tamamlanma oranına ulaşılmıştır.
* **Bozulmalar (Artifacts):** Hızlı hareketlerde ve aşırı kafa açılarında doku bozulmaları gözlemlenmiştir. Bu bozulmalar, savunma modelimizin eğitilmesi için "Zorlu Negatif" (Hard Negative) veri olarak kullanılmaktadır.
