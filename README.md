# Sensör Verileri ve Diferansiyel Denklemlerle Kurutma Bitiş Zamanı Tahmini

![Durum](https://img.shields.io/badge/durum-devam%20ediyor-orange)
![Python](https://img.shields.io/badge/Python-3776AB?logo=python&logoColor=white)
![IoT](https://img.shields.io/badge/IoT-sens%C3%B6r%20verisi-blue)

> 🚧 **Bu proje geliştirme aşamasındadır.** Kod ve deney sonuçları ilerledikçe bu depoya eklenecektir.

## Proje Hakkında

Kurutma işlemlerinde genellikle **sabit bir süre** uygulanır ya da ürünün kuruyup kurumadığı işlem sonrasında **elle ölçülür**. Bu yöntemler ürünün gereğinden fazla ya da eksik kurumasına, enerji ve zaman kaybına yol açar.

Bu proje, kurutma sırasında **sıcaklık**, **nem** ve **tepsi ağırlığı** değişimlerini anlık olarak izler. Kuruma eğrisini **diferansiyel denklemlerle** modelleyip ilk saatlerin verisine uydurur ve kurumanın ne zaman biteceğini tahmin eder. Sistem:

- Kurutmayı **ne zaman durduracağına kendisi (otonom) karar verir**.
- **Tahmin hatasını dakika bazında** ölçer ve raporlar.

## Yöntem

Ürünün nem oranının zamanla değişimi, birinci dereceden bir diferansiyel denklemle modellenir:

```
dM/dt = -k · (M - Mₑ)
```

- `M`: Ürünün anlık nem oranı (tepsi ağırlığından hesaplanır)
- `Mₑ`: Denge nem oranı (ortam sıcaklığı ve nemine bağlı)
- `k`: Kuruma hız sabiti

Kurutmanın ilk saatlerinde toplanan ağırlık verisi bu modele uydurularak `k` ve `Mₑ` parametreleri bulunur. Model ileriye doğru çözülerek ürünün hedef nem oranına ulaşacağı zaman tahmin edilir. Yeni veri geldikçe tahmin güncellenir.

## Deney Aşamaları

1. **Elma dilimleri:** İlk testler elma dilimleriyle gerçekleştiriliyor.
2. **İkincil ürün grupları:** Model, farklı ürün gruplarında doğrulanacak.

## Teknolojiler

- **Python:** Veri işleme, model uydurma ve tahmin
- **Diferansiyel denklem modellemesi:** Kuruma eğrisinin fiziksel modeli
- **Sensör veri analitiği:** Ağırlık, sıcaklık ve nem
- **Zaman serisi tahminleme**
- **IoT entegrasyonu:** Sensör verilerinin anlık toplanması

## Yol Haritası

- [x] Proje fikri ve yöntemin belirlenmesi
- [ ] Sensör düzeneğinin kurulması (yük hücresi, sıcaklık ve nem sensörü)
- [ ] Anlık veri toplama altyapısı (IoT)
- [ ] Diferansiyel denklem modelinin veriye uydurulması
- [ ] Bitiş zamanı tahmini ve otonom durdurma kararı
- [ ] Elma dilimleriyle deneyler ve tahmin hatasının (dakika) raporlanması
- [ ] İkincil ürün gruplarında doğrulama

## Geliştirici

**Beyzanur Kaya**, Süleyman Demirel Üniversitesi
[GitHub](https://github.com/Beyzanrkya) · [LinkedIn](https://www.linkedin.com/in/beyza-nur-kaya-795b3629a)
