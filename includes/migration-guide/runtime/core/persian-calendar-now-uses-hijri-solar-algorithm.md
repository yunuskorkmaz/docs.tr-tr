---
ms.openlocfilehash: 130c26b7d135db232eb40a2c466aa3bdb2481ace
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67858560"
---
### <a name="persian-calendar-now-uses-the-hijri-solar-algorithm"></a>Farsça takvimi Hicri güneşin algoritması artık kullanır.

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.6 ile başlayan <xref:System.Globalization.PersianCalendar?displayProperty=name> sınıfı Hicri güneşin algoritması kullanır. Tarihleri arasında dönüştürme <xref:System.Globalization.PersianCalendar?displayProperty=name> ve diğer takvimlerdeki biraz farklı sonuç ile başlayan bir .NET Framework 4.6 için 1800'den önceki bir sürümü veya daha sonraki bir (Gregoryen) 2023 tarihleri üretebilir. Ayrıca, <xref:System.Globalization.PersianCalendar.MinSupportedDateTime?displayProperty=nameWithType> artık <code>March 22, 0622</code> yerine <code>March 21, 0622</code>.|
|Öneri|Bazı erken ve geç tarihleri PersianCalendar .NET Framework 4. 6 ' kullanırken biraz farklı olabileceğini unutmayın. (Bu değerler farklı olabileceğinden) ayrıca, farklı .NET Framework sürümleri üzerinde çalışmaya başlayabilir işlemleri arasındaki tarihleri serileştirilirken bunları PersianCalendar tarihi dize olarak depolamayın.|
|`Scope`|Küçük|
|Version|4.6|
|Type|Çalışma zamanı|
|Etkilenen API’ler|<ul><li><xref:System.Globalization.PersianCalendar?displayProperty=nameWithType></li></ul>|

