# 🛡️ Jungheinrich ERE 225a (AGV) — Safety 4.0 & Siber-Emniyet (OT Security) Portföyü

Bu repository, **Safety 4.0 Bootcamp** metodolojisi çerçevesinde[cite: 1], **Jungheinrich ERE 225a Sürücüsüz Taşıma Sistemi (AGV / Akülü Transpalet)** hedef alınarak hazırlanan endüstriyel siber-fiziksel güvenlik ve siber-emniyet laboratuvar çalışmalarını ve risk analizlerini içermektedir.

---

## 📌 Makine Kimliği ve Teknik Özellikler
* **Ürün / Model:** Jungheinrich ERE 225a — Sürücüsüz Taşıma Sistemi (AGV) / Otomasyonlu Akülü Transpalet.
* **Üretici:** Jungheinrich Aktiengesellschaft (Hamburg, Almanya).
* **Kapasite ve Performans:** Maksimum 2.500 kg yük kapasitesi, 122 mm kaldırma yüksekliği, 6,1 km/h sürüş hızı (yüklü/yüksüz), 24 V Lityum-İyon batarya teknolojisi.
* **Navigasyon ve İletişim:** Sürüş yolu reflektörleri üzerinden milimetrik lazer navigasyonu, mevcut WLAN altyapısı, FTS kontrol istasyonu ve WMS/ERP entegrasyonu için Jungheinrich lojistik arayüzü.

---

## 📊 SWOT Analizi (Siber-Fiziksel Sistemler & Safety 4.0 Perspektifi)

| **Güçlü Yönler (Strengths)** | **Zayıf Yönler (Weaknesses)** |
| :--- | :--- |
| • **Gelişmiş Otonom Emniyet Donanımı:** Hıza duyarlı kişi koruma sensörleri, virajlarda öngörülü engel taraması ve yan sensörler.<br>• **Yenilikçi Enerji Yönetimi:** Lityum-iyon (Li-Ion) batarya sayesinde gaz oluşumu riski taşımayan, şarj odası izolasyonu istemeyen yapı.<br>• **Hibrit Operasyonel Esneklik:** Standart kumanda kolu ile otonom (AGV) ve manuel kullanım arasında geçiş.<br>• **Hassas Konumlandırma:** Sürüş yolu reflektörleri ve lazer navigasyon ile milimetrik konumlama. | • **Genişletilmiş Siber Saldırı Yüzeyi:** İletişim için tesisin "mevcut" paylaşımlı kablosuz ağının (WLAN) kullanılması, ağ izolasyonunu (IEC 62443) zorlaştırır[cite: 1, 11].<br>• **IT/OT Yakınsaması Riskleri:** WMS/ERP sistemlerine doğrudan entegrasyon, kurumsal (IT) ağ zafiyetlerinin OT sahasına sıçrama riskini doğurur[cite: 1, 14].<br>• **Kritik Korumaların Opsiyonelliği:** Yük yönünde kişi koruma ve çatal kırılma algılayıcılarının opsiyonel sunulması. |

| **Fırsatlar (Opportunities)** | **Tehditler (Threats)** |
| :--- | :--- |
| • **IEC 62443 Odaklı Ağ Segmentasyonu:** FTS kontrol istasyonu ve AGV haberleşme ağının Endüstriyel DMZ mimarisiyle izole edilmesi[cite: 1, 11, 14].<br>• **Holistik Savunma (Defense in Depth):** Fiziksel emniyet fonksiyonlarının siber katmanlarla (MFA, VPN, Jump Server) desteklenmesi[cite: 1, 21]. | • **Kritik Fiziksel Etki (S=3):** 2.500 kg kapasiteli ve 6,1 km/s hızla hareket eden sistemde siber müdahalenin can kaybına yol açabilmesi[cite: 1, 19].<br>• **Kablosuz Ağ (WLAN) Manipülasyonu:** Ortak ağ üzerinden araç rotalarının değiştirilmesi veya frenlerin engellenmesi[cite: 1, 4]. |

---

## 🧪 Laboratuvar Raporları (Lab 1 — Lab 5)

