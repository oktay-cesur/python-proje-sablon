# Python Dönem Projesi Yönergesi

## Genel Çerçeve

Bu projede dersimiz boyunca öğrendiğiniz yöntem ve teknikleri kullanarak gerçek bir problemi çözen bir yazılım geliştireceksiniz. Konu serbesttir: insan kaynaklarından muhasebeye, iş takibinden oyun geliştirmeye kadar geniş bir yelpaze mümkündür. Yönergede doğrudan sayılmayan bir konu da seçilebilir; önemli olan projenin gerçek bir problemi çözmesi ve aşağıdaki teknik gereklilikleri karşılamasıdır. Ancak konu ilginç olsa bile çekirdek gereklilikleri karşılamayan projeler yeterli kabul edilmeyecektir.

Başlangıçta belirtmek gerekir ki proje buradan bakınca göz korkutucu görünebilir. Bu yönergedeki kriterlerin büyük çoğunluğu temel sektör standartlarına dayanmaktadır; fakat bu, sizden sektör standardında kod yazmanızı beklediğim anlamına gelmemektedir. Elbette öğrenme aşamasında olduğunuzun farkındayım ve beklentilerim de bu doğrultudadır. Puanlama kısmında hangi kriterin kaç puan olduğu ve hangi düzeyde neyi karşılaması gerektiği yazmaktadır. Projeniz bu kriterleri ne kadar karşılarsa o kadar puan alırsınız. Yetersiz kalan kısımlar notunuzu aşağı çeker, iyi yapılan kısımlar ise yukarı taşır.

Burada asıl beklediğim şey, projenin size ait olması ve projeyi açıklayabilmenizdir. Yapay zekâdan yardım alabilirsiniz; ancak anlamadığınız kodu, sorguyu veya yapıyı projeye koymanız kabul edilmeyecektir. Örneğin veritabanında `GROUP BY`, `COUNT`, `LEFT JOIN` veya `RIGHT JOIN` kullanan bir öğrenci, en temel `SELECT * FROM urunler` sorgusunu bile açıklayamıyorsa bu proje öğrenci tarafından anlaşılmadan hazırlanmış kabul edilir. Sunum sırasında eksikler olabilir, hatalar yapabilirsiniz; ancak ileri seviye kodlar kullanıp en basit örneği açıklayamıyorsanız, bu durum kodun size ait olmadığı kanaatini doğurur. Böyle bir durumda kod çalışıyor olsa bile proje geçersiz sayılır ve durum intihal/akademik dürüstlük kapsamında değerlendirilebilir. Proje ile ilgili bir şeylerden çekiniyorsanız bu duruma düşme olmalıdır. Bu ise basit şekilde yazdığınız kodların ne olduğunu anlamanızla çözülebilir.

Buna karşılık, eksikleri olan, kusurlu çalışan veya çok gelişmiş olmayan bir proje de değerlendirilebilir. Eğer proje temel gereklilikleri kısmen karşılıyor ve öğrenci yaptığı işi sunumda açıklayabiliyorsa puan alabilir; genel olarak 50-60 arası bir not alması mümkündür. Kısacası, mükemmel görünen ama anlatılamayan proje kabul edilmeyecek; eksikleri olan ama öğrencinin gerçekten yaptığı ve açıklayabildiği proje puan alacaktır.

Başlamadan önce bu yönergeyi dikkatlice okumanız gerekmektedir. Değerlendirme, “benzer bir proje yapılmış mı” veya “program bir şekilde çalışıyor mu” sorusuna göre değil, aşağıda yazan ölçütlere göre yapılacaktır. Bu nedenle yönergede açıkça istenen bir gerekliliğin eksik olması, proje genel olarak iyi görünse bile puan kaybına yol açacaktır.

Projeler en fazla **3 kişilik** gruplar hâlinde yapılacaktır. Grup büyüklüğüne göre ek gereklilikler aşağıda belirtilmiştir.

