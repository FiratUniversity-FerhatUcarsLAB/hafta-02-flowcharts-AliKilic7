BAŞLA
    deneme_sayısı ← 0

    TEKRAR:
        Kullanıcı kimlik ve şifreyi girer
        Eğer kimlik ve şifre doğruysa
            GİRİŞ BAŞARILI
            Menü göster:
                1 - Randevu Alma
                2 - Tahlil Sonucu Görüntüleme
            Kullanıcıdan seçim al

            Eğer seçim = 1 ise
                Poliklinik seç
                Doktor seç
                Uygun saatleri görüntüle
                Randevuyu onayla
                SMS gönder
                BİTİR

            Değilse eğer seçim = 2 ise
                Tahlil var mı kontrol et
                Eğer tahlil varsa
                    Sonuç hazır mı kontrol et
                    Eğer sonuç hazırsa
                        Sonucu görüntüle
                        İsterse PDF indir
                    Değilse
                        "Sonuç henüz hazır değil" mesajı göster
                Değilse
                    "Tahlil bulunamadı" mesajı göster
                BİTİR

        DEĞİLSE
            deneme_sayısı ← deneme_sayısı + 1
            Eğer deneme_sayısı < 3 ise
                "Hatalı şifre, tekrar deneyiniz." mesajı göster
                Git TEKRAR
            Değilse
                "Şifrenizi birçok kez hatalı girdiniz.\n3 dk sonra tekrar deneyiniz." mesajı göster
                BİTİR
