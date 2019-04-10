---
ms.openlocfilehash: bfe406161ac754124a2cc38c68a80c3b9fb2c7f6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234303"
---
### <a name="persian-calendar-now-uses-the-hijri-solar-algorithm"></a>Farsça takvimi Hicri güneşin algoritması artık kullanır.

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.6 ile başlayan <xref:System.Globalization.PersianCalendar?displayProperty=name> sınıfı Hicri güneşin algoritması kullanır. Tarihleri arasında dönüştürme <xref:System.Globalization.PersianCalendar?displayProperty=name> ve diğer takvimlerdeki biraz farklı sonuç ile başlayan bir .NET Framework 4.6 için 1800'den önceki bir sürümü veya daha sonraki bir (Gregoryen) 2023 tarihleri üretebilir. Ayrıca, <xref:System.Globalization.PersianCalendar.MinSupportedDateTime?displayProperty=nameWithType> artık <code>March 22, 0622</code> yerine <code>March 21, 0622</code>.|
|Öneri|Bazı erken ve geç tarihleri PersianCalendar .NET Framework 4. 6 ' kullanırken biraz farklı olabileceğini unutmayın. (Bu değerler farklı olabileceğinden) ayrıca, farklı .NET Framework sürümleri üzerinde çalışmaya başlayabilir işlemleri arasındaki tarihleri serileştirilirken bunları PersianCalendar tarihi dize olarak depolamayın.|
|Kapsam|İkincil|
|Sürüm|4.6|
|Tür|Çalışma zamanı|
|Etkilenen API’ler|<ul><li><xref:System.Globalization.PersianCalendar?displayProperty=nameWithType></li></ul>|