---

## 1. Zorunlu Teknik Gereklilikler

Her projede aşağıdaki çekirdek bileşenler bulunmalıdır:

1. **Modüler yapı** — Proje tek dosyadan oluşmamalıdır. Kod işlevsel modüllere ayrılmalı; klasör yapısı anlaşılır olmalıdır.

2. **Veritabanı kullanımı** — Uygulama kalıcı veri tutmalıdır. Veriler dosya içi geçici değişkenlerle değil, bir veritabanıyla saklanmalıdır.

3. **En az üç kullanıcı tipi** — Yetkileri birbirinden gerçek anlamda farklılaşmış en az üç kullanıcı rolü bulunmalıdır (örnek: Yönetici, Standart Kullanıcı, Ziyaretçi). Her rolün hangi işlemleri yapabildiği açıkça tanımlanmalıdır.

4. **Önceden tanımlı admin hesabı** — Yönetim işlemlerini gerçekleştirebilen bir admin kullanıcı sistemde hazır bulunmalıdır.

5. **Nesne yönelimli tasarım** — Her kullanıcı tipi kendine özgü bir sınıfla temsil edilmeli; ortak özellikler için bir temel sınıf tanımlanmalı, diğer tipler bu sınıftan türetilmelidir. İşlevler yalnızca dağınık fonksiyonlar hâlinde bırakılmamalıdır.

6. **İşlem kaydı (log)** — Kullanıcıların gerçekleştirdiği temel işlemler tarih/saat bilgisiyle birlikte veritabanında kaydedilmeli; bu kayıtlar sorgulanabilir ve raporlanabilir olmalıdır.

7. **Raporlama** — Her kullanıcı kendi işlemlerine ilişkin rapor alabilmelidir. Admin, herhangi bir kullanıcının işlem kayıtlarını görüntüleyip çıktı alabilmelidir.

8. **Çalıştırılabilirlik** — Kurulum ve çalıştırma adımları açık olmalı; değerlendirici projeyi makul sürede başlatabilmelidir. Dosya ve klasör yolları işletim sisteminden bağımsız çalışacak biçimde yazılmalıdır (`os.path` veya `pathlib` kullanılmalıdır).

---

## 2. Yazılım Gereksinimleri

Program komut satırı üzerinden çalışabilir olmalıdır. İsteğe bağlı olarak Tkinter, PyQt, Streamlit, Flask veya Django gibi araçlarla görsel arayüz eklenebilir; bu bir zorunluluk değildir.

Program çalıştırıldığında kısa bir tanıtım yazısı gösterilmeli, ardından kullanıcı giriş ekranına geçilmelidir. Giriş ekranında mevcut kullanıcıyla giriş ve yeni kullanıcı kaydı seçenekleri sunulmalıdır.

---

## 3. Grup Büyüklüğüne Göre Ek Gereklilikler

Grup sayısına bağlı olarak aşağıda listelenen **ileri özelliklerden** belirtilen sayıda seçilmeli ve projeye gerçekten entegre edilmelidir:

| Grup büyüklüğü | Gereken ileri özellik sayısı |
| -------------- | ---------------------------- |
| 1 kişi         | En az 1                      |
| 2 kişi         | En az 2                      |
| 3 kişi         | En az 3                      |

**Seçilebilecek ileri özellikler:**

