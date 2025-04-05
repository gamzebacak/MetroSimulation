# MetroSimulation

# Sürücüsüz Metro Simülasyonu - Rota Optimizasyonu

## 1. Proje Başlığı ve Kısa Açıklama

Bu proje, bir şehir içi metro ağında iki istasyon arasındaki en az aktarma ve en kısa sürede ulaşım rotalarını belirlemek amacıyla geliştirilmiştir. Farklı metro hatlarını, istasyonlar arasındaki bağlantıları ve seyahat sürelerini göz önünde bulundurarak, optimal rota hesaplamaları yapılmaktadır.

## 2. Kullanılan Teknolojiler ve Kütüphaneler

Bu projede aşağıdaki Python kütüphaneleri kullanılmıştır:
## collections.defaultdict: Metro ağındaki istasyonları ve hatları organize etmek için kullanılmıştır.
## collections.deque: Genişlik Öncelikli Arama (BFS) algoritmasında kuyruk yapısı olarak kullanılmıştır.
## heapq: En hızlı rotayı hesaplamak için kullanılan A* algoritmasında öncelik kuyruğu (priority queue) oluşturmak amacıyla kullanılmıştır.


## 3. Algoritmaların Çalışma Mantığı

## BFS Algoritması (en_az_aktarma_bul)
Fonksiyonun Amacı: Başlangıç ve hedef istasyonlar arasında en az aktarma ile gidilen rotayı bulmak.
## Çalışma Prensibi:
BFS algoritması, en kısa yolu bulmak için kullanılır ve kuyruk veri yapısını temel alır.
İlk olarak, başlangıç istasyonu kuyruğa eklenir.
Kuyruktan bir istasyon çıkartılır ve komşuları keşfedilir.
Eğer hedef istasyona ulaşılmışsa, bulunan yol döndürülür.
Daha önce ziyaret edilmemiş komşular kuyruğa eklenerek süreç devam eder.
Kuyruk boşaldığında hedefe ulaşılmamışsa, None döndürülür.

## A* Algoritması (en_hizli_rota_bul)
Fonksiyonun Amacı: Başlangıç ve hedef istasyonlar arasında en hızlı rotayı (toplam süre bazında) bulmak.
## Çalışma Prensibi:
A* algoritması, en kısa sürede hedefe ulaşmayı amaçlayan bir yol arama algoritmasıdır.
Öncelik kuyruğu (heapq) kullanılarak en düşük süreye sahip yol her zaman öncelikli işlenir.
Başlangıç istasyonu kuyruğa (0, baslangic_istasyonu) olarak eklenir.
Kuyruktaki en düşük süreye sahip istasyon işlenir ve komşuları değerlendirilir.
Eğer hedef istasyona ulaşılmışsa, toplam süre ve rota döndürülür.
Daha önce keşfedilen yolların süresi, yeni bulunan süreden kısa ise güncellenir.
Kuyruk boşaldığında hedefe ulaşılmamışsa, None döndürülür.

## Neden Bu Algoritmalar Kullanıldı?

BFS, en az aktarmalı rotayı bulmada etkilidir çünkü istasyonlar arasındaki aktarma sayısını minimize eder.
A*, süre bazlı en kısa rotayı bulmada etkilidir çünkü her adımda en düşük maliyetli hareket tercih edilir.

## 4. Örnek Kullanım ve Test Sonuçları

## Örnek Senaryolar:
Aşağıdaki test senaryoları metro ağı üzerinde çalıştırılmıştır.

![Örnek Senaryolar](https://raw.githubusercontent.com/gamzebacak/MetroSimulation/399aeddba67b60e0e2624c871960704327c339a8/Test%20Sonu%C3%A7lar%C4%B1.jpeg)

## Çalıştırma Örneği:

![Örnek Kod](https://github.com/gamzebacak/MetroSimulation/blob/main/%C3%87al%C4%B1%C5%9Ft%C4%B1rma%20%C3%96rne%C4%9Fi.jpeg?raw=true)

Bu kod, "Kızılay" ve "AŞTİ" istasyonları arasında en az aktarmalı rotayı döndürür.

## Sonuçlar: Test sonuçlarına göre, BFS en az aktarmalı rota belirlemede başarılı olurken, A* algoritması süre bazlı en iyi rotayı bulmada etkili olmuştur. Proje, büyük metro ağlarında da çalışabilir şekilde optimize edilmiştir.
