---
ms.openlocfilehash: 192873aa5069aa4f96a18716afb066c80b223e29
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002451"
---
### <a name="floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception"></a>Kayan nokta ayrıştırma işlemleri artık başarısız olmaz veya bir OverflowException oluşturmaz

Kayan nokta ayrıştırma yöntemleri artık, sayısal değeri <xref:System.Single> veya <xref:System.Double> kayan nokta türü aralığının dışında olan bir dizeyi ayrıştırdıklarında <xref:System.OverflowException> ' ı oluşturmaz veya `false` ' i döndürmez.

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET Core 2,2 ve önceki sürümlerinde, <xref:System.Double.Parse%2A?displayProperty=nameWithType> ve <xref:System.Single.Parse%2A?displayProperty=nameWithType> yöntemleri, ilgili türünün aralığı dışında değerler için bir <xref:System.OverflowException> oluşturur. @No__t-0 ve <xref:System.Single.TryParse%2A?displayProperty=nameWithType> yöntemleri, Aralık dışı sayısal değerlerin dize temsilleri için `false` ' i döndürür.

.NET Core 3,0 ile başlayarak, Aralık dışı sayısal dizeler ayrıştırılırken <xref:System.Double.Parse%2A?displayProperty=nameWithType>, <xref:System.Double.TryParse%2A?displayProperty=nameWithType>, <xref:System.Single.Parse%2A?displayProperty=nameWithType> ve <xref:System.Single.TryParse%2A?displayProperty=nameWithType> yöntemleri artık başarısız olmaz. Bunun yerine, <xref:System.Double> ayrıştırma yöntemleri <xref:System.Double.MaxValue?displayProperty=nameWithType> ' den fazla değerler için <xref:System.Double.PositiveInfinity?displayProperty=nameWithType> döndürür ve <xref:System.Double.MinValue?displayProperty=nameWithType> ' ten küçük değerler için <xref:System.Double.NegativeInfinity?displayProperty=nameWithType> ' ü döndürür. Benzer şekilde, <xref:System.Single> ayrıştırma yöntemleri <xref:System.Single.MaxValue?displayProperty=nameWithType> ' den fazla değerler için <xref:System.Single.PositiveInfinity?displayProperty=nameWithType> döndürür ve <xref:System.Single.MinValue?displayProperty=nameWithType> ' ten küçük değerler için <xref:System.Single.NegativeInfinity?displayProperty=nameWithType> ' ü döndürür.

Bu değişiklik, geliştirilmiş IEEE 754:2008 uyumluluğu için yapılmıştır. 

#### <a name="version-introduced"></a>Sunulan sürüm

3.0

#### <a name="recommended-action"></a>Önerilen eylem

Bu değişiklik, kodunuzun ikisini de iki şekilde etkileyebilir:

- Kodunuz, bir taşma oluştuğunda yürütülecek <xref:System.OverflowException> işleyicisine bağlıdır. Bu durumda, `catch` ifadesini kaldırmalı ve gerekli kodu <xref:System.Double.IsInfinity%2A?displayProperty=nameWithType> veya <xref:System.Single.IsInfinity%2A?displayProperty=nameWithType> `true` olup olmadığını test eden bir `If` ifadesine yerleştirmeniz gerekir.

- Kodunuz, kayan nokta değerlerinin `Infinity` olmadığı varsayılır. Bu durumda, `PositiveInfinity` ve `NegativeInfinity` ' in kayan nokta değerlerini denetlemek için gerekli kodu eklemeniz gerekir.

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
