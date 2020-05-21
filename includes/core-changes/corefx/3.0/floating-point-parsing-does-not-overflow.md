---
ms.openlocfilehash: 935d9b2368ea4a0eeca7943dcbd584d24d2a6633
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721249"
---
### <a name="floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception"></a>Kayan nokta ayrıştırma işlemleri artık başarısız olmaz veya bir OverflowException oluşturmaz

Kayan nokta ayrıştırma yöntemleri, <xref:System.OverflowException> `false` sayısal değeri <xref:System.Single> veya kayan nokta türü aralığının dışında olan bir dizeyi ayrıştırdıklarında artık bir veya döndürmez <xref:System.Double> .

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET Core 2,2 ve önceki sürümlerinde, <xref:System.Double.Parse%2A?displayProperty=nameWithType> ve yöntemleri kendi <xref:System.Single.Parse%2A?displayProperty=nameWithType> <xref:System.OverflowException> türü aralığının dışında bir değer oluşturur. <xref:System.Double.TryParse%2A?displayProperty=nameWithType>Ve <xref:System.Single.TryParse%2A?displayProperty=nameWithType> yöntemleri, `false` Aralık dışı sayısal değerlerin dize temsillerine yönelik döndürülür.

.NET Core 3,0 ile başlayarak,, <xref:System.Double.Parse%2A?displayProperty=nameWithType> , <xref:System.Double.TryParse%2A?displayProperty=nameWithType> <xref:System.Single.Parse%2A?displayProperty=nameWithType> ve <xref:System.Single.TryParse%2A?displayProperty=nameWithType> yöntemleri Aralık dışı sayısal dizeler ayrıştırılırken artık başarısız olmaz. Bunun yerine, <xref:System.Double> ayrıştırma yöntemleri <xref:System.Double.PositiveInfinity?displayProperty=nameWithType> , aşan değerler için döndürülür <xref:System.Double.MaxValue?displayProperty=nameWithType> ve ' <xref:System.Double.NegativeInfinity?displayProperty=nameWithType> den küçük değerler için geri döner <xref:System.Double.MinValue?displayProperty=nameWithType> . Benzer şekilde, <xref:System.Single> ayrıştırma yöntemleri <xref:System.Single.PositiveInfinity?displayProperty=nameWithType> , aşan değerler için döndürülür <xref:System.Single.MaxValue?displayProperty=nameWithType> ve ' <xref:System.Single.NegativeInfinity?displayProperty=nameWithType> den küçük değerler için geri döner <xref:System.Single.MinValue?displayProperty=nameWithType> .

Bu değişiklik, geliştirilmiş IEEE 754:2008 uyumluluğu için yapılmıştır.

#### <a name="version-introduced"></a>Sunulan sürüm

3.0

#### <a name="recommended-action"></a>Önerilen eylem

Bu değişiklik, kodunuzun ikisini de iki şekilde etkileyebilir:

- Kodunuz, <xref:System.OverflowException> bir taşma oluştuğunda yürütülmesi için işleyicisine bağlıdır. Bu durumda, `catch` ifadesini kaldırmalı ve gerekli kodu `If` , veya olup olmadığını test eden bir deyime yerleştirmeniz gerekir <xref:System.Double.IsInfinity%2A?displayProperty=nameWithType> <xref:System.Single.IsInfinity%2A?displayProperty=nameWithType> `true` .

- Kodunuz, kayan nokta değerlerinin değil olduğunu varsayar `Infinity` . Bu durumda, ve ' ın kayan nokta değerlerini denetlemek için gerekli kodu eklemelisiniz `PositiveInfinity` `NegativeInfinity` .

#### <a name="category"></a>Kategori

Core .NET kitaplıkları

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Double.Parse%2A?displayProperty=nameWithType>
- <xref:System.Double.TryParse%2A?displayProperty=nameWithType>
- <xref:System.Single.Parse%2A?displayProperty=nameWithType>
- <xref:System.Single.TryParse%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Double.Parse`
- `Overload:System.Double.TryParse`
- `Overload:System.Single.Parse`
- `Overload:System.Single.TryParse`

-->
