# GPS Spoofing ve Konum Yönlendirme Araştırması
## 1. Giriş
GNSS sistemleri (GPS, Galileo, GLONASS, BeiDou) modern ulaşım, finans, telekom ve savunma alanlarında kritik öneme sahiptir. Sivil GNSS alıcıları düşük sinyal gücü ve mesaj doğrulaması olmayan yapıları nedeniyle spoofing saldırılarına açıktır. Bu çalışmada amaç, spoofing’in teorik temellerini, risklerini ve güvenli test yöntemlerini detaylı bir şekilde ortaya koymaktır.

## 2. GPS Spoofing Nedir ve Ne İşe Yarar?
GPS spoofing, bir alıcıya sahte konum, hız veya zaman verisi göndererek yanlış PVT (position, velocity, time) hesaplatma saldırısıdır. Amaçları şunlardır:
- ARGE ve akademik araştırma senaryoları
- Savunma/elektronik harp testleri
- Drone ve otonom sistemlerin güvenlik testleri
- Zaman ve konum bağımlı kritik altyapıların güvenlik analizi

## 3. GPS Spoofing: Zafiyet, Sızma ve Exploit Mantığı

### 3.1 Zaafiyetin Temel Kaynakları
1. **Sivil GNSS sinyallerinin doğrulamasız olması:**
   - Sivil GPS, Galileo veya GLONASS alıcıları şifreleme ve mesaj doğrulaması kullanmaz.
   - Alıcı, sinyali güçlü olduğu sürece gerçek kabul eder → “güç temelli güvenlik açığı”.

2. **Tek kaynak bağımlılığı:**
   - Alıcı tek GNSS konstelasyonuna bağlıysa, sahte sinyal tek noktadan başarıyla yanıltabilir.
   - Multi-constellation ve multi-frequency sistemlerde risk azalır.

3. **Zaman ve frekans hassasiyeti:**
   - Alıcı, sinyalin kod ve taşıyıcı fazını takip eder.
   - Küçük değişiklikler bile alıcının PVT çözümünü saptırabilir.

4. **Alıcı tarafındaki mantıksal eksiklikler:**
   - RAIM (Receiver Autonomous Integrity Monitoring) gibi kontroller kapalı veya zayıf olabilir.
   - Doppler ve carrier-to-noise ratio analizi yapılmazsa sahte sinyal kolay kabul edilir.

### 3.2 Sızma Yöntemleri
- **Replay / Meaconing:** Gerçek sinyal kaydedilip laboratuvar ortamında veya simülatörde oynatılır. Alıcı kısa süreli yanlış konum üretebilir.
- **Aligned / Carry-off Spoofing:** Alıcı ile senkronize olduktan sonra sinyal yavaşça manipüle edilir. Konum ve yönlendirme hataları üretilir.
- **Fake Constellation:** Tamamen sahte uydu sinyalleri laboratuvar ortamında oluşturulur. Alıcıya yanlış PVT çözümleri verilir.
- **Sensor Fusion Bypass:** IMU veya odometri verisi alıcı tarafından cross-check yapılmadan kullanılıyorsa, sahte GNSS sinyali ile hatalı senkronizasyon sağlanabilir.

### 3.3 Exploit Mantığı
1. **Hedef Alıcı Analizi:** Hangi GNSS konstelasyonları kullanılıyor, RAIM ve plausibility kontrolleri açık mı?
2. **Sinyal Modelleme:** Offline I/Q datasetleri veya simülatör kullanarak sahte sinyal oluştur. Sinyal gücü ve faz senkronizasyonu laboratuvar ortamında ayarlanır.
3. **Senaryo Testi:** Sahte sinyal ile alıcı PVT değişiklikleri gözlemlenir. Yanlış konum, hız ve zaman hataları kaydedilir.
4. **Tespit ve Analiz:** Anomali tespiti: Doppler shift, carrier-to-noise ratio, PRN tutarlılığı. Detection algoritmaları: CUSUM, ML tabanlı sınıflandırma.

### 3.4 Kullanım Alanları
- **Red Team / PenTest:** Drone veya otonom araç güvenlik testi.
- **Savunma ARGE:** GNSS spoofing senaryoları simülasyonu.
- **Akademik Çalışmalar:** Spoofing tespit algoritmaları geliştirme.
- **Kritik Altyapı Testi:** Finans, telekom veya denizcilik senaryolarında risk analizi.

## 4. Laboratuvar Bazlı Etik Deney Tasarımı
- Offline I/Q kayıtları kullanılır (TEXBAT, FGI, Mendeley).
- RF yayını yapılmaz, simülatör veya izole laboratuvar ortamı kullanılır.
- Tespit algoritmaları: CUSUM, Random Forest, LSTM.
- Performans metrikleri: Detection Rate, False Positive Rate, Time-to-Detect, Konum Hatası.

## 5. Adım Adım Analiz Önerisi
1. **Dataset seçimi:** TEXBAT veya FGI datasetleri.
2. **Özellik çıkarımı:** SNR, Doppler, PRN sayısı, PVT residuals.
3. **Algoritma uygulama:** ML veya istatistiksel anomali tespiti.
4. **Performans analizi:** ROC eğrileri, CDF, detection time.
5. **Savunma değerlendirmesi:** Çoklu sensör ve konstelasyon kullanımı.

## 6. Spoofing’in Potansiyel Etkileri
- Yanlış konum ve rota hesaplamaları.
- Zaman kritik sistemlerde domino etkisi ve senkronizasyon hataları.
- Drone veya otonom araçlarda yönlendirme hataları.
- Kritik altyapı hataları ve sistem güvenliği riski.

## 7. Tespit ve Savunma Yöntemleri
- **Kryptografik doğrulama:** Galileo OSNMA.
- **RAIM ve alıcı iç tutarlılık kontrolü.**
- **Çoklu konstelasyon ve frekans karşılaştırması.**
- **Sinyal-temelli tespit:** SNR, Doppler, carrier-to-noise ratio.
- **DOA ve çoklu anten kullanımı.**
- **Sensör füzyonu:** IMU, odometri, vision tabanlı kontrol.
- **ML tabanlı anomali tespiti.**