1. Veritabanı işlemlerinin özel bir **veritabanı sınıfı** üzerinden yürütülmesi.
2. **SQLAlchemy** ORM kullanımı.
3. **Harici API entegrasyonu** ile gerçek zamanlı veri kullanımı (döviz kuru, hava durumu, rastgele kullanıcı verisi vb.).
4. Veritabanında One-to-One, One-to-Many ve Many-to-Many ilişkilerinin tamamının bulunması ve bir **ER diyagramı** ile belgelenmesi.
5. Soyut sınıflar, kapsülleme, çok biçimlilik ve çoklu kalıtım gibi **ileri OOP prensiplerinin** etkin kullanımı ve projeye uygun bir **UML diyagramı** hazırlanması.
6. **Görsel arayüz** eklenmesi (Tkinter, PyQt, Streamlit, Flask, Django vb.).
7. Kullanıcının sisteme **dosya yükleyebilmesi**, **dosya kaydedebilmesi** veya veri çıktısı alabilmesi (PDF/CSV rapor oluşturma vb.).
8. **Grafik destekli raporlama** (`matplotlib`, `plotly`, `seaborn` vb.).
9. Admin kullanıcıların diğer kullanıcıların yetkilerini değiştirebildiği bir **yönetim paneli**.
10. Tüm işlem kayıtlarının ayrı bir dosyaya yazılması veya grafiksel olarak görüntülenmesi gibi **zenginleştirilmiş loglama** (temel loglama zorunlu gereklilik olduğundan bu kriter farklı bir yaklaşım gerektirmektedir).

Seçilen özelliğin projeye gerçekten entegre edilmesi beklenir. Çalışmayan veya yalnızca var gibi görünen eklemeler değerlendirmede katkı sayılmaz.

---

## 4. Kodlama ve Dokümantasyon Standardı

Kod yalnızca çalışır hâlde olmakla yetinmemelidir; okunabilir ve savunulabilir de olmalıdır.

- Anlamlı değişken, fonksiyon ve sınıf isimleri kullanılmalıdır.
- Her fonksiyon ve modül başında o kısmın ne işe yaradığını açıklayan kısa bir yorum bulunmalıdır.
- Yorum satırları ne gereğinden fazla ne de eksik olmalıdır; ikisi de puan kaybına yol açar. Hedef: kodu okuyan birinin sistemi anlayabilmesidir.
- Tekrar eden yapılar fonksiyonlaştırılmalıdır.
- Her modülün amacı açık olmalı; iş kuralları tek bir yerde toplanmalıdır.
- Hata yönetimi düşünülmüş olmalı; yetki kontrolü görünür biçimde uygulanmalıdır.
- Spagetti yapıdan kaçınılmalıdır.

---

## 5. Standart Teslim Yapısı

Her grup teslimini aşağıdaki yapıyla hazırlamalıdır:

```
GrupNo_ProjeAdi/
│
├── README.md
├── requirements.txt
├── main.py
├── src/                   ← kaynak kod modülleri
├── data/                  ← varsa başlangıç/örnek veri dosyaları
├── logs/                  ← örnek log çıktıları
├── outputs/               ← örnek rapor veya çıktı dosyaları
└── docs/
    └── proje_onerisi.md
    ├── teknik_rapor.md
    ├── rol_yetki_matrisi.md
    ├── veritabani_ozeti.md
    ├── senaryolar.md
    └── ai_kullanim_beyani.md

```

Klasör adları birebir aynı olmak zorunda değildir; ancak aynı tür belgeler teslimde bulunmalıdır.

---

## 6. Zorunlu Teslim Dosyaları

### README.md

En az şu bilgileri içermelidir:

- Projenin kısa tanımı ve çözdüğü problem
- Kullanılan teknolojiler
- Kurulum ve çalıştırma adımları
- Kullanıcı rolleri ve demo kullanıcı bilgileri
- Örnek kullanım akışı
- Proje klasör yapısı ve modüllerin işlevleri
- Seçilen ileri özelliklerin listesi ve projedeki yeri
- Varsa API anahtarı veya konfigürasyon ayarları hakkında bilgi

### docs/teknik_rapor.md

- Proje amacı
- Sistem mimarisi
- Kullanıcı rolleri ve görevleri
- Temel modüller
- Veritabanı yapısı
- Kullanılan ileri özellikler
- Karşılaşılan teknik problemler ve çözümleri

### docs/rol_yetki_matrisi.md

