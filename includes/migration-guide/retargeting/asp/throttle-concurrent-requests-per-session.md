---
ms.openlocfilehash: b521f4163bf5bf4a369d0eec12dae503703a976e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614643"
---
### <a name="throttle-concurrent-requests-per-session"></a>Oturum başına eşzamanlı istekleri kısıtlama

#### <a name="details"></a>Ayrıntılar

.NET Framework 4.6.2 ve önceki sürümlerde, ASP.NET aynı SessionID ile istekleri sırayla yürütür ve ASP.NET her zaman varsayılan olarak tanımlama bilgileri aracılığıyla SessionID 'yi yayınlar. Bir sayfanın yanıt vermesi uzun sürerse, tarayıcıda <kbd>F5</kbd> tuşuna basarak sunucu performansını önemli ölçüde düşürür. Bu durumda, sıradaki istekleri izlemek için bir sayaç ekledik ve belirtilen sınırı aştığında istekleri sonlandıracağız. Varsayılan değer 50 ' dir. Sınıra ulaşılırsa, olay günlüğüne bir uyarı kaydedilir ve IIS günlüğüne bir HTTP 500 yanıtı kaydedilebilir.

#### <a name="suggestion"></a>Öneri

Eski davranışı geri yüklemek için, yeni davranışı devre dışı bırakmak üzere web.config dosyanıza aşağıdaki ayarı ekleyebilirsiniz.

```xml
<appSettings>
    <add key="aspnet:RequestQueueLimitPerSession" value="2147483647"/>
</appSettings>
```

| Name    | Değer       |
|:--------|:------------|
| Kapsam   | Edge        |
| Sürüm | 4,7         |
| Tür    | Yeniden Hedefleme |
