# ✈️ Hava Yolları Yönetim Sistemi

## 👨‍🎓 Projeyi Yapan Öğrenciler
- **Hasan Yılmaz Gürsoy 215260008**
- **Muhammet Eray Yıldırım 225260080**
- **Ahmet Taha Ural 225260014**

---

## 📌 1. Proje Gereksinimleri

**Hava Yolları Yönetim Sistemi** uçuş, yolcu, rezervasyon ve ödeme işlemlerini yönetmek amacıyla geliştirilmiş bir veritabanı projesidir. Sistemin temel gereksinimleri aşağıda listelenmiştir.

### 1.1. 🧑‍💻 Kullanıcı Türleri

- ### 🧳 **Müşteri Kullanıcılar:**
  - Uçuş arama ve görüntüleme.
  - Uçuş rezervasyonu yapma.
  - Rezervasyon bilgilerini görüntüleme.
  - Ödeme işlemlerini gerçekleştirme.
  - Geri bildirim gönderme.
  - Mil puanı kazanma ve kullanma.
  - Check-in işlemi yapma.

- ### 👔 **Yönetici Kullanıcılar:**
  - Uçuş bilgilerini ekleme, düzenleme ve silme.
  - Havaalanı bilgilerini güncelleme.
  - Uçak bilgilerini yönetme.
  - Kullanıcı geri bildirimlerini görüntüleme.
  - Rezervasyon ve ödeme bilgilerini yönetme.

---

## 📊 2. Varlıklar ve Nitelikler

### 2.1. 📁 Varlıklar

1. **Kullanıcılar (TbKullanicilar)**
   - **Nitelikler:** `KullaniciID`, `KullaniciAdi`, `Email`, `Sifre`, `Rol` (Müşteri/Yönetici)
   - **Kısıtlamalar:** `KullaniciAdi` ve `Email` benzersiz olmalıdır.

2. **Havaalanları (TbHavaalanlari)**
   - **Nitelikler:** `HavaalaniNo`, `HavaalaniAdi`, `Sehir`
   - **Kısıtlamalar:** `HavaalaniNo` benzersiz olmalıdır.

3. **Uçaklar (TbUcaklar)**
   - **Nitelikler:** `UcakID`, `UcakModeli`, `KoltukSayisi`
   - **Kısıtlamalar:** `UcakID` benzersiz olmalıdır.

4. **Uçuşlar (TbUcuslar)**
   - **Nitelikler:** `UcusKod`, `KalkisHavaalani`, `VarisHavaalani`, `UcakID`, `UcusTarihi`
   - **Kısıtlamalar:** `UcusKod` benzersiz olmalıdır.

5. **Yolcular (TbYolcular)**
   - **Nitelikler:** `YolcuID`, `YolcuAdi`, `YolcuSoyadi`, `TCNo`
   - **Kısıtlamalar:** `TCNo` benzersiz olmalıdır.

6. **Rezervasyonlar (TbRezervasyon)**
   - **Nitelikler:** `RezervasyonNo`, `UcusID`, `YolcuID`, `KullaniciID`, `RezervasyonTarihi`
   - **Kısıtlamalar:** `RezervasyonNo` benzersiz olmalıdır.

7. **Bagaj (TbBagaj)**
   - **Nitelikler:** `BagajID`, `RezervasyonID`, `BagajTipi`
   - **Kısıtlamalar:** `BagajID` benzersiz olmalıdır.

8. **Geri Bildirim (TbGeriBildirim)**
   - **Nitelikler:** `GeriBildirimID`, `KullaniciID`, `UcusKod`, `Mesaj`
   - **Kısıtlamalar:** `GeriBildirimID` benzersiz olmalıdır.

9. **Check-in Bilgileri (TbCheckInBilgileri)**
   - **Nitelikler:** `CheckInID`, `RezervasyonID`, `CheckInTarihi`
   - **Kısıtlamalar:** `CheckInID` benzersiz olmalıdır.

10. **Ödeme (TbOdeme)**
    - **Nitelikler:** `OdemeID`, `RezervasyonID`, `OdemeTarihi`, `OdemeTutari`
    - **Kısıtlamalar:** `OdemeID` benzersiz olmalıdır.

