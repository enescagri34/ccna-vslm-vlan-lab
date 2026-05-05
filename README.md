# 🧠 CCNA VLSM, VLAN ve Routing Lab

## 📌 Proje Özeti

Bu projede, tek bir IP bloğu (`192.168.1.0/24`) kullanılarak **VLSM (Variable Length Subnet Mask)** yöntemiyle farklı büyüklükte alt ağlar oluşturulmuş ve bu ağlar VLAN’lara dağıtılmıştır.

Amaç, gerçek bir ağ senaryosuna benzer şekilde:

* IP adreslerini verimli kullanmak
* Ağı mantıksal olarak segmentlere ayırmak
* VLAN’lar arası iletişimi sağlamak
* Router’lar arasında yönlendirme yapmak

ve tüm yapıyı uçtan uca çalışır hale getirmektir.

---

## 🎯 Amaçlar

* VLSM ile subnet planlaması yapmak
* VLAN kullanarak ağ segmentasyonu oluşturmak
* Trunk bağlantılar ile VLAN’ları taşımak
* Router-on-a-Stick ile Inter-VLAN routing sağlamak
* Static ve Default routing kullanmak
* Gerçekçi bir topoloji üzerinde test yapmak

---

## 🧠 Kullanılan Teknolojiler

* VLSM (Variable Length Subnet Mask)
* VLAN (Virtual LAN)
* Trunk (802.1Q)
* Inter-VLAN Routing (ROAS)
* Static Routing
* Default Routing
* Spanning Tree Protocol (STP)

---

## 🌐 Ağ Topolojisi

[Network Topology](topology.png)

Bu topolojide:

* Farklı büyüklükte VLAN’lar oluşturulmuştur
* Switchler arasında trunk bağlantılar kurulmuştur
* Router üzerinden VLAN’lar arası iletişim sağlanmıştır
* Routerlar arasında point-to-point bağlantılar kurulmuştur
* Layer 2 seviyesinde oluşabilecek loop’lar STP ile kontrol edilmiştir

---

## 🧮 VLSM IP Planı

| VLAN / Amaç | Network          | Subnet Mask     | Host Kapasitesi |
| ----------- | ---------------- | --------------- | --------------- |
| VLAN40      | 192.168.1.0/26   | 255.255.255.192 | 62              |
| VLAN30      | 192.168.1.64/27  | 255.255.255.224 | 30              |
| VLAN20      | 192.168.1.96/27  | 255.255.255.224 | 30              |
| VLAN10      | 192.168.1.128/28 | 255.255.255.240 | 14              |
| Routing     | 192.168.1.144/29 | 255.255.255.248 | 6               |
| Routing     | 192.168.1.152/30 | 255.255.255.252 | 2               |

📌 IP planı, en büyük subnet ihtiyacından başlanarak küçüğe doğru bölünerek oluşturulmuştur.

---

## 🔧 Yapılandırma Detayları

### 🔹 VLAN ve Switch Konfigürasyonu

* VLAN10, VLAN20, VLAN30 ve VLAN40 oluşturuldu
* Access portlar ilgili VLAN’lara atandı
* Switchler arası bağlantılar trunk olarak ayarlandı

---

### 🔹 Inter-VLAN Routing (Router-on-a-Stick)

Router üzerinde subinterface kullanılarak VLAN’lar arası iletişim sağlandı:

```
interface g0/0.10
 encapsulation dot1Q 10
 ip address ...

interface g0/0.20
 encapsulation dot1Q 20
 ip address ...
```

---

### 🔹 Routing Yapısı

* Routerlar arasında **static route** yapılandırıldı
* Ağ dışına erişim için **default route** kullanıldı

---

### 🔹 Layer 2 Güvenliği (STP)

* Switchler arasında loop oluşabilecek topoloji kuruldu
* Spanning Tree Protocol ile loop engellendi
* Gereksiz yollar blocking duruma alındı

---

## 🧪 Test ve Doğrulama

Ağ yapılandırması aşağıdaki testlerle doğrulanmıştır:

* ✔ Aynı VLAN içindeki cihazlar arasında iletişim sağlandı
* ✔ Farklı VLAN’lar arasında iletişim sağlandı
* ✔ PC’ler default gateway’lerine erişebiliyor
* ✔ Routerlar arası bağlantılar çalışıyor
* ✔ Tüm ağ uçtan uca erişilebilir durumda

---

## 🎯 Öğrenilenler

Bu çalışma ile birlikte:

* VLSM ile IP adresleme mantığı
* VLAN ile ağ segmentasyonu
* Inter-VLAN routing (ROAS) yapısı
* Static ve default routing kullanımı
* Gerçekçi bir ağ topolojisi kurma

konularında pratik deneyim kazanılmıştır.

---

## 📎 Not

Bu proje, CCNA seviyesinde ağ konularını pekiştirmek amacıyla hazırlanmıştır ve tamamen eğitim amaçlıdır.
