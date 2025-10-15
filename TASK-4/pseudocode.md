BAŞLA

  // --- Öğrenci Girişi ---
  Tekrarla
      Yaz "Öğrenci numaranızı giriniz:"
      Oku ogr_no
      Yaz "Şifrenizi giriniz:"
      Oku sifre

      Eğer (ogr_no ve sifre doğruysa) ise
          Yaz "Giriş başarılı."
          Çık
      Aksi halde
          Yaz "Hatalı giriş! Lütfen tekrar deneyiniz."
      Son
  Doğru giriş yapılana kadar
  Son Tekrarla

  // --- Ders Listesini Görüntüleme ---
  Yaz "Mevcut dersler:"
  Her ders için ders_listesi içinde
      Yaz ders_adi, kredi, kontenjan, önkoşul, zaman
  Son

  toplam_kredi ← 0
  secilen_dersler ← ∅

  // --- Ders Seçimi ve Kontroller ---
  Tekrarla
      Yaz "Bir ders seçiniz (bitirmek için 0 giriniz):"
      Oku ders

      Eğer ders = 0 ise Çık
      Son

      Eğer ders.kontenjan = 0 ise
          Yaz "Kontenjan dolu. Başka ders seçiniz."
          Devam et
      Son

      Eğer ders.onkosul var ve alınmamış ise
          Yaz "Önkoşul dersi tamamlanmamış."
          Devam et
      Son

      Eğer ders.zaman çakışıyor(secilen_dersler) ise
          Yaz "Zaman çakışması mevcut."
          Devam et
      Son

      Eğer toplam_kredi + ders.kredi > 35 ise
          Yaz "Kredi limiti aşıldı."
          Devam et
      Son

      secilen_dersler’e ders ekle
      toplam_kredi ← toplam_kredi + ders.kredi
      Yaz "Ders başarıyla eklendi."

  Ders seçimi bitene kadar
  Son Tekrarla

  // --- Danışman Onayı ---
  Eğer ogrenci.GPA < 2.5 ise
      Yaz "Danışman onayı gereklidir."
  Son

  // --- Kayıt Özeti ---
  Yaz "Seçilen dersler ve toplam kredi gösteriliyor..."
  Yaz "Kaydı onaylıyor musunuz? (E/H)"
  Oku cevap

  Eğer cevap = 'E' ise
      Yaz "Kayıt başarıyla tamamlandı."
  Aksi halde
      Yaz "Kayıt iptal edildi."
  Son

BİTİR
