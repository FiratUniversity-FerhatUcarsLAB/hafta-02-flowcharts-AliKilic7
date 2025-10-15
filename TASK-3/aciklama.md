İsim - Soy İsim Selahattin Ali Kılıç
Öğrenci NO: 250541036
sistemin kısa açıklaması (maks. 5-6 satır)
Harika 👍 işte bu güncel sisteme uygun, rapor veya ödevde kullanılabilecek **resmî açıklama metni**:

---

**Hastane İşlem Sistemi Açıklaması:**
Bu çalışmada, kullanıcı kimlik doğrulaması sonrası iki ana fonksiyon içeren bir hastane işlem sistemi modellenmiştir.
Sistem, kullanıcıdan kimlik ve şifre bilgilerini alır; hatalı giriş durumunda deneme sayısını takip eder. Üç kez hatalı 
giriş yapılması durumunda, kullanıcıya “Şifrenizi birçok kez hatalı girdiniz. 3 dakika sonra tekrar deneyiniz.” uyarısı
gösterilir ve giriş işlemi sonlandırılır.

Başarılı kimlik doğrulamasından sonra kullanıcıya iki seçenek sunulur: **Randevu Alma** ve **Tahlil Sonucu Görüntüleme**.
Randevu akışında kullanıcı sırasıyla poliklinik, doktor ve uygun saat seçimini gerçekleştirir; ardından randevuyu onaylayarak
SMS bilgilendirmesi alır. Tahlil sürecinde ise sistem önce tahlil kaydının varlığını, ardından sonucun hazır olup olmadığını 
kontrol eder. Sonuç hazırsa kullanıcıya görüntüleme ve PDF indirme seçenekleri sunulur; aksi durumda bilgilendirici bir mesaj gösterilir.

Her iki işlem akışı da kullanıcı etkileşiminin tamamlanmasıyla **BİTİR** düğümünde sonlanmaktadır.
