
# 🚇 Metro Ağı Rota Bulucu

Bu proje, bir şehir metrosu ağı üzerinde **en az aktarmalı** veya **en hızlı** rotayı bulmak için Python ile geliştirilmiş bir simülasyondur. Kullanıcı, başlangıç ve hedef istasyonlarını girerek sistemin sunduğu rotaları inceleyebilir.

## 🛠️ Kullanılan Teknolojiler ve Kütüphaneler

- **Python 3.x**: Projenin ana programlama dili
- **collections**
  - `defaultdict`: Hatları gruplayarak organize etmek için kullanıldı.
  - `deque`: Breadth-First Search (BFS) sırasında hızlı kuyruk işlemleri için tercih edildi.
- **heapq**: A* algoritmasında öncelikli kuyruk işlemleri için kullanıldı.
- **typing**: Kodun okunabilirliğini ve sürdürülebilirliğini artırmak için tip ipuçları verildi (List, Tuple, Optional, vb.)

## 📊 Algoritmaların Çalışma Mantığı

### 🔄 BFS (Breadth-First Search) - En Az Aktarmalı Rota

- Bu algoritma **katman katman** tüm istasyonları gezer.
- Her istasyon ziyaret edilirken, aynı hatta devam etmek tercih edilir.
- Hat değiştirildiğinde, "aktarma sayısı" bir artırılır.
- Hedef istasyona ulaşıldığında, ilk bulunan çözüm en az aktarmalı rota olarak döndürülür.

> **Neden BFS?**  
> BFS algoritması, grafikte bir hedefe **minimum adımda ulaşmak** için garantili çözüm sunar. Burada her adım bir istasyon, her seviye bir aktarma anlamına gelir.

### ⚡ A* (A-Star) Algoritması - En Hızlı Rota

- A* algoritması, **en kısa sürede** hedefe ulaşmak için kullanılır.
- Komşu istasyonlar için hesaplanan süreler, `heapq` ile yönetilen bir öncelik kuyruğunda saklanır.
- Bu versiyonda **heuristic (tahmin)** kısmı sıfır alınarak **Dijkstra** gibi davranması sağlanmıştır.

> **Neden A*?**  
> Gerçek ulaşım sistemlerinde "aktarma sayısı" kadar **toplam yolculuk süresi** de önemlidir. Bu yüzden A* ile her rotanın süresi karşılaştırılarak en hızlısı seçilir.

## 🚀 Örnek Kullanım ve Test Sonuçları

```python
rota = metro.en_az_aktarma_bul("M1", "K4")
print("En az aktarmalı rota:", " -> ".join(i.ad for i in rota))

rota, sure = metro.en_hizli_rota_bul("M1", "K4")
print(f"En hızlı rota ({sure} dakika):", " -> ".join(i.ad for i in rota))
```

### Test Çıktıları:

#### 1. AŞTİ'den OSB'ye:
- **En az aktarmalı rota**: AŞTİ -> Kızılay (Mavi) -> Kızılay (Kırmızı) -> Ulus -> Demetevler -> OSB  
- **En hızlı rota** (22 dakika): Aynı rota

#### 2. Batıkent'ten Keçiören'e:
- **En az aktarmalı rota**: Batıkent -> Demetevler -> Gar -> Keçiören  
- **En hızlı rota** (21 dakika): Aynı rota

#### 3. Keçiören'den AŞTİ'ye:
- **En az aktarmalı rota**: Keçiören -> Gar (Turuncu) -> Gar (Mavi) -> Sıhhiye -> Kızılay -> AŞTİ  
- **En hızlı rota** (19 dakika): Aynı rota

## 📌 Kurulum ve Çalıştırma

```bash
git clone https://github.com/kullaniciAdi/metro-agi-projesi.git
cd metro-agi-projesi
python metro_agi.py
```
