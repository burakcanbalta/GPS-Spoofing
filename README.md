# GPS Spoofing ve Konum Yönlendirme Araştırması

## Özet (Abstract)
Bu çalışma, sivil GNSS sinyalleri üzerinde gerçekleştirilen spoofing tehditlerini kapsamlı olarak incelemekte, zafiyetlerin ortaya çıkış mekanizmalarını, potansiyel istismar senaryolarını, laboratuvar ortamında analiz ve tespit yöntemlerini detaylı şekilde ele almaktadır. Deneyler yalnızca kayıtlı datasetler ve simülatörler kullanılarak yürütülmüştür.

## 1. Giriş
GNSS sistemleri (GPS, Galileo, GLONASS, BeiDou) modern ulaşım, finans, telekom ve savunma alanlarında kritik öneme sahiptir. Sivil GNSS alıcıları düşük sinyal gücü ve mesaj doğrulaması olmayan yapıları nedeniyle spoofing saldırılarına açıktır. Bu çalışmada amaç, spoofing’in teorik temellerini, risklerini ve güvenli test yöntemlerini detaylı bir şekilde ortaya koymaktır.

## 2. GPS Spoofing Nedir ve Ne İşe Yarar?
GPS spoofing, bir alıcıya sahte konum, hız veya zaman verisi göndererek yanlış PVT (position, velocity, time) hesaplatma saldırısıdır. Amaçları şunlardır:
- ARGE ve akademik araştırma senaryoları
- Savunma/elektronik harp testleri
- Drone ve otonom sistemlerin güvenlik testleri
- Zaman ve konum bağımlı kritik altyapıların güvenlik analizi

## 3. Çalışma Prensibi ve Kullanım Alanları
### 3.1 Temel Kavramlar
- **Alıcı ve uydu senkronizasyonu:** Alıcı uydu sinyalini çözer ve PVT hesaplar.
- **Spoofing mantığı:** Saldırgan sahte sinyal üreterek alıcının çözümünü manipüle eder.

### 3.2 Teknik Yöntemler
- **Meaconing / Replay:** Gerçek sinyal kaydedilip zaman/faz değiştirerek yeniden gönderilir.
- **Carry-off / Aligned Spoofing:** Alıcı ile senkronize olduktan sonra sinyal yavaşça manipüle edilir.
- **Fake Constellation:** Tamamen sahte uydular ile alıcı yanıltılır.

## 4. Zaafiyetler ve Risk Mekanizmaları
- Sivil alıcıların sinyal doğrulaması yok.
- Tek GNSS kaynağına bağımlı alıcılar yüksek risk altında.
- Kritik altyapılar (finans, telekom, denizcilik) hedef olabilir.
- Anomalilere karşı sınırlı plausibility kontrolü bulunur.

## 5. Laboratuvar Bazlı Etik Deney Tasarımı
- Offline I/Q kayıtları kullanılır (TEXBAT, FGI, Mendeley).
- RF yayını yapılmaz, simülatör veya izole laboratuvar ortamı kullanılır.
- Tespit algoritmaları: CUSUM, Random Forest, LSTM.
- Performans metrikleri: Detection Rate, False Positive Rate, Time-to-Detect, Konum Hatası.

## 6. Adım Adım Analiz Önerisi
1. **Dataset seçimi:** TEXBAT veya FGI datasetleri.
2. **Özellik çıkarımı:** SNR, Doppler, PRN sayısı, PVT residuals.
3. **Algoritma uygulama:** ML veya istatistiksel anomali tespiti.
4. **Performans analizi:** ROC eğrileri, CDF, detection time.
5. **Savunma değerlendirmesi:** Çoklu sensör ve konstelasyon kullanımı.

## 7. Spoofing’in Potansiyel Etkileri
- Yanlış konum ve rota hesaplamaları.
- Zaman kritik sistemlerde domino etkisi ve senkronizasyon hataları.
- Drone veya otonom araçlarda yönlendirme hataları.
- Kritik altyapı hataları ve sistem güvenliği riski.

## 8. Tespit ve Savunma Yöntemleri
- **Kryptografik doğrulama:** Galileo OSNMA.
- **RAIM ve alıcı iç tutarlılık kontrolü.**
- **Çoklu konstelasyon ve frekans karşılaştırması.**
- **Sinyal-temelli tespit:** SNR, Doppler, carrier-to-noise ratio.
- **DOA ve çoklu anten kullanımı.**
- **Sensör füzyonu:** IMU, odometri, vision tabanlı kontrol.
- **ML tabanlı anomali tespiti.**