Hangi kullanıcının hangi işlemleri yapabildiği tablo hâlinde gösterilmelidir.

### docs/veritabani_ozeti.md

Kullanılan tablolar, temel alanlar ve ilişkiler kısaca açıklanmalıdır. ER diyagramı varsa buraya eklenmelidir.

### docs/senaryolar.md

Sistemin nasıl test edileceğini gösteren en az şu senaryolar bulunmalıdır:

- Başarılı giriş
- Yetkisiz işlem denemesi
- Veri ekleme / güncelleme / silme
- Rapor üretme
- Log oluşumu

### docs/ai_kullanim_beyani.md

Yapay zekâ araçları kullanıldıysa hangi bölümde, ne amaçla kullanıldığı kısaca ve dürüstçe açıklanmalıdır (kod iskeleti, hata ayıklama, dokümantasyon, SQL önerisi vb.). Bu dosya yasak mantığı için değil, akademik şeffaflık için istenmektedir.

---

## 7. Demo Verisi ve Değerlendirilebilirlik

Her proje değerlendirici tarafından tekrar üretilebilir ve incelenebilir biçimde teslim edilmelidir:

- En az bir admin ve gerekli diğer örnek kullanıcı hesapları
- Gerekirse örnek seed veri
- Örnek log çıktıları
- En az bir örnek rapor çıktısı
- Projede izlenebilecek net bir kullanım senaryosu

---

## 8. Değerlendirme Ölçütleri

Toplam puan **100** üzerinden hesaplanır. Ek olarak, yönerge kapsamını aşan nitelikli çalışmalar için **15 puana kadar bonus** verilebilir (bkz. Bölüm 9).

Her kriter üç düzeyde değerlendirilir:

- **Yetersiz:** Kriter görünürde sağlanmış olsa bile içerik projenin genel amacını karşılamıyorsa bu düzey uygulanır ve kriterin puanının yarısından fazlası verilmez.
- **Yeterli:** Kriter işlevsel ve anlamlı biçimde sağlanmıştır.
- **İyi:** Kriter beklentinin ötesinde, sisteme gerçek değer katacak düzeyde uygulanmıştır.

---

### Modüler Yapı ve Kod Kalitesi — 15 puan

**Beklenen kanıtlar:** İşlevsel modüllere ayrılmış proje dosyaları, anlamlı isimlendirme, uygun yorum satırları, fonksiyonlaştırılmış tekrar eden yapılar.

| Düzey        | Açıklama                                                                                                                                                    |
| ------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Yetersiz** | Kod tek dosyada ya da anlamsız parçalara bölünmüş; isimlendirmeler belirsiz; yorum hiç yok ya da her satırda gereksiz yorum var; yapı spagetti.             |
| **Yeterli**  | Modüller işlevlerine göre ayrılmış; fonksiyonlar tek bir iş yapıyor; yorumlar orantılı ve bilgilendirici; kod başkası tarafından takip edilebilir.          |
| **İyi**      | Modüller arası sorumluluk sınırları net; iş kuralları tek noktada toplanmış; hata yönetimi düşünülmüş; kod minimal değişiklikle genişletilebilir nitelikte. |

---

### Kullanıcı Yönetimi ve OOP — 20 puan

**Beklenen kanıtlar:** Birbirinden gerçek anlamda farklılaşmış kullanıcı sınıfları, temel sınıftan türetme, role göre menü ve işlem farklılaşması, çalışan giriş/kayıt ekranı.

| Düzey        | Açıklama                                                                                                                                                                                       |
| ------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Yetersiz** | Kullanıcı tipleri sınıf olarak tanımlanmış ama aralarındaki tek fark ad/soyad gibi veri alanları; yetkiler kodda gerçek anlamda ayrışmıyor; OOP yalnızca şeklen uygulanmış.                    |
| **Yeterli**  | Her kullanıcı tipinin kendine özgü işlemleri var; temel sınıf–alt sınıf ilişkisi anlamlı; giriş sonrası menü ve erişimler role göre farklılaşıyor; yetki kontrolü görünür biçimde uygulanıyor. |
| **İyi**      | Sınıf hiyerarşisi projenin iş mantığını doğal biçimde yansıtıyor; yetki ihlali denemeleri düzgün yönetiliyor; tasarım genişlemeye açık.                                                        |

