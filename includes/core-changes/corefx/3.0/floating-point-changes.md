---
ms.openlocfilehash: ce4f09908b1025e8e5a0380c9bf035c6b0db479a
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74568076"
---
### <a name="floating-point-formatting-and-parsing-behavior-changed"></a>Kayan nokta biçimlendirme ve ayrıştırma davranışı değişti

Kayan nokta ayrıştırma ve biçimlendirme davranışı (<xref:System.Double> ve <xref:System.Single> türlerine göre) artık IEEE uyumludur.

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET Core 2,2 ve önceki sürümlerinde, <xref:System.Double.ToString%2A?displayProperty=nameWithType> ve <xref:System.Single.ToString%2A?displayProperty=nameWithType>ile biçimlendirme ve <xref:System.Double.Parse%2A?displayProperty=nameWithType>, <xref:System.Double.TryParse%2A?displayProperty=nameWithType>, <xref:System.Single.Parse%2A?displayProperty=nameWithType>ve <xref:System.Single.TryParse%2A?displayProperty=nameWithType> ile ayrıştırma IEEE uyumlu değildir. Sonuç olarak, bir değerin desteklenen herhangi bir standart veya özel biçim dizesiyle gidiş dönüş olacağını garanti etmek olanaksızdır. Bazı girişler için, biçimlendirilen bir değeri Ayrıştırma girişimi başarısız olabilir ve diğerleri için ayrıştırılmış değer özgün değere eşit değildir.

.NET Core 3,0 ile başlayarak, ayrıştırma ve biçimlendirme işlemleri IEEE 754 ile uyumludur. Bu, .NET 'teki kayan nokta türleri davranışının gibi IEEE uyumlu dillerle eşleşmesini sağlar C#. Daha fazla bilgi için bkz. [.NET Core 3,0 blog gönderisine kayan nokta ayrıştırma ve biçimlendirme geliştirmeleri](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) .

#### <a name="version-introduced"></a>Sunulan sürüm

3.0

#### <a name="recommended-action"></a>Önerilen eylem

.NET Core 3,0 Web günlüğü gönderisine ilişkin [kayan nokta ayrıştırma ve biçimlendirme geliştirmelerinden](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) oluşan "var olan koda etkisi" bölümünde, .net Core 2,2 uygulamalarıyla karşılaştırıldığında bir davranış değişikliği gözlemlerseniz kodunuzda değişiklik yapılması önerilir. Bu, istenen davranışı zorlamak için farklı bir standart veya özel biçim dizesi kullanmayı içerir. Bazı sonuçlar daha önceden yanlış olsaydı geçici bir çözüme sahip olmayabilir.

#### <a name="category"></a>Kategori

CoreFx

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Double.ToString%2A?displayProperty=nameWithType>
- <xref:System.Single.ToString%2A?displayProperty=nameWithType>
- <xref:System.Double.Parse%2A?displayProperty=nameWithType>
- <xref:System.Double.TryParse%2A?displayProperty=nameWithType>
- <xref:System.Single.Parse%2A?displayProperty=nameWithType>
- <xref:System.Single.TryParse%2A?displayProperty=nameWithType>

<!-- 

### Affected APIs

- `Overload:System.Double.ToString`
- `Overload:System.Single.ToString`
- `Overload:System.Double.Parse`
- `Overload:System.Double.TryParse`
- `Overload:System.Single.Parse`
- `Overload:System.Single.TryParse`

-->
