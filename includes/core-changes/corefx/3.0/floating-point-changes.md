---
ms.openlocfilehash: ce4f09908b1025e8e5a0380c9bf035c6b0db479a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74568076"
---
### <a name="floating-point-formatting-and-parsing-behavior-changed"></a>Kayan nokta biçimlendirme ve ayrıştma davranışı değiştirildi

Kayan nokta ayrıştırma ve biçimlendirme <xref:System.Single> davranışı (ve <xref:System.Double> türleri tarafından) artık IEEE uyumludur.

#### <a name="change-description"></a>Açıklamayı değiştir

.NET Core 2.2 <xref:System.Double.ToString%2A?displayProperty=nameWithType> ve önceki sürümlerde, biçimlendirme ve <xref:System.Double.Parse%2A?displayProperty=nameWithType> <xref:System.Double.TryParse%2A?displayProperty=nameWithType> <xref:System.Single.Parse%2A?displayProperty=nameWithType> <xref:System.Single.TryParse%2A?displayProperty=nameWithType> <xref:System.Single.ToString%2A?displayProperty=nameWithType>, , , , ile ayrışma ve IEEE uyumlu değildir. Sonuç olarak, desteklenen herhangi bir standart veya özel biçim dizesiyle bir değerin gidiş dönüş olacağını garanti etmek mümkün değildir. Bazı girişler için biçimlendirilmiş bir değeri ayrışdırma girişimi başarısız olabilir ve diğerleri için ayrıştı değer özgün değere eşit değildir.

.NET Core 3.0 ile başlayan ayrışma ve biçimlendirme işlemleri IEEE 754 uyumlu. Bu, .NET'teki kayan nokta türlerinin davranışının C# gibi IEEE uyumlu dillerinkiyle eşleşmesini sağlar. Daha fazla bilgi için [.NET Core 3.0 blog gönderisinde Kayan nokta ayrıştırma ve biçimlendirme geliştirmelerine](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) bakın.

#### <a name="version-introduced"></a>Sürüm tanıtıldı

3,0

#### <a name="recommended-action"></a>Önerilen eylem

[.NET Core 3.0 blog gönderisinde Kayan nokta ayrıştırma ve biçimlendirme geliştirmeleri](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) bölümünün "Varolan koda olası etkisi" bölümü, .NET Core 2.2 uygulamalarına kıyasla davranış değişikliğini gözlemlerseniz kodunuzda değişiklikler önerir, bu, istenen davranışı uygulamak için farklı bir standart veya özel biçim dizesi kullanmayı içerir. Daha önce yanlış sayılsalardı, bazı sonuçların geçici çözüm eki olmayabilir.

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
