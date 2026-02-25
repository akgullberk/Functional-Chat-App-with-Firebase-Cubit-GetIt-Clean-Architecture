## 💬 Messenger App

![Flutter](https://img.shields.io/badge/Flutter-%2302569B.svg?style=for-the-badge&logo=Flutter&logoColor=white)
![Dart](https://img.shields.io/badge/dart-%230175C2.svg?style=for-the-badge&logo=dart&logoColor=white)
![Firebase](https://img.shields.io/badge/Firebase-%23FFCA28.svg?style=for-the-badge&logo=firebase&logoColor=black)
![BLoC](https://img.shields.io/badge/State-Cubit%2FBLoC-blue?style=for-the-badge)
![get_it](https://img.shields.io/badge/DI-get__it-purple?style=for-the-badge)

Messenger App, kullanıcıların rehberlerindeki kayıtlı kişilerle gerçek zamanlı sohbet edebildiği, çevrimiçi/çevrimdışı durumlarını görebildiği ve modern bir mesajlaşma deneyimi sunan bir mobil uygulamadır. Firebase üzerinde çalışan **gerçek zamanlı altyapı** ve **Cubit tabanlı state management** ile geliştirilmiştir.

---

### 🚀 Özellikler

- **E-posta ile Giriş ve Kayıt:** Firebase Auth ile güvenli kullanıcı kaydı ve oturum açma.
- **Rehber Entegrasyonu:** `flutter_contacts` ile cihaz rehberini okuyup, uygulamaya kayıtlı kullanıcıları telefon numaralarına göre eşleştirme.
- **Gerçek Zamanlı Mesajlaşma:** Cloud Firestore stream’leri ile anlık mesaj gönderme ve alma.
- **Sohbet Listesi ve Son Mesaj Özeti:** Her sohbet odası için son mesaj içeriği ve sıralanmış sohbet listesi.
- **Çevrimiçi / Son Görülme Durumu:** Kullanıcıların anlık çevrimiçi durumu ve son görülme zamanının gösterilmesi.
- **Yazıyor Göstergesi:** Karşı taraf yazı yazarken üst barda “typing” animasyonu ile bilgilendirme.
- **Okundu Bilgisi ve Mesaj Durumu:** Mesajların gönderildi/okundu durumunu ikon ve renklerle gösterme.
- **Kullanıcı Engelle / Engeli Kaldır:** İstemediğiniz kullanıcıları engelleme ve engeli kaldırma akışı.
- **Emoji Desteği:** `emoji_picker_flutter` ile zengin emoji klavyesi entegrasyonu.
- **Rehberden Yeni Sohbet Başlatma:** Alt sayfada açılan rehber modali üzerinden hızlı sohbet başlatma.
- **Modern UI/UX:** Material 3 tabanlı, sade ve okunabilir arayüz; özelleştirilmiş tema ve bileşenler.

---

### 🛠️ Teknik Stack

- **Framework:** [Flutter](https://flutter.dev)
- **Dil:** Dart
- **Backend:** [Firebase](https://firebase.google.com) (Auth & Cloud Firestore)
- **State Management:** [flutter_bloc](https://pub.dev/packages/flutter_bloc) (Cubit yapısı)
- **Dependency Injection:** [get_it](https://pub.dev/packages/get_it)
- **Navigasyon:** `GlobalKey<NavigatorState>` kullanan özel `AppRouter`
- **Contacts API:** [flutter_contacts](https://pub.dev/packages/flutter_contacts)
- **Emoji Desteği:** [emoji_picker_flutter](https://pub.dev/packages/emoji_picker_flutter)
- **Yardımcı Paketler:** [intl](https://pub.dev/packages/intl), [equatable](https://pub.dev/packages/equatable)

---

### 🏗️ Mimari Yapı

Uygulama, okunabilirlik ve genişletilebilirlik için katmanlara ayrılmıştır:

- **config:** Tema yapılandırmaları (`AppTheme`) ve genel uygulama ayarları.
- **core:** Ortak kullanılan widget’lar (`CustomButton`, `CustomTextField`) ve yardımcı sınıflar (`UiUtils`).
- **data:**
  - **models:** `UserModel`, `ChatRoomModel`, `ChatMessage` gibi Firestore modelleri.
  - **repositories:** `AuthRepository`, `ChatRepository`, `ContactRepository` ile Firebase & cihaz API erişimi.
  - **services:** `service_locator.dart` ile `get_it` tabanlı bağımlılık yönetimi ve Firebase başlangıç ayarları.
- **logic:** Uygulama iş mantığını yöneten Cubit’ler ve observer:
  - `AuthCubit`, `ChatCubit`, `AppLifeCycleObserver`.
- **presentation:**
  - **screens:** `LoginScreen`, `SignupScreen`, `HomeScreen`, `ChatMessageScreen` gibi sayfalar.
  - **widgets:** `ChatListTile`, `MessageBubble`, `LoadingDots` gibi tekrar kullanılabilir UI bileşenleri.
- **router:** `AppRouter` ile sayfa geçişleri ve `navigatorKey` yönetimi.
- **firebase_options.dart:** FlutterFire CLI ile üretilmiş Firebase konfigürasyonu.
- **main.dart:** Uygulama giriş noktası; `setupServiceLocator()` çağrısı, tema ve başlangıç ekranı yönetimi.

#### 📂 Proje Dizini

```text
lib/
├── config/               # Tema ve genel konfigürasyon
├── core/                 # Ortak widget'lar ve yardımcı sınıflar
├── data/                 # Modeller, repository'ler ve servisler
├── logic/                # Cubit'ler ve yaşam döngüsü observer'ı
├── presentation/         # Ekranlar ve UI bileşenleri
├── router/               # Navigasyon yönetimi (AppRouter)
├── firebase_options.dart # Firebase konfigürasyonu
└── main.dart             # Uygulama giriş noktası
```

---

### 🎨 Tasarım Detayları

Uygulama, hafif ve modern bir **aydınlık tema (Light Mode)** üzerine inşa edilmiştir:

- **Ana Renk:** `#692960` (mor tonunda vurgu rengi)
- **Yüzey / Arka Plan:** Beyaz ağırlıklı arka planlar ve sade kartlar.
- **Mesaj Balonları:**
  - Gönderen için: ana renk arka plan, beyaz metin.
  - Alıcı için: ana rengin düşük opaklıkta tonu ve koyu metin.
- **Tipografi:** Material 3 `TextTheme` üzerinde başlık, gövde ve etiket stilleri özelleştirilmiştir.
- **Formlar ve Input Alanları:** Yuvarlatılmış köşeler, hafif arka plan rengi ve belirgin ikon kullanımı.

---