---

### Veritabanı Kullanımı — 20 puan

**Beklenen kanıtlar:** Veritabanı bağlantı dosyası, birden fazla tablo, tablolar arası en az bir ilişki, projenin ihtiyaçlarını karşılayan sorgu çeşitliliği.

| Düzey        | Açıklama                                                                                                                                                           |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Yetersiz** | Veritabanı var ama tek tablo ve birkaç basit sütundan ibaret; yalnızca INSERT/SELECT kullanılmış; ilişki yok; veri yapısı projenin gerçek ihtiyacını karşılamıyor. |
| **Yeterli**  | Birden fazla tablo ve aralarında en az bir ilişki var; CRUD işlemleri uygulanmış; veritabanı yapısı projenin veri ihtiyacını karşılıyor.                           |
| **İyi**      | Tablo ve ilişki tasarımı projenin tüm iş akışını taşıyacak düzeyde; sorgular karmaşıklığa orantılı; veri bütünlüğü düşünülmüş.                                     |

---

### İşlem Kayıtları (Loglama) — 10 puan

**Beklenen kanıtlar:** Giriş, veri ekleme/silme/güncelleme, rapor alma gibi işlemlerin tarih/saat ve işlem tipiyle birlikte veritabanına yazılması; kayıtların sorgulanabilir olması.

| Düzey        | Açıklama                                                                                                                         |
| ------------ | -------------------------------------------------------------------------------------------------------------------------------- |
| **Yetersiz** | Log tablosu var ama yalnızca giriş kaydı tutuluyor ya da kayıtlar tarih/saat içermiyor; sorgulanamıyor.                          |
| **Yeterli**  | Temel işlemler tarih/saat ve kullanıcı bilgisiyle birlikte kaydediliyor; admin bu kayıtları görüntüleyebiliyor.                  |
| **İyi**      | Tüm kritik işlemler eksiksiz kaydediliyor; kayıtlar filtrelenebilir ya da özetlenebilir; işlevsel bir denetim izi oluşturuluyor. |

---

### Raporlama — 10 puan

**Beklenen kanıtlar:** Kullanıcıya özel işlem raporu, admin için sistem geneli rapor; raporların veritabanı kayıtlarına dayanması.

| Düzey        | Açıklama                                                                                                                                         |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Yetersiz** | Rapor ekranı var ama içerik sabit/sahte veri ya da yalnızca ham tablo çıktısı; kullanıcıya özgü filtreleme yok.                                  |
| **Yeterli**  | Kullanıcı kendi işlemlerini, admin tüm kullanıcıların işlemlerini görebiliyor; raporlar veritabanından çekiliyor ve anlaşılır biçimde sunuluyor. |
| **İyi**      | Raporlar tarih aralığı veya işlem tipi gibi parametrelerle filtrelenebiliyor ya da özetlenmiş istatistik sunuyor.                                |

---

### İleri Özellikler — 15 puan

**Beklenen kanıtlar:** Grup büyüklüğüne göre seçilen ileri özelliklerin projeye entegrasyonu ve README'de açıklanması.

| Düzey        | Açıklama                                                                                                     |
| ------------ | ------------------------------------------------------------------------------------------------------------ |
| **Yetersiz** | Özellik eklenmiş ama çalışmıyor, projeyle entegre değil ya da yalnızca import edilmiş; işlevsel katkısı yok. |
| **Yeterli**  | Seçilen özellikler çalışıyor ve projenin akışına entegre edilmiş; ne amaçla kullanıldığı anlaşılıyor.        |
| **İyi**      | Özellikler projeye gerçek değer katıyor; sistemin başka türlü karşılayamayacağı bir ihtiyacı çözüyor.        |

