---
ms.openlocfilehash: e4d9efe7d2a06a1e501b070c23184dcd913dba71
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621411"
---
### <a name="persian-calendar-now-uses-the-hijri-solar-algorithm"></a>Farsça takvimi artık Hicri güneş algoritmasını kullanıyor

#### <a name="details"></a>Ayrıntılar

.NET Framework 4,6 ' den başlayarak, <xref:System.Globalization.PersianCalendar?displayProperty=fullName> sınıfı Hicri Solar algoritmasını kullanır. Ve diğer takvimler arasındaki tarihleri dönüştürmek, <xref:System.Globalization.PersianCalendar?displayProperty=fullName> 2023 1800 ' den (Gregoryen) daha önceki tarihler için .NET Framework 4,6 ' den başlayarak biraz farklı bir sonuç üretebilir. Ayrıca, <xref:System.Globalization.PersianCalendar.MinSupportedDateTime?displayProperty=nameWithType> artık <code>March 22, 0622</code> yerine <code>March 21, 0622</code> .

#### <a name="suggestion"></a>Öneri

.NET Framework 4,6 ' de Persıancalendar kullanılırken erken veya geç tarihlerin biraz farklı olabileceğini unutmayın. Ayrıca, farklı .NET Framework sürümlerde çalışabilen süreçler arasındaki tarihleri serileştirilirken, bu değerler farklı olabileceğinden, bunları bir veya daha fazla takvim tarih dizesi olarak saklamayın.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |İkincil|
|Sürüm|4.6|
|Tür|Çalışma Zamanı

#### <a name="affected-apis"></a>Etkilenen API’ler

-<xref:System.Globalization.PersianCalendar?displayProperty=nameWithType></li></ul>|
