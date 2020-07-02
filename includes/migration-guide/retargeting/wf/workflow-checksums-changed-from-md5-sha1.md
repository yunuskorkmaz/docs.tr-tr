---
ms.openlocfilehash: 72d48d1daa85b6891c122f2fcc5279642253b926
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614842"
---
### <a name="workflow-checksums-changed-from-md5-to-sha1"></a>İş akışı sağlama toplamı, MD5 'den SHA1 'ye değişti

#### <a name="details"></a>Ayrıntılar

Visual Studio ile hata ayıklamayı desteklemek için, Iş akışı çalışma zamanı bir karma algoritması kullanarak bir iş akışı örneği için bir sağlama toplamı üretir. .NET Framework 4.6.2 ve önceki sürümlerde, iş akışı sağlama toplamı karması, FIPS özellikli sistemlerde sorun oluşmasına neden olan MD5 algoritmasını kullandı. 4,7 .NET Framework başlayarak algoritma SHA1 ' dır. Kodunuz bu sağlama toplamlarını kalıcı hale alıyorsa, bunlar uyumsuz olur.

#### <a name="suggestion"></a>Öneri

Kodunuz, sağlama toplamı hatası nedeniyle iş akışı örneklerini yükleyememesi durumunda, `AppContext` anahtarı &quot;Switch.Sysdıtem ayarlamayı deneyin. Activities. UseMD5ForWFDebugger &quot; . Kodda:

```csharp
System.AppContext.SetSwitch("Switch.System.Activities.UseMD5ForWFDebugger", true);
```

Ya da yapılandırmada:

```xml
<configuration>
  <runtime>
    <AppContextSwitchOverrides value="Switch.System.Activities.UseMD5ForWFDebugger=true" />
  </runtime>
</configuration>
```

| Name    | Değer       |
|:--------|:------------|
| Kapsam   | İkincil       |
| Sürüm | 4,7         |
| Tür    | Yeniden Hedefleme |
