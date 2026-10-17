# 🚪 Garage Gate Automation System with PLC & HMI

Siemens TIA Portal ortamında PLC (Ladder Diagram) ve SIMATIC HMI panel kullanılarak geliştirilmiş, Otomatik ve Manuel çalışma modlarına sahip endüstriyel garaj kapısı otomasyon sistemi projesidir.

---

## 📌 Proje Özeti
Bu proje, bir garaj kapısının endüstriyel standartlara uygun şekilde kontrol edilmesini sağlar. Sistem; kullanıcı müdahalesine olanak tanıyan **Manuel Mod** ile sensör ve zamanlayıcı tabanlı çalışan **Otomatik Mod** olmak üzere iki temel işletim moduna sahiptir.

### 🎥 HMI & Sistem Simülasyonu (PLC-Sim)

<img width="800" alt="HMI Simulation - Gate Opening" src="https://github.com/user-attachments/assets/80518448-ac4f-4cc4-8c53-cc9fef87f70a" />

<img width="800" alt="HMI Simulation - Gate Closing" src="https://github.com/user-attachments/assets/db85664f-da51-47db-b5b0-a23dc6262c9b" />

---

## ⚙️ Özellikler ve Çalışma Mantığı

* **Çift Çalışma Modu (Otomatik / Manuel):**
  * **Manuel Mod:** HMI paneli üzerindeki *"İleri"* ve *"Geri"* butonları ile kapı hareketi manuel olarak yönlendirilir. Sınır anahtarları (limit switch) ile güvenli duruş sağlanır.
  * **Otomatik Mod:** İç ve dış sensörler tetiklendiğinde kapı otomatik açılır, belirlenen süre boyunca açık bekler ve süre sonunda emniyetli bir şekilde kapanır.
* **Dinamik Konum Takibi:** Kapının anlık hareketini ve konumunu HMI üzerinde simüle etmek amacıyla yükselen kenar palsı ve toplama/çıkarma (`ADD`/`SUB`) mantığı kullanılmıştır.
* **Modüler Mimari:** Kod tekrarını önlemek, okunabilirliği artırmak ve bakımı kolaylaştırmak için özel Fonksiyon Blokları (`FB`) ve Veri Blokları (`DB`) oluşturulmuştur.

---

## 🛠️ PLC Mimari ve Kod Yapısı

### 1. Ana Kontrol Blokları (Main OB1)

**Network 1: Çalışma Modu Seçimi (OTO / MANUEL)**
![Main Network 1](https://github.com/user-attachments/assets/a2f31a54-6389-48bc-9eea-2fb92c56e70e)

**Network 2: Manuel Yön Kontrolü ve Güvenlik Sınırları**
<img width="739" alt="Main Network 2" src="https://github.com/user-attachments/assets/8d7cabf0-1af8-4382-8003-9c4472178c7c" />

**Network 3: Otomatik Mod Sensör ve Zamanlayıcı Mantığı**
![Main Network 3](https://github.com/user-attachments/assets/c066d199-3487-44c9-a8a0-c1b55202b37e)

**Network 4: Fonksiyon Bloğu (FB2) Çağrısı ve Çıkış Atamaları**
![Main Network 4](https://github.com/user-attachments/assets/bb21feed-97d1-44eb-a4a0-0dd2609940e5)

---

### 2. Modüler Fonksiyon Blokları (FB)

**FB1: Zamanlayıcı ve Tetikleme Blok Yapısı**
![FB1 Details](https://github.com/user-attachments/assets/ee95b74e-a7a6-40eb-b496-64d5245c5f77)

**FB2: Konum Hesabı ve Durum Yönetimi (ADD / SUB Algoritması)**
![FB2 Network 1](https://github.com/user-attachments/assets/7a1ef93d-589e-43cd-8dc7-6471b5068c76)

![FB2 Network 2](https://github.com/user-attachments/assets/10d85f98-a177-498e-bbe1-939dfc7f12b9)

---

## 🛠️ Kullanılan Teknolojiler

* **Yazılım:** Siemens TIA Portal
* **Programlama Dili:** Ladder Diagram (LAD)
* **Arayüz (HMI):** SIMATIC HMI Touch Panel Simulation
* **Simülasyon:** S7-PLCSIM
