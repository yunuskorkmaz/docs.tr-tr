---
ms.openlocfilehash: ce4f09908b1025e8e5a0380c9bf035c6b0db479a
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71182002"
---
### <a name="floating-point-formatting-and-parsing-behavior-changed"></a><span data-ttu-id="ffc10-101">Kayan nokta biçimlendirme ve ayrıştırma davranışı değişti</span><span class="sxs-lookup"><span data-stu-id="ffc10-101">Floating-point formatting and parsing behavior changed</span></span>

<span data-ttu-id="ffc10-102">Kayan nokta ayrıştırma ve biçimlendirme davranışı ( <xref:System.Double> ve <xref:System.Single> türlerine göre) artık IEEE uyumludur.</span><span class="sxs-lookup"><span data-stu-id="ffc10-102">Floating point parsing and formatting behavior (by the <xref:System.Double> and <xref:System.Single> types) are now IEEE-compliant.</span></span>

#### <a name="change-description"></a><span data-ttu-id="ffc10-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="ffc10-103">Change description</span></span>

<span data-ttu-id="ffc10-104">.NET Core 2,2 ve önceki sürümlerinde, <xref:System.Double.ToString%2A?displayProperty=nameWithType> ve <xref:System.Single.ToString%2A?displayProperty=nameWithType>ile biçimlendirme ve,, ve <xref:System.Single.TryParse%2A?displayProperty=nameWithType> ile <xref:System.Double.Parse%2A?displayProperty=nameWithType>ayrıştırma <xref:System.Double.TryParse%2A?displayProperty=nameWithType>, <xref:System.Single.Parse%2A?displayProperty=nameWithType>IEEE uyumlu değildir.</span><span class="sxs-lookup"><span data-stu-id="ffc10-104">In .NET Core 2.2 and earlier versions, formatting with <xref:System.Double.ToString%2A?displayProperty=nameWithType> and <xref:System.Single.ToString%2A?displayProperty=nameWithType>, and parsing with <xref:System.Double.Parse%2A?displayProperty=nameWithType>, <xref:System.Double.TryParse%2A?displayProperty=nameWithType>, <xref:System.Single.Parse%2A?displayProperty=nameWithType>, and <xref:System.Single.TryParse%2A?displayProperty=nameWithType> are not IEEE-compliant.</span></span> <span data-ttu-id="ffc10-105">Sonuç olarak, bir değerin desteklenen herhangi bir standart veya özel biçim dizesiyle gidiş dönüş olacağını garanti etmek olanaksızdır.</span><span class="sxs-lookup"><span data-stu-id="ffc10-105">As a result, it is impossible to guarantee that a value will roundtrip with any supported standard or custom format string.</span></span> <span data-ttu-id="ffc10-106">Bazı girişler için, biçimlendirilen bir değeri Ayrıştırma girişimi başarısız olabilir ve diğerleri için ayrıştırılmış değer özgün değere eşit değildir.</span><span class="sxs-lookup"><span data-stu-id="ffc10-106">For some inputs, the attempt to parse a formatted value can fail, and for others, the parsed value doesn't equal the original value.</span></span>

<span data-ttu-id="ffc10-107">.NET Core 3,0 ile başlayarak, ayrıştırma ve biçimlendirme işlemleri IEEE 754 ile uyumludur.</span><span class="sxs-lookup"><span data-stu-id="ffc10-107">Starting with .NET Core 3.0, parsing and formatting operations are IEEE 754-compliant.</span></span> <span data-ttu-id="ffc10-108">Bu, .NET 'teki kayan nokta türleri davranışının gibi IEEE uyumlu dillerle eşleşmesini sağlar C#.</span><span class="sxs-lookup"><span data-stu-id="ffc10-108">This ensures that the behavior of floating-point types in .NET matches that of IEEE-compliant languages such as C#.</span></span> <span data-ttu-id="ffc10-109">Daha fazla bilgi için bkz. [.NET Core 3,0 blog gönderisine kayan nokta ayrıştırma ve biçimlendirme geliştirmeleri](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) .</span><span class="sxs-lookup"><span data-stu-id="ffc10-109">For more information, see the [Floating-point parsing and formatting improvements in .NET Core 3.0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) blog post.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="ffc10-110">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="ffc10-110">Version introduced</span></span>

<span data-ttu-id="ffc10-111">3.0</span><span class="sxs-lookup"><span data-stu-id="ffc10-111">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="ffc10-112">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="ffc10-112">Recommended action</span></span>

<span data-ttu-id="ffc10-113">.NET Core 3,0 Web günlüğü gönderisine ilişkin [kayan nokta ayrıştırma ve biçimlendirme geliştirmelerinden](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) oluşan "var olan koda etkisi" bölümünde, .net Core 2,2 uygulamalarıyla karşılaştırıldığında bir davranış değişikliği gözlemlerseniz kodunuzda değişiklikler yapılır. Bu, istenen davranışı zorlamak için farklı bir standart veya özel biçim dizesi kullanmayı içerir.</span><span class="sxs-lookup"><span data-stu-id="ffc10-113">The "Potential impact to existing code" section of the [Floating-point parsing and formatting improvements in .NET Core 3.0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) blog post suggests changes to your code if you observe a change of behavior when compared to .NET Core 2.2 applications Generally, this involves using a different standard or custom format string to enforce the desired behavior.</span></span> <span data-ttu-id="ffc10-114">Bazı sonuçlar daha önceden yanlış olsaydı geçici bir çözüme sahip olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="ffc10-114">Some results may not have a workaround if they were previously incorrect.</span></span>

#### <a name="category"></a><span data-ttu-id="ffc10-115">Kategori</span><span class="sxs-lookup"><span data-stu-id="ffc10-115">Category</span></span>

<span data-ttu-id="ffc10-116">CoreFx</span><span class="sxs-lookup"><span data-stu-id="ffc10-116">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="ffc10-117">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="ffc10-117">Affected APIs</span></span>

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
