---
ms.openlocfilehash: 418bcdca1e9a325894891d7b0e080ce035e2d1b4
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614679"
---
### <a name="aspnet-accessibility-improvements-in-net-framework-471"></a>.NET Framework 4.7.1 'de erişilebilirlik Iyileştirmeleri ASP.NET

#### <a name="details"></a>Ayrıntılar

4.7.1, ASP.NET .NET Framework ile başlayarak, ASP.NET müşterilerini daha iyi desteklemek için ASP.NET Web denetimlerinin Visual Studio 'da erişilebilirlik teknolojisiyle nasıl çalıştığını geliştirmiştir.  Bunlar aşağıdaki değişiklikleri içerir:

- Ayrıntılar görünümü sihirbazındaki alan Ekle iletişim kutusu ya da ListView sihirbazının ListView yapılandırma iletişim kutusu gibi denetimlerde eksik UI erişilebilirlik düzenlerini uygulamak için değişiklikler.
- Veri sayfalayıcı alanları Düzenleyicisi gibi Yüksek Karşıtlık modunda görüntüyü geliştirmek için değişiklikler.
- DataPager denetiminin sayfalayıcı alanlarını Düzenle Sihirbazı 'ndaki alanlar iletişim kutusu gibi denetimler için klavye gezinti deneyimlerini geliştirmek üzere yapılan değişiklikler veya veri kaynağını yapılandırma Sihirbazı 'nın veri kaynağını yapılandırma Sihirbazı ' nın veri seçimini Yapılandır iletişim kutusu.

#### <a name="suggestion"></a>Öneri

**Bu değişiklikleri kabul etme veya devre dışı bırakma** Visual Studio Tasarımcısı 'nın bu değişikliklerden faydalanabilir olması için .NET Framework 4.7.1 veya sonraki bir sürümde çalışmalıdır. Web uygulaması aşağıdaki yollarla bu değişikliklerden faydalanabilir:

- Varsayılan olarak aşağıdaki AppContext anahtarıyla yeni erişilebilirlik özelliklerini destekleyen Visual Studio 2017 15,3 veya üstünü yükler.
- `Switch.UseLegacyAccessibilityFeatures` `<runtime>` `false` Aşağıdaki örnekte gösterildiği gibi, appcontext anahtarını devenv.exe.config dosyasında bölümüne ekleyerek ve olarak ayarlayarak eski erişilebilirlik davranışlarını geri çevirin.

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
<runtime>
...
<!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true/false;key2=true/false'  -->
<AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false" />
...
</runtime>
</configuration>
```

.NET Framework 4.7.1 veya üstünü hedefleyen ve eski erişilebilirlik davranışını korumak isteyen uygulamalar, bu AppContext anahtarını açıkça olarak ayarlayarak eski erişilebilirlik özelliklerinin kullanımını kabul edebilir `true` .

| Name    | Değer       |
|:--------|:------------|
| Kapsam   | İkincil       |
| Sürüm | 4.7.1       |
| Tür    | Yeniden Hedefleme |