11. **Mil Puanları (TbMilPuanlari)**
    - **Nitelikler:** `MilPuanID`, `KullaniciID`, `ToplamMil`, `KazanmaTarihi`, `KullanmaTarihi`
    - **Kısıtlamalar:** `MilPuanID` benzersiz olmalıdır.

---

## 🔗 3. İlişkiler ve Sayısal Kısıtlamalar

1. **Kullanıcılar ile Rezervasyonlar**
   - **İlişki Türü:** 1'e M (One to Many)
   - **Açıklama:** Bir kullanıcı birden fazla rezervasyon yapabilir, ancak her rezervasyon yalnızca bir kullanıcıya aittir.

2. **Uçuşlar ile Rezervasyonlar**
   - **İlişki Türü:** 1'e M (One to Many)
   - **Açıklama:** Bir uçuş, birden fazla rezervasyona sahip olabilir, ancak her rezervasyon bir uçuşa aittir.

3. **Yolcular ile Rezervasyonlar**
   - **İlişki Türü:** 1'e M (One to Many)
   - **Açıklama:** Bir yolcu birden fazla rezervasyon yapabilir, ancak her rezervasyon yalnızca bir yolcuya aittir.

4. **Rezervasyonlar ile Bagaj**
   - **İlişki Türü:** 1'e M (One to Many)
   - **Açıklama:** Bir rezervasyon birden fazla bagaj kaydına sahip olabilir, ancak her bagaj yalnızca bir rezervasyona aittir.

5. **Kullanıcılar ile Geri Bildirim**
   - **İlişki Türü:** 1'e M (One to Many)
   - **Açıklama:** Bir kullanıcı birden fazla geri bildirim gönderebilir, ancak her geri bildirim yalnızca bir kullanıcıya aittir.

6. **Rezervasyonlar ile Check-in Bilgileri**
   - **İlişki Türü:** 1'e 1 (One to One)
   - **Açıklama:** Her rezervasyon için yalnızca bir check-in kaydı vardır.

7. **Rezervasyonlar ile Ödeme**
   - **İlişki Türü:** 1'e 1 (One to One)
   - **Açıklama:** Her rezervasyon için yalnızca bir ödeme kaydı vardır.

8. **Yolcular ile Mil Puanları**
   - **İlişki Türü:** 1'e 1 (One to One)
   - **Açıklama:** Her yolcu yalnızca bir mil puanı kaydına sahip olabilir.

9. **Uçaklar ile Uçuşlar**
   - **İlişki Türü:** 1'e M (One to Many)
   - **Açıklama:** Bir uçağın birden fazla uçuşu olabilir, ancak her uçuş yalnızca bir uçağa aittir.

10. **Uçuşlar ile Geri Bildirim**
    - **İlişki Türü:** 1'e M (One to Many)
    - **Açıklama:** Bir uçuş birden fazla geri bildirim alabilir, ancak her geri bildirim yalnızca bir uçuşa aittir.

11. **Havaalanları ile Uçuşlar**
    - **İlişki Türü:** 1'e M (One to Many)
    - **Açıklama:** Bir havaalanından birçok uçuş kalkış yapabilir veya varış yapabilir. Her uçuş ise belirli bir kalkış ve varış havaalanına sahiptir.



## 📝 4. Sonuç

Bu gereksinimler ve ilişkiler, Hava Yolları Yönetim Sistemi'nin veritabanı yapısının tasarımında dikkate alınması gereken unsurları kapsamlı bir şekilde ele almaktadır. Her kullanıcı türü için belirlenen özellikler, sistemin kullanılabilirliğini ve yönetimini artıracak şekilde tasarlanmıştır. Bu proje, kullanıcıların ihtiyaçlarına yanıt vermek ve işlemleri etkili bir şekilde yönetmek için gerekli tüm bileşenleri içermektedir.

---
## 📐 5. ER Diyagramı

![er_1730810988443](https://github.com/user-attachments/assets/bfa7a5a9-9cbd-4bff-bbb0-858715ca7f38)


6.Foreign Key ve Referansları
![WhatsApp Görsel 2024-11-06 saat 10 22 12_dbc1275d](https://github.com/user-attachments/assets/3467173e-b246-432f-8603-12f84d102f57)





