---
ms.openlocfilehash: 30580b3fde5b8a99862896bb7d31c6c4024f97e8
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74568235"
---
### <a name="floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception"></a>Kayan nokta ayrıştırma işlemleri artık başarısız olmaz veya bir OverflowException oluşturmaz

Kayan nokta ayrıştırma yöntemleri artık <xref:System.OverflowException> oluşturmaz veya sayısal değeri <xref:System.Single> veya <xref:System.Double> kayan nokta türünde olan bir dizeyi ayrıştırdıklarında `false` döndürmez.

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET Core 2,2 ve önceki sürümlerinde, <xref:System.Double.Parse%2A?displayProperty=nameWithType> ve <xref:System.Single.Parse%2A?displayProperty=nameWithType> yöntemleri kendi tür aralığının dışında bir <xref:System.OverflowException> oluşturur. <xref:System.Double.TryParse%2A?displayProperty=nameWithType> ve <xref:System.Single.TryParse%2A?displayProperty=nameWithType> yöntemleri, Aralık dışı sayısal değerlerin dize temsilleri için `false` döndürür.

.NET Core 3,0 ile başlayarak, Aralık dışı sayısal dizeler ayrıştırılırken <xref:System.Double.Parse%2A?displayProperty=nameWithType>, <xref:System.Double.TryParse%2A?displayProperty=nameWithType>, <xref:System.Single.Parse%2A?displayProperty=nameWithType>ve <xref:System.Single.TryParse%2A?displayProperty=nameWithType> yöntemleri artık başarısız olmaz. Bunun yerine, <xref:System.Double> ayrıştırma yöntemleri <xref:System.Double.MaxValue?displayProperty=nameWithType>aşan değerler için <xref:System.Double.PositiveInfinity?displayProperty=nameWithType> döndürür ve <xref:System.Double.MinValue?displayProperty=nameWithType>küçük değerler için <xref:System.Double.NegativeInfinity?displayProperty=nameWithType> döndürür. Benzer şekilde, <xref:System.Single> ayrıştırma yöntemleri <xref:System.Single.MaxValue?displayProperty=nameWithType>aşan değerler için <xref:System.Single.PositiveInfinity?displayProperty=nameWithType> döndürür ve <xref:System.Single.MinValue?displayProperty=nameWithType>küçük değerler için <xref:System.Single.NegativeInfinity?displayProperty=nameWithType> döndürür.

Bu değişiklik, geliştirilmiş IEEE 754:2008 uyumluluğu için yapılmıştır.

#### <a name="version-introduced"></a>Sunulan sürüm

3.0

#### <a name="recommended-action"></a>Önerilen eylem

Bu değişiklik, kodunuzun ikisini de iki şekilde etkileyebilir:

- Kodunuz, bir taşma oluştuğunda yürütülecek <xref:System.OverflowException> işleyicisine bağlıdır. Bu durumda `catch` ifadesini kaldırmalı ve gerekli kodu <xref:System.Double.IsInfinity%2A?displayProperty=nameWithType> ya da <xref:System.Single.IsInfinity%2A?displayProperty=nameWithType> `true`olup olmadığını test eden bir `If` bildirimine yerleştirmeniz gerekir.

- Kodunuz, kayan nokta değerlerinin `Infinity`değil olduğunu varsayar. Bu durumda, `PositiveInfinity` ve `NegativeInfinity`kayan nokta değerlerini denetlemek için gerekli kodu eklemeniz gerekir.

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
