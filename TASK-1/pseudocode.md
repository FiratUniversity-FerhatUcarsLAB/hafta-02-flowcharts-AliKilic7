BASLA

  // Başlangıç değişkenleri (gerçekte veritabanından/hesaptan alınır)
  hesapPIN <- "1234"                // örnek; gerçek sistemde güvenli saklanır
  hesapBakiyesi <- 2500             // örnek bakiye (TL)
  gunlukLimit <- 1000               // hesap için günlük çekim limiti (TL)
  gunlukKullanilan <- 0             // o gün çekilen toplam tutar
  MAX_PIN_HAK <- 3

  // PIN doğrulama
  pinHak <- 0
  pinDogru <- YANLIS

  DONGU (pinHak < MAX_PIN_HAK VE pinDogru = YANLIS)
    YAZ "Lütfen PIN kodunuzu giriniz:"
    OKU girilenPIN
    pinHak <- pinHak + 1

    EGER-ISE girilenPIN = hesapPIN
      pinDogru <- DOGRU
      YAZ "PIN doğrulandı."
    DEĞİLSE
      kalanHak <- MAX_PIN_HAK - pinHak
      EGER-ISE kalanHak > 0
        YAZ "Yanlış PIN. Kalan hak: " + kalanHak
      DEĞİLSE
        YAZ "3 başarısız denemeden sonra kart bloke edildi. İşlem sonlandırılıyor."
        YAZ "Kart iade ediliyor."
        BITIR
      EGER-ISE SONU
    EGER-ISE SONU

  DONGU SONU

  // Ana işlem döngüsü - işlem tekrarı seçeneği
  islemDevam <- DOGRU

  DONGU (islemDevam = DOGRU)
    YAZ "Mevcut bakiye: " + hesapBakiyesi + " TL"
    YAZ "Günlük kalan limit: " + (gunlukLimit - gunlukKullanilan) + " TL"

    YAZ "Çekmek istediğiniz tutarı giriniz (20 TL katları):"
    OKU tutar

    // Tutar geçerlilik kontrolü
    EGER-ISE tutar <= 0
      YAZ "Geçersiz tutar. Lütfen pozitif bir tutar giriniz."
      DONGU (devam)   // yeniden sor
    EGER-ISE SONU

    EGER-ISE (tutar MOD 20) <> 0
      YAZ "Tutar 20 TL katları halinde olmalıdır. Lütfen 20, 40, 60 ... gibi bir tutar giriniz."
      DONGU (devam)   // yeniden sor
    EGER-ISE SONU

    // Günlük limit kontrolü
    EGER-ISE tutar > (gunlukLimit - gunlukKullanilan)
      YAZ "İşlem reddedildi: Günlük limit aşılıyor."
      YAZ "Günlük kalan limit: " + (gunlukLimit - gunlukKullanilan) + " TL"
      DONGU (devam)
    EGER-ISE SONU

    // Bakiye kontrolü
    EGER-ISE tutar > hesapBakiyesi
      YAZ "İşlem reddedildi: Hesabınızda yeterli bakiye yok."
      DONGU (devam)
    EGER-ISE SONU

    // Onay adımı
    YAZ tutar + " TL çekmek istediğinize emin misiniz? (E/H)"
    OKU onay
    EGER-ISE onay = "E" VEYA onay = "e"
      // Para verme ve bakiye güncelleme
      hesapBakiyesi <- hesapBakiyesi - tutar
      gunlukKullanilan <- gunlukKullanilan + tutar
      YAZ "Lütfen paranızı alınız: " + tutar + " TL"
      YAZ "İşlem başarılı. Yeni bakiye: " + hesapBakiyesi + " TL"
    DEĞİLSE
      YAZ "İşlem iptal edildi."
    EGER-ISE SONU

    // İşlem tekrarı seçeneği
    YAZ "Başka işlem yapmak istiyor musunuz? (E/H)"
    OKU cevap
    EGER-ISE cevap = "E" VEYA cevap = "e"
      islemDevam <- DOGRU
    DEĞİLSE
      islemDevam <- YANLIS
      YAZ "Kartınızı alınız. İyi günler."
    EGER-ISE SONU

  DONGU SONU

BITIR
