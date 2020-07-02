---
ms.openlocfilehash: 946e71f2f466664c8f9fcf4811288ce693a872eb
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616295"
---
### <a name="workflow-xaml-checksums-for-symbols-changed-from-sha1-to-sha256"></a>Semboller için iş akışı XAML sağlama toplamı, SHA1 'den SHA256 'e değişti

#### <a name="details"></a>Ayrıntılar

Visual Studio ile hata ayıklamayı desteklemek için, Iş akışı çalışma zamanı bir karma algoritması kullanarak bir iş akışı XAML dosyası için bir sağlama toplamı üretir. .NET Framework 4.6.2 ve önceki sürümlerde, iş akışı sağlama toplamı karması, FIPS özellikli sistemlerde sorun oluşmasına neden olan MD5 algoritmasını kullandı. 4,7 .NET Framework başlayarak, varsayılan algoritma SHA1 olarak değiştirilmiştir. 4,8 .NET Framework başlayarak, varsayılan algoritma SHA256 olarak değiştirilmiştir.

#### <a name="suggestion"></a>Öneri

Kodunuz iş akışı örneklerini yükleyemediğinden veya bir sağlama toplamı hatası nedeniyle uygun sembolleri bulamadı, `AppContext` "Switch.SysTItem anahtarını ayarlamayı deneyin. Activities. UseSHA1HashForDebuggerSymbols " `true` . Kod:

```csharp
System.AppContext.SetSwitch("Switch.System.Activities.UseSHA1HashForDebuggerSymbols", true);
```

Ya da yapılandırmada:

```xml
<configuration>
  <runtime>
    <AppContextSwitchOverrides value="Switch.System.Activities.UseSHA1HashForDebuggerSymbols=true" />
  </runtime>
</configuration>
```

| Name    | Değer       |
|:--------|:------------|
| Kapsam   | İkincil       |
| Sürüm | 4,8         |
| Tür    | Yeniden Hedefleme |
