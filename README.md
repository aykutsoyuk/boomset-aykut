# boomset-aykut

## Front-End Developer Egzersiz
Aykut Söyük

28.12.2020

[Uygulamaya git](https://aykutsoyuk.github.io/boomset-aykut/)

### Uygulamanın Özellikleri

* Proje Vue framework ile Boomset Public API kullanılarak oluşturulmuştur.
* Ana sayfada kullanıcıya ait bilgilerin bulunduğu bir sidebar ve eventlerin sıralandığı ayrı bir bileşen oluşturulmuştur. 
* Eventler isme göre sıralanmış, eklenen arama çubuğu ile istenen evente kolaylıkla ulaşım sağlanmıştır.
* Event bloğuna tıklandığında o evente ait detay sayfası açılmaktadır.
* Detay sayfasında kullanıcıya, eventin hangi tarihte başlayıp biteceği, detaylı açıklaması, konuk sayısı ve en yakın tarihe göre sıralanmış oturumları gösterilmektedir.
* Uygulama mobile, tablet ve desktop cihazlarda sorunsuz çalışmaktadır.

### Uygulamayı local olarak çalıştırmak için: 

1. Github reposunu bilgisayarınıza klonlayın.
2. Klonladığınız dosyanın içinde "npm install" komutunu çalıştırın.
3. "npm run serve" komutu ile uygulamayı çalıştırın. 
4. Tarayıcınızda localhost:8080'e gidin.

### İyileştirmeler

- [ ] Vue Router uygulamak
- [ ] Kullanıcı arayüzü için API error yakalama


### Known Bugs

- [ ] API cevabı geldikten sonra "EventDetails" componenti bir süre için render olmuyor. Ve UI yapısı bozuluyor.
- [ ] API'dan cevap gelmeden detay sayfası açılıyor ve küçük bir an için bir önceki eventin bilgisi görünüyor.


### Kopyala yapıştır

"Loader" ın kaynağını [buradan](https://loading.io/css/) kopyaladım. 

---

Aykut Söyük | aykutsoyuk@gmail.com | www.linkedin.com/in/aykutsoyuk

