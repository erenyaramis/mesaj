# Gelişmiş Yerel Sohbet (Advanced Local Chat)

Tarayıcı üzerinden çalışan, PeerJS (WebRTC) altyapısı ile uçtan uca (P2P) şifreli metin ve sesli iletişim sağlayan web tabanlı bir sohbet uygulamasıdır. Merkezi bir mesajlaşma sunucusuna ihtiyaç duymadan cihazların doğrudan birbirine bağlanmasını sağlar.

## 🌟 Öne Çıkan Özellikler
* **Otomatik Cihaz Keşfi:** Ortak bir "Ağ/Oda Adı" kullanan cihazlar MQTT protokolü üzerinden birbirini otomatik olarak bulur.
* **Uçtan Uca (P2P) İletişim:** Mesajlar ve ses verisi, WebRTC mimarisi ile sunucuya uğramadan doğrudan iki cihaz arasında şifreli olarak iletilir.
* **Gerçek Zamanlı Sesli Arama:** Kullanıcılar tarayıcı üzerinden doğrudan ve gecikmesiz sesli görüşme yapabilir.
* **QR Kod Entegrasyonu:** Bağlantı kurmak için ekranda QR kod oluşturabilir veya cihaz kamerasından QR kod okutabilirsiniz.

---

## 🚀 Adım Adım Kurulum ve Kullanım Kılavuzu

Bu proje herhangi bir arka uç (backend) kodlaması veya veritabanı kurulumu gerektirmez. Sadece HTML, CSS ve JavaScript'ten oluşur.

### Aşama 1: Dosyayı Oluşturma
1. Bilgisayarınızda yeni bir klasör oluşturun (Örn: `yerel-sohbet`).
2. Klasörün içine `index.html` adında bir dosya açın.
3. Projeye ait tüm kodları bu dosyanın içerisine yapıştırıp kaydedin.

### Aşama 2: Bilgisayarda (Yerel Ortamda) Test Etme
Projenin temel mesajlaşma özelliklerini kendi bilgisayarınızda hemen test edebilirsiniz:
1. `index.html` dosyasına çift tıklayarak tarayıcınızda (Chrome, Edge vb.) açın.
2. Karşınıza çıkan ekranda **Adınızı** yazın (Örn: Ahmet).
3. **Ağ / Oda Adı** kısmına bir isim belirleyin (Örn: `TestAgi123`). Bu odayı kullanan herkes birbirini görecektir.
4. **"Bağlan ve Keşfet"** butonuna tıklayın.
5. İkinci bir cihazı simüle etmek için tarayıcınızda yeni bir sekme (veya gizli sekme) açın ve aynı işlemleri farklı bir isimle tekrarlayın.
6. "Ağdaki Cihazlar" listesinde diğer cihazı göreceksiniz. **"Bağlan"** diyerek sohbeti başlatın.

### Aşama 3: Mobil Cihazlarda Kullanım İçin Canlıya Alma (Kritik Aşama)
Uygulamanın QR kod tarama (kamera) ve sesli arama (mikrofon) özelliklerinin özellikle mobil cihazlarda çalışabilmesi için güvenlik politikaları gereği **HTTPS** (Güvenli Bağlantı) üzerinden çalışması zorunludur. Dosyayı sadece telefona atarak veya yerel IP adresiyle (http://192...) açarsanız donanım erişim izni verilmez.

Bunu çözmek için projeyi bir sunucuya yüklemeniz gerekir:
1. `index.html` dosyanızı Hosting Dünyam gibi bir sağlayıcıdaki mevcut sunucu alanınıza (public_html klasörüne) yükleyin.
2. Bağlı olan alan adınızı Cloudflare üzerinden yönlendirerek SSL sertifikasını (HTTPS) aktif duruma getirin.
3. Artık uygulamanıza `https://sizin-siteniz.com` adresi üzerinden telefonla giriş yaptığınızda tarayıcı sizden kamera ve mikrofon izni isteyecek ve sistem sorunsuz çalışacaktır.

*(Alternatif olarak projeyi Vercel, Netlify veya GitHub Pages gibi ücretsiz statik hosting servislerine yükleyerek de otomatik HTTPS linki elde edebilirsiniz.)*

---

## 📱 Arayüz Kullanım Adımları

Bağlantı kurulduktan sonra uygulamanın özelliklerini şu şekilde kullanabilirsiniz:

### 1. Manuel Bağlantı Kurma
* Giriş yaptıktan sonra ekrandaki cihaz listesinden bağlanmak istediğiniz kişinin yanındaki **"Bağlan"** butonuna basın.
* Karşı tarafa bir bağlantı isteği (Kabul Et / Reddet) gidecektir.
* Kabul edildiğinde sohbet ekranı otomatik olarak açılır.

### 2. QR Kod ile Hızlı Eşleşme
* **Kod Gösteren Kişi:** Cihaz listesi ekranında **"QR Göster"** butonuna tıklar. Ekranda o cihaza ait özel bir karekod belirir.
* **Kodu Okuyan Kişi:** Kendi telefonundan **"QR Tara"** butonuna basar. Kamera açılır ve diğer ekrandaki kodu okutur.
* Okuma başarılı olduğunda sistem otomatik olarak bağlantı isteğini gönderir.

### 3. Sesli Arama Yapma
* Sohbet ekranındayken üst kısımdaki **"Sesli Ara 📞"** butonuna tıklayın.
* Tarayıcı sizden mikrofon erişim izni isteyecektir, onaylayın.
* Karşı tarafın ekranında bir arama uyarısı çıkar. Aramayı cevapladığında sesli iletişim başlar.
* Görüşmeyi bitirmek için **"Aramayı Bitir 📞"** butonuna tıklamanız yeterlidir.

---

## 🛠 Kullanılan Teknolojiler

* **Arayüz:** HTML5, CSS3, JavaScript (Mobil Uyumlu Vanilla JS)
* **P2P Ağ ve WebRTC:** [PeerJS](https://peerjs.com/) (Güvenli veri ve medya aktarımı)
* **Sinyalleşme ve Keşif:** [MQTT.js](https://github.com/mqttjs/MQTT.js) (Oda bazlı eşleşme için public HiveMQ broker)
* **QR Modülleri:** `qrcode.js` (Oluşturma) ve `html5-qrcode` (Tarama)
