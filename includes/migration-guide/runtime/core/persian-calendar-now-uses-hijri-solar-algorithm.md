---
ms.openlocfilehash: bfe406161ac754124a2cc38c68a80c3b9fb2c7f6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858560"
---
### <a name="persian-calendar-now-uses-the-hijri-solar-algorithm"></a>Farsça takvim şimdi Hicri güneş algoritması kullanır

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.6 ile <xref:System.Globalization.PersianCalendar?displayProperty=name> başlayan sınıf, Hicri güneş algoritmasını kullanır. Tarihler <xref:System.Globalization.PersianCalendar?displayProperty=name> ve diğer takvimler arasındaki tarihleri dönüştürmek, 1800'den önceki veya 2023'ten (Gregoryen) önceki tarihler için .NET Framework 4.6 ile başlayan biraz farklı bir sonuç üretebilir. Ayrıca, <xref:System.Globalization.PersianCalendar.MinSupportedDateTime?displayProperty=nameWithType> şimdi <code>March 22, 0622</code> yerine <code>March 21, 0622</code>.|
|Öneri|.NET Framework 4.6'da Farsça Takvim'i kullanırken bazı erken veya geç tarihlerin biraz farklı olabileceğini unutmayın. Ayrıca, farklı .NET Framework sürümlerinde çalıştırılabilen işlemler arasındaki tarihleri serihale getirdiğinizde, bunları PersianCalendar tarih dizeleri olarak saklamayın (bu değerler farklı olabileceğinden).|
|Kapsam|İkincil|
|Sürüm|4.6|
|Tür|Çalışma Zamanı|
|Etkilenen API’ler|<ul><li><xref:System.Globalization.PersianCalendar?displayProperty=nameWithType></li></ul>|