---

### Dokümantasyon — 10 puan

**Beklenen kanıtlar:** README ve docs/ klasöründeki zorunlu belgeler; kurulum/çalıştırma adımlarının eksiksizliği; demo kullanıcı bilgileri.

| Düzey        | Açıklama                                                                                                                          |
| ------------ | --------------------------------------------------------------------------------------------------------------------------------- |
| **Yetersiz** | Belgeler eksik ya da yalnızca başlıklardan ibaret; kurulum adımları belirsiz; proje başkası tarafından çalıştırılamıyor.          |
| **Yeterli**  | Tüm zorunlu belgeler mevcut ve anlaşılır; kurulum adımları izlenerek proje çalıştırılabiliyor; demo kullanıcılar tanımlanmış.     |
| **İyi**      | Belgeler projeyi hiç görmeyen birinin sistemi anlayıp çalıştırmasına yetecek düzeyde; örnek senaryolar somut ve takip edilebilir. |

---

## 9. Bonus Puan

Yönergenin zorunlu gerekliliklerini tam karşılayan projelerde, aşağıdaki niteliklerin görülmesi hâlinde **15 puana kadar** bonus verilebilir. Bonus, standart rubriğin ötesine geçen gerçek niteliği ödüllendirmek için kullanılır; eksik kriterleri telafi etmez.

Bonus değerlendirmesinde dikkate alınan nitelikler:

- Projenin gerçek kullanım senaryolarına yanıt verecek olgunlukta olması
- Sistem bileşenlerinin birbirine sıkı ve tutarlı biçimde entegre edilmesi
- Kullanıcı deneyiminin düşünülmüş olması (hata mesajları, akış yönetimi, uç durumlar)
- Teknik kararların gerekçelendirilebilir ve savunulabilir olması

---

## 10. Sunum ve Akademik Dürüstlük

Dersin son haftasında projenin canlı gösterimi yapılacaktır. Sunum ayrı bir puan kalemi değildir; projenin öğrenci tarafından üretilip üretilmediğini doğrulamak amacıyla yapılır.

**Her takım üyesi:**

- Kendi yazdığı kodun ne yaptığını ve neden o şekilde tasarladığını açıklayabilmelidir.
- Takım arkadaşlarının ürettiği bölümleri genel düzeyde anlatabilmelidir.

**Geçersizlik koşulu:** Sunumda projeyi büyük ölçüde yapay zekâ veya başka biri aracılığıyla ürettiği ve içeriğin farkında olmadığı anlaşılan öğrencinin teslimi **geçersiz sayılır ve sıfır** alır. Bu durum aynı zamanda akademik dürüstlük ihlali olarak değerlendirilir ve kurumsal etik süreçlerine taşınabilir.

Yapay zekâ araçlarının kullanımı serbesttir. Sınır, üretilen içeriğin anlaşılmadan kopyalanmasıdır. Kodu yazan araç değil, tasarım kararını veren ve savunan öğrencidir.

---

## 11. Son Uyarılar

- Tek dosyalı projeler kabul edilmeyecektir.
- Yalnızca arayüz yapıp sistem mantığını zayıf bırakan projeler düşük değerlendirilir.
- Veritabanı ve kullanıcı rolleri göstermelik olmamalıdır; değerlendirme bu bileşenlerin gerçek işlevine bakarak yapılır.
- README ve teknik belge eksikliği doğrudan puanı düşürür.
- Kurulum adımı belirsiz veya çalıştırılamayan teslimler ciddi eksik kabul edilir.
- Seçilen ileri özellik çalışmıyorsa ek katkı sayılmaz.

---

Sorularınızı ders saatlerinde veya e-posta yoluyla iletebilirsiniz. Başarılar.
