# 🌞 Arduino #7: LDR (Işık Sensörü) ile Otomatik LED Kontrolü

Bu projede, **LDR (Light Dependent Resistor)** kullanarak Arduino ile **ortamdaki ışık seviyesine göre LED kontrolü** yapmayı öğreneceğiz.

🔗 [Web Siteme Bakmak İçin Tıkla](https://www.hakkiharmankaya.com/)  
🔗 [Tinkercad Tasarımına Göz At](https://www.tinkercad.com/things/kXKRuSaoZ4q?sharecode=wCPpF2oQTquVStYDxKhsbseKr0tu-GPcuZfmqzw0JUI)

---

## 🧰 Gerekli Malzemeler

- 1 adet **LDR (ışık sensörü)**
- 1 adet **10KΩ direnç**
- 1 adet **220Ω veya 330Ω direnç**
- 1 adet **LED**
- 1 adet **Arduino**
- 1 adet **breadboard**
- 4 adet **jumper kablo**

---

## ⚙️ Adım Adım Devre Kurulumu

### 🔹 Adım 1: Devreyi Kurun

- **LDR**'nin bir ucu → **5V**, diğer ucu → **GND**
- **10KΩ direnç**, LDR'nin bir ucu ile **A0 analog pinine** bağlanacak şekilde yerleştirilir.
- **LED**'in:
  - **Anot (uzun bacak)** → Arduino **D3 pinine**
  - **Katot (kısa bacak)** → **direnç** → **GND**

---

## 🔹 Adım 2: Arduino Kodunu Yazın ve Yükleyin

```cpp
void setup() {
  pinMode(3, OUTPUT);        // LED çıkış pini
  Serial.begin(9600);        // Seri haberleşme başlat
}

void loop() {
  int isik = analogRead(A0); // LDR'den gelen ışık değeri
  Serial.println(isik);      // Seri monitöre yazdır

  if (isik < 400) {
    digitalWrite(3, HIGH);   // Ortam karanlıksa LED yanar
  } else {
    digitalWrite(3, LOW);    // Ortam aydınlıksa LED söner
  }
}
