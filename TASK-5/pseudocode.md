BAŞLA

// --- Kullanıcı Ayarları ---
Yaz("Lütfen alarm ses seviyesini belirleyin (1–10): ")
SesSeviyesi ← KullanıcıGirişi()
Yaz("Lütfen alarm süresini saniye cinsinden girin (önerilen: 30 sn): ")
AlarmSüresi ← KullanıcıGirişi()

SistemDurumu ← AKTİF

// --- Ana Döngü (7/24 Çalışma) ---
WHILE SistemDurumu = AKTİF DO
    // Sensör Verilerini Oku
    Hareket ← HareketSensörüOku()
    Kapı ← KapıSensörüOku()
    Pencere ← PencereSensörüOku()
    Duman ← DumanSensörüOku()
    Gaz ← GazSensörüOku()

    // --- Tehdit Algılama ve İşlem ---
    IF Hareket = ALGILANDI THEN
        KameraAktifEt()
        AlarmÇal(SesSeviyesi, AlarmSüresi)
        BildirimGönder("Hareket algılandı! Evde izinsiz giriş olabilir.")
    
    ELSEIF Kapı = AÇILDI THEN
        KameraAktifEt()
        AlarmÇal(SesSeviyesi, AlarmSüresi)
        BildirimGönder("Kapı izinsiz açıldı!")

    ELSEIF Pencere = AÇILDI THEN
        KameraAktifEt()
        AlarmÇal(SesSeviyesi, AlarmSüresi)
        BildirimGönder("Pencere açıldı!")

    ELSEIF Duman = ALGILANDI THEN
        KameraAktifEt()
        AlarmÇal(SesSeviyesi, AlarmSüresi)
        BildirimGönder("Duman algılandı! Yangın riski var!")

    ELSEIF Gaz = ALGILANDI THEN
        KameraAktifEt()
        AlarmÇal(SesSeviyesi, AlarmSüresi)
        BildirimGönder("Gaz kaçağı tespit edildi! Lütfen hemen kontrol edin!")

    ELSE
        Yaz("Her şey normal. Sistem izleme modunda...")
    ENDIF

    // --- Sistem Döngü Süresi ---
    BEKLE(5 saniye)

ENDWHILE

BİTİR
