BASLA

  // --- Başlangıç değişkenleri ---
  pinHak <- 0
  MAX_PIN_HAK <- 3
  pinDogru <- YANLIS
  hesapBakiyesi <- 2500
  gunlukLimit <- 1000
  gunlukKullanilan <- 0

  // --- PIN DOĞRULAMA ---
  DONGU (pinDogru = YANLIS VE pinHak < MAX_PIN_HAK)
      YAZ "Lütfen PIN kodunuzu giriniz:"
      OKU girilenPIN

      EGER-ISE girilenPIN = hesapPIN
          pinDogru <- DOGRU
      DEĞİLSE
          pinHak <- pinHak + 1
          EGER-ISE pinHak >= MAX_PIN_HAK
              YAZ "Kart bloke edildi."
              YAZ "Kart yutuldu."
              YAZ "Kartı geri almak için şubeye gidiniz."
              BITIR
          EGER-ISE SONU
      EGER-ISE SONU
  DONGU SONU


  // --- ANA İŞLEM DÖNGÜSÜ ---
  islemDevam <- DOGRU

  DONGU (islemDevam = DOGRU)

      YAZ "Bakiye: " + hesapBakiyesi + " TL"
      YAZ "Günlük kalan limit: " + (gunlukLimit - gunlukKullanilan) + " TL"

      YAZ "Çekmek istediğiniz tutarı giriniz:"
      OKU tutar

      // --- TUTAR KONTROLÜ ---
      EGER-ISE (tutar MOD 20) <> 0
          YAZ "Tutar 20 TL katları olmalıdır."
          DEVAM ET  // tekrar başa dön
      EGER-ISE SONU

      // --- GÜNLÜK LİMİT KONTROLÜ ---
      EGER-ISE (tutar > (gunlukLimit - gunlukKullanilan))
          YAZ "Günlük limit aşılıyor."
          DEVAM ET
      EGER-ISE SONU

      // --- BAKİYE KONTROLÜ ---
      EGER-ISE (tutar > hesapBakiyesi)
          YAZ "Yetersiz bakiye."
          DEVAM ET
      EGER-ISE SONU

      // --- ONAY ADIMI ---
      YAZ "İşlemi onaylıyor musunuz? (E/H)"
      OKU onay

      EGER-ISE (onay = "E" VEYA onay = "e")
          hesapBakiyesi <- hesapBakiyesi - tutar
          gunlukKullanilan <- gunlukKullanilan + tutar
          YAZ "Lütfen paranızı alınız."
          YAZ "Yeni bakiye: " + hesapBakiyesi + " TL"
      DEĞİLSE
          YAZ "İşlem iptal edildi."
      EGER-ISE SONU

      // --- TEKRAR İŞLEM SEÇENEĞİ ---
      YAZ "Başka işlem yapmak istiyor musunuz? (E/H)"
      OKU cevap

      EGER-ISE (cevap = "E" VEYA cevap = "e")
          islemDevam <- DOGRU
      DEĞİLSE
          islemDevam <- YANLIS
      EGER-ISE SONU

  DONGU SONU

YAZ "Kartınızı alınız. İyi günler."
BITIR
