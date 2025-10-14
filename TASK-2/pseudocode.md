1.  BAŞLA
2.      YAZ "Kullanıcı girişi yapınız."
3.      kullanici ← GİRİŞ_YAP()
4.      
5.      EĞER kullanici = GEÇERSİZ İSE
6.          YAZ "Siteye kayıt olmadan giremezsiniz."
7.          KAYIT_OL()
8.          GİRİŞ_YAP()
9.      SON
10.     
11.     sepet ← BOS_SEPET_OLUSTUR()
12.     
13.     TEKRARLA
14.         urun ← URUN_SEC()
15.         adet ← GİRİS("Adet giriniz: ")
16.         
17.         EĞER STOK_YETERLI_MI(urun, adet) = EVET İSE
18.             SEPETE_EKLE(sepet, urun, adet)
19.             YAZ "Ürün sepete eklendi."
20.         DEĞİLSE
21.             YAZ "Stok yetersiz!"
22.         SON
23.         
24.         devam ← GİRİS("Başka ürün eklemek ister misiniz? (E/H): ")
25.     MÜDDETİNCE devam = "E"
26.     
27.     kod ← GİRİS("İndirim kodu giriniz: ")
28.     EĞER INDIRIM_KODU_GECERLI_MI(kod) = EVET İSE
29.         indirim_miktari ← INDIRIM_DEGERI_AL(kod)
30.         YAZ "İndirim uygulandı."
31.     DEĞİLSE
32.         indirim_miktari ← 0
33.         YAZ "Geçersiz indirim kodu."
34.     SON
35.     
36.     kargo_ucreti ← KARGO_HESAPLA(sepet)
37.     genel_toplam ← sepet.toplam_tutar - indirim_miktari + kargo_ucreti
38.     
39.     YAZ "Toplam tutar: ", genel_toplam
40.     
41.     odeme_durumu ← ODEME_ISLEMI(genel_toplam)
42.     EĞER odeme_durumu = BASARILI İSE
43.         SIPARIS_OLUSTUR(kullanici, sepet, genel_toplam)
44.         STOK_GUNCELLE(sepet)
45.         YAZ "Ödeme başarılı! Siparişiniz oluşturuldu."
46.     DEĞİLSE
47.         YAZ "Ödeme başarısız! Lütfen tekrar deneyiniz."
48.     SON
49.     
50. BİTİR
