# Kalk, Geldik (Android)

Varışa belirlediğin mesafe kalınca seni uyandıran otobüs alarmı. Konum takibi ve alarm arka plandaki bir servistedir, ekran kapalıyken de çalışır. Arayüz `app/src/main/assets/index.html` içindedir.

## APK'yı almak (Android Studio kurmadan)

1. github.com'da yeni bir depo aç (Private olabilir).
2. Bu klasörün içindekileri depoya yükle: **Add file > Upload files**, `.github` klasörü dahil hepsini sürükle. Gizli klasör görünmüyorsa: Windows'ta Görünüm > Gizli öğeler, Mac'te Cmd+Shift+Nokta.
3. **Commit changes**'e bas. Üstteki **Actions** sekmesinde "APK derle" kendiliğinden çalışır (5-8 dk). Çalışmazsa Actions > APK derle > Run workflow.
4. Bitince çalıştırmanın sayfasında, en altta **Artifacts** bölümünden `kalk-geldik-apk`'yı indir. Zip'in içindeki `app-debug.apk`'yı telefona gönder.
5. Telefonda APK'ya dokun, "bilinmeyen kaynaklardan yükleme" iznini ver ve kur.

## Android Studio ile

Klasörü **Open** ile aç. Gradle sürümü sorarsa 8.9, JDK sorarsa 17 seç. Telefonu USB hata ayıklama açık bağla ve **Run**'a bas.

## İlk kullanım

- Konum iznini ver ve "Kesin" konumu seç. Bildirim iznini de ver.
- "Pil kısıtlamasını kapat" düğmesiyle uygulamayı pil kısıtlamasından çıkar. Samsung, Xiaomi, Huawei gibi telefonlarda ayrıca "uyku modundaki uygulamalar" listesinden de çıkar.
- Yolculuktan önce "Sesi dene" ve "Simülasyonla dene" ile alarmı kontrol et. Alarm, telefonun "Alarm" ses kanalından çalar ve çalarken ses otomatik en yükseğe çıkar.

## Dosyalar

- `MainActivity.kt`: arayüz (WebView) ve izinler
- `TripService.kt`: arka planda konum takibi ve alarm
- `TripState.kt`: servis ile ekranın paylaştığı durum
- `Sounds.kt` ve `res/raw/alarm_*.wav`: alarm sesleri

## Bilinen sınırlar

- Harita internet ister. Konum takibi ve alarm internetsiz de çalışır.
- Mesafe düz çizgi ölçülür, yol biraz daha uzun olabilir.
- Bu kod, hazırlandığı ortamda derlenip telefonda denenemedi. Derleme hatası çıkarsa Actions'taki kırmızı adımın günlüğünü kopyalayıp gönder.