### LAB 1: Safety Architecture (Safety Function Map)
* **Tehlike:** 2.500 kg yük taşıyan ve 6,1 km/h hızla otonom hareket eden AGV'nin depo çalışanlarına çarpması veya ezmesi.
* **Emniyet Fonksiyonu (Safety Function):** Tahrik yönündeki kişi koruma sensörü veya acil kapama tuşu engel algıladığında tahrik gücünün kesilip aracın durdurulması[cite: 1].
* **Emniyet Sistemi:** Kişi koruma sensörleri + acil kapama tuşu $\rightarrow$ Safety PLC $\rightarrow$ STO / Elektromekanik Fren[cite: 7].
* **Normal vs Safety PLC:** Normal kontrolcü navigasyon ve görevleri yönetirken; Safety PLC bağımsız, sertifikalı ve insanı korumayı garanti eden donanımsal yapıdır[cite: 1, 7].
* **Siber Müdahale Noktası:** WLAN veya FTS kontrol istasyonunun emniyet parametrelerine eriştiği dijital kesişim noktası[cite: 1, 7].

### LAB 2: IEC 62443 Mini Workshop (Zone / Conduit Diagram)
* **Bölgeleme (Zones):** Enterprise IT Zone, Industrial DMZ (Lojistik Arayüzü / Jump Server), Supervisory & Wireless Zone (FTS & WLAN), AGV Control Zone, AGV Safety Zone[cite: 1, 11, 14].
* **Conduit Kontrolleri:** IT/WMS ile AGV arasında Firewall filtrelemesi; WLAN trafiğinde şifreleme; Safety PLC ile normal kontrolcü arasında fiziksel/mantıksal salt-okunur izolasyon[cite: 1, 7, 11, 14].
* **Uzak Erişim Kararları:** Jump server aracı, VPN tünelleme, MFA kimlik doğrulama, kişisel hesaplar, tam oturum kaydı ve varsayılan kapalı ilkesi[cite: 1, 15, 21].

### LAB 3: Threat & Risk + Risk Matrix (Risk Register)
* **Kritik Senaryo (Skor: 18):** Dış/İç saldırganın ortak WLAN ağı üzerinden FTS sunucusuna sahte rota basması ve AGV'nin virajda yük devirerek çalışanı yaralaması ($L=3, S=2, E=3$)[cite: 19].
* **S=3 Kuralı:** Sensör körleştirme senaryosu ($S=3$) düşük skorlu çıksa dahi ölümcül sonuç potansiyeli nedeniyle risk register'ın en başına alınır[cite: 1, 19].

### LAB 4: Secure Remote Access (Secure Architecture)
* **Mevcut Durum:** Doğrudan WLAN'a bağlı, ortak hesaplı ve kayıtsız savunmasız uzaktan erişim[cite: 21].
* **Hedef Mimari:** Jump server, VPN, MFA, varsayılan kapalı portlar ve tam oturum kaydı[cite: 1, 21].
* **Functional Safety Köprüsü:** Emniyet zinciri (kişi koruma ve acil durdurma), WLAN ve normal navigasyondan tamamen bağımsız çalışarak siber ihlalde bile aracı güvenli duruma geçirmelidir[cite: 1, 21].

### LAB 5: SBOM / CVE / Patch (Vulnerability Decision)
* **Zafiyet Analizi:** Lojistik arayüz kütüphanesindeki Kritik (CVSS 9.8) zafiyetin AGV'nin WLAN/WMS bağlantısı nedeniyle sistemi etkilediği doğrulanır[cite: 23].
* **Yama Stratejisi:** Üretim anında kesinti yapılmaz; önce izole test ortamında (test AGV'si üzerinde) doğrulanır, ardından planlı bakımda uygulanır[cite: 1].
* **Telafi Edici Önlem (Compensating Control):** Ağ segmentasyonu (WLAN'ı BT ağından ayırma) ve beyaz liste (whitelist) tabanlı FTS erişim kısıtlaması[cite: 1, 11, 14].

---
*Bu doküman Safety 4.0 Bootcamp kapsamında eğitim ve mühendislik analizi amacıyla oluşturulmuştur.*
