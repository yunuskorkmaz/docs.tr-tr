---
ms.openlocfilehash: 719f336e1b38597674d6ee8f0c5429dd965054b1
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83720938"
---
### <a name="floating-point-formatting-and-parsing-behavior-changed"></a>Kayan nokta biçimlendirme ve ayrıştırma davranışı değişti

Kayan nokta ayrıştırma ve biçimlendirme davranışı ( <xref:System.Double> ve türlerine göre <xref:System.Single> ) artık IEEE uyumludur.

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET Core 2,2 ve önceki sürümlerinde, ve ile biçimlendirme ve,, <xref:System.Double.ToString%2A?displayProperty=nameWithType> <xref:System.Single.ToString%2A?displayProperty=nameWithType> ve ile <xref:System.Double.Parse%2A?displayProperty=nameWithType> ayrıştırma <xref:System.Double.TryParse%2A?displayProperty=nameWithType> , <xref:System.Single.Parse%2A?displayProperty=nameWithType> <xref:System.Single.TryParse%2A?displayProperty=nameWithType> IEEE uyumlu değildir. Sonuç olarak, bir değerin desteklenen herhangi bir standart veya özel biçim dizesiyle gidiş dönüş olacağını garanti etmek olanaksızdır. Bazı girişler için, biçimlendirilen bir değeri Ayrıştırma girişimi başarısız olabilir ve diğerleri için ayrıştırılmış değer özgün değere eşit değildir.

.NET Core 3,0 ile başlayarak, ayrıştırma ve biçimlendirme işlemleri IEEE 754 ile uyumludur. Bu, .NET 'teki kayan nokta türlerinin davranışının C# gibi IEEE uyumlu dillerle eşleştiğinden emin olmanızı sağlar. Daha fazla bilgi için bkz. [.NET Core 3,0 blog gönderisine kayan nokta ayrıştırma ve biçimlendirme geliştirmeleri](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) .

#### <a name="version-introduced"></a>Sunulan sürüm

3.0

#### <a name="recommended-action"></a>Önerilen eylem

.NET Core 3,0 Web günlüğü gönderisine ilişkin [kayan nokta ayrıştırma ve biçimlendirme geliştirmelerinden](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) oluşan "var olan koda etkisi" bölümünde, .net Core 2,2 uygulamalarıyla karşılaştırıldığında bir davranış değişikliği gözlemlerseniz kodunuzda değişiklik yapılması önerilir. Bu, istenen davranışı zorlamak için farklı bir standart veya özel biçim dizesi kullanmayı içerir. Bazı sonuçlar daha önceden yanlış olsaydı geçici bir çözüme sahip olmayabilir.

#### <a name="category"></a>Kategori

Core .NET kitaplıkları

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Double.ToString%2A?displayProperty=nameWithType>
- <xref:System.Single.ToString%2A?displayProperty=nameWithType>
- <xref:System.Double.Parse%2A?displayProperty=nameWithType>
- <xref:System.Double.TryParse%2A?displayProperty=nameWithType>
- <xref:System.Single.Parse%2A?displayProperty=nameWithType>
- <xref:System.Single.TryParse%2A?displayProperty=nameWithType>

<!-- 

#### Affected APIs

- `Overload:System.Double.ToString`
- `Overload:System.Single.ToString`
- `Overload:System.Double.Parse`
- `Overload:System.Double.TryParse`
- `Overload:System.Single.Parse`
- `Overload:System.Single.TryParse`

-->
