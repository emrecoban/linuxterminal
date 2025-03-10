**Linux Sistem Yönetimi Genişletilmiş Pratik Çalışması**  
**Amaç:** Öğrencilerin temel ve orta seviye Linux komutlarını, sistem yönetimi becerilerini ve problem çözme yeteneklerini geliştirmeleri.  

---
 
#### **Hazırlık**  
1. Terminali açın ve kök erişimi olan bir kullanıcıyla çalışın (gerekirse `sudo` kullanın).  
2. Aşağıdaki komutları gözden geçirin:  
   - Temel komutlar: `ls`, `cd`, `mkdir`, `touch`, `cp`, `mv`, `rm`, `find`, `grep`  
   - Kullanıcı/grup yönetimi: `adduser`, `deluser`, `passwd`, `groupadd`, `gpasswd`, `usermod`  
   - Dosya izinleri: `chmod`, `chown`, `chgrp`  
   - İleri komutlar: `cron`, `tar`, `systemctl`, `top`, `ping`, `curl`  

---

### **Görev Listesi**  
#### **1. Temel Dizin ve Dosya İşlemleri**  
- **Görev 1:** Aşağıdaki dizin yapısını oluşturun:  
  ```bash
  /home/öğrenci/calisma  
  ├── proje1  
  │   ├── rapor.txt  
  │   └── veri.csv  
  └── proje2  
      └── loglar  
  ```  
  *Komutlar:* `mkdir -p`, `touch`, `echo "içerik" > dosya`  
- **Görev 2:** `proje1/rapor.txt` dosyasını `proje2/loglar` dizinine kopyalayın ve adını `rapor_backup.txt` olarak değiştirin.  
  *Komut:* `cp`, `mv`  
- **Görev 3:** `proje1/veri.csv` dosyasını silin.  
  *Komut:* `rm`  

---

#### **2. Kullanıcı ve Grup Yönetimi**  
- **Görev 4:** `developer` adında bir kullanıcı oluşturun ve parolasını ayarlayın.  
  *Komut:* `sudo adduser developer`, `sudo passwd developer`  
- **Görev 5:** `dev_team` adında bir grup oluşturun ve `developer` kullanıcısını bu gruba ekleyin.  
  *Komut:* `sudo groupadd dev_team`, `sudo gpasswd -a developer dev_team`  
- **Görev 6:** `developer` kullanıcısını geçici olarak devre dışı bırakıp tekrar aktifleştirin.  
  *Komut:* `sudo usermod -L developer`, `sudo usermod -U developer`  

---

#### **3. Dosya İzinleri ve Güvenlik**  
- **Görev 7:** `rapor.txt` dosyasını yalnızca sahibinin okuyup yazabileceği şekilde ayarlayın.  
  *Komut:* `chmod 600 rapor.txt`  
- **Görev 8:** `loglar` dizinini, sahibi ve grubunun tüm izinlere sahip olduğu, diğerlerinin erişemediği şekilde yapılandırın.  
  *Komut:* `chmod 770 loglar`  

---

#### **4. Arama ve Filtreleme**  
- **Görev 9:** `/home` dizininde son 24 saat içinde değiştirilen dosyaları bulun.  
  *Komut:* `sudo find /home -mtime -1`  
- **Görev 10:** `rapor.txt` dosyasında "acil" kelimesini aratın.  
  *Komut:* `grep "acil" rapor.txt`  

---

#### **5. Bağlantılar ve İleri Dosya İşlemleri**  
- **Görev 11:** `rapor.txt` için bir **hard link** ve bir **symbolic link** oluşturun. Orijinal dosyayı silerek farkı gözlemleyin.  
  *Komut:* `ln rapor.txt hard_link`, `ln -s rapor.txt sym_link`  

---

#### **6. Ortam Değişkenleri**  
- **Görev 12:** `PATH` değişkenine `/home/öğrenci/bin` dizinini ekleyin ve kalıcı hale getirin.  
  *Komut:* `echo 'export PATH=$PATH:/home/öğrenci/bin' >> ~/.bashrc`, `source ~/.bashrc`  

---

#### **7. Kabuk Programlama (BASH)**  
- **Görev 13:** Aşağıdaki BASH script'ini oluşturup çalıştırın:  
  ```bash
  #!/bin/bash
  echo "Bugünün tarihi: $(date)"
  echo "Mevcut kullanıcı: $(whoami)"
  ```  
  *Adımlar:*  
  1. `touch script.sh`  
  2. İçeriği yazın.  
  3. Çalıştırma izni verin: `chmod +x script.sh`  
  4. Çalıştırın: `./script.sh`  

---

#### **8. Süreç Yönetimi**  
- **Görev 14:** Çalışan tüm süreçleri listeleyin ve `nginx` servisini başlatın/durdurun.  
  *Komut:* `ps aux`, `sudo systemctl start nginx`, `sudo systemctl stop nginx`  
- **Görev 15:** Sistem kaynak kullanımını gerçek zamanlı izleyin.  
  *Komut:* `top` veya `htop`  

---

#### **9. Paket Yönetimi**  
- **Görev 16:** `htop` paketini kurun ve çalıştırın.  
  *Komut:* `sudo apt install htop`, `htop`  
- **Görev 17:** Kurulu paketler arasında "python" kelimesini arayın.  
  *Komut:* `apt list --installed | grep python`  

---

#### **10. Ağ Yapılandırması**  
- **Görev 18:** IP adresinizi görüntüleyin ve Google sunucularına ping atın.  
  *Komut:* `ip a`, `ping 8.8.8.8`  
- **Görev 19:** Bir web sayfasını terminalde görüntüleyin.  
  *Komut:* `curl https://example.com`  

---

#### **11. Log Analizi**  
- **Görev 20:** Sistem log'larında "error" kelimesini içeren satırları filtreleyin.  
  *Komut:* `sudo grep -i "error" /var/log/syslog`  

---

### **Zaman Kısıtı**  
- Toplam süre: **90 dakika**  
- Her görev için önerilen süre: **5-10 dakika**  

---

### **Sonuç Raporlama**  
1. Her görevin terminal çıktılarını ekran görüntüsü olarak kaydedin.  
2. Kullandığınız komutları ve amaçlarını açıklayan bir rapor yazın (örneğin: "`chmod 600` ile dosya izinleri kısıtlandı").  

---

### **Değerlendirme Kriterleri**  
- **Doğruluk:** Komutların doğru kullanımı ve beklenen çıktılar.  
- **Hız:** Görevlerin zamanında tamamlanması.  
- **Hata Yönetimi:** Karşılaşılan sorunların nasıl çözüldüğü.  

**Not:** Sanal makine veya Docker container kullanarak güvenli bir ortamda çalışabilirsiniz.
