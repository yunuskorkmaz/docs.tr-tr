---
ms.openlocfilehash: 30580b3fde5b8a99862896bb7d31c6c4024f97e8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74568235"
---
### <a name="floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception"></a>Kayan nokta ayrışma işlemleri artık başarısız veya bir OverflowException atmak

Kayan nokta ayrıştırma yöntemleri, <xref:System.OverflowException> sayısal `false` değeri <xref:System.Single> veya <xref:System.Double> kayan nokta türünün aralığının dışında olan bir dizeyi ayrıştırdıkları zaman artık bir veya geri dönüş atmaz.

#### <a name="change-description"></a>Açıklamayı değiştir

.NET Core 2.2 ve önceki <xref:System.Double.Parse%2A?displayProperty=nameWithType> <xref:System.Single.Parse%2A?displayProperty=nameWithType> sürümlerinde, <xref:System.OverflowException> ve yöntemler kendi türüaralığının dışında olan değerler için bir değer atar. Ve <xref:System.Double.TryParse%2A?displayProperty=nameWithType> <xref:System.Single.TryParse%2A?displayProperty=nameWithType> yöntemler, `false` aralık dışı sayısal değerlerin dize gösterimleri için döndürür.

.NET Core 3.0 ile <xref:System.Double.Parse%2A?displayProperty=nameWithType> <xref:System.Double.TryParse%2A?displayProperty=nameWithType>başlayarak, aralık dışı sayısal dizeleri ayrıştirırken , , <xref:System.Single.Parse%2A?displayProperty=nameWithType>ve <xref:System.Single.TryParse%2A?displayProperty=nameWithType> yöntemler artık başarısız olmaz. Bunun <xref:System.Double> yerine, ayrıştırma yöntemleri aşan <xref:System.Double.PositiveInfinity?displayProperty=nameWithType> <xref:System.Double.MaxValue?displayProperty=nameWithType>değerler <xref:System.Double.NegativeInfinity?displayProperty=nameWithType> için döndürür <xref:System.Double.MinValue?displayProperty=nameWithType>ve daha az olan değerler için geri döner. Benzer şekilde, <xref:System.Single> ayrıştırma <xref:System.Single.PositiveInfinity?displayProperty=nameWithType> yöntemleri aşan <xref:System.Single.MaxValue?displayProperty=nameWithType>değerler için <xref:System.Single.NegativeInfinity?displayProperty=nameWithType> döndürür ve <xref:System.Single.MinValue?displayProperty=nameWithType>daha az olan değerler için geri döner.

Bu değişiklik geliştirilmiş IEEE 754:2008 uyumluluğu için yapılmıştır.

#### <a name="version-introduced"></a>Sürüm tanıtıldı

3,0

#### <a name="recommended-action"></a>Önerilen eylem

Bu değişiklik kodunuzu iki şekilde etkileyebilir:

- Kodunuz, taşma oluştuğunda <xref:System.OverflowException> yürütülmesi için işleyiciye bağlıdır. `catch` Bu durumda, deyimi kaldırmalı ve gerekli kodu `If` bir ifadeye <xref:System.Double.IsInfinity%2A?displayProperty=nameWithType> <xref:System.Single.IsInfinity%2A?displayProperty=nameWithType> yerleştirmeli ve bu kodu sınama. `true`

- Kodunuz kayan nokta değerlerinin `Infinity`. Bu durumda, kayan nokta değerlerini denetlemek için gerekli kodu `PositiveInfinity` `NegativeInfinity`eklemeniz gerekir ve.

#### <a name="category"></a>Kategori

CoreFx

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Double.Parse%2A?displayProperty=nameWithType>
- <xref:System.Double.TryParse%2A?displayProperty=nameWithType>
- <xref:System.Single.Parse%2A?displayProperty=nameWithType>
- <xref:System.Single.TryParse%2A?displayProperty=nameWithType>

<!--

### Affected APIs

- `Overload:System.Double.Parse`
- `Overload:System.Double.TryParse`
- `Overload:System.Single.Parse`
- `Overload:System.Single.TryParse`

-->
