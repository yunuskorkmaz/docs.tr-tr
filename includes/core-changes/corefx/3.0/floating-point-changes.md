---
ms.openlocfilehash: 719f336e1b38597674d6ee8f0c5429dd965054b1
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83720938"
---
### <a name="floating-point-formatting-and-parsing-behavior-changed"></a><span data-ttu-id="b2d3a-101">Kayan nokta biçimlendirme ve ayrıştırma davranışı değişti</span><span class="sxs-lookup"><span data-stu-id="b2d3a-101">Floating-point formatting and parsing behavior changed</span></span>

<span data-ttu-id="b2d3a-102">Kayan nokta ayrıştırma ve biçimlendirme davranışı ( <xref:System.Double> ve türlerine göre <xref:System.Single> ) artık IEEE uyumludur.</span><span class="sxs-lookup"><span data-stu-id="b2d3a-102">Floating point parsing and formatting behavior (by the <xref:System.Double> and <xref:System.Single> types) are now IEEE-compliant.</span></span>

#### <a name="change-description"></a><span data-ttu-id="b2d3a-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="b2d3a-103">Change description</span></span>

<span data-ttu-id="b2d3a-104">.NET Core 2,2 ve önceki sürümlerinde, ve ile biçimlendirme ve,, <xref:System.Double.ToString%2A?displayProperty=nameWithType> <xref:System.Single.ToString%2A?displayProperty=nameWithType> ve ile <xref:System.Double.Parse%2A?displayProperty=nameWithType> ayrıştırma <xref:System.Double.TryParse%2A?displayProperty=nameWithType> , <xref:System.Single.Parse%2A?displayProperty=nameWithType> <xref:System.Single.TryParse%2A?displayProperty=nameWithType> IEEE uyumlu değildir.</span><span class="sxs-lookup"><span data-stu-id="b2d3a-104">In .NET Core 2.2 and earlier versions, formatting with <xref:System.Double.ToString%2A?displayProperty=nameWithType> and <xref:System.Single.ToString%2A?displayProperty=nameWithType>, and parsing with <xref:System.Double.Parse%2A?displayProperty=nameWithType>, <xref:System.Double.TryParse%2A?displayProperty=nameWithType>, <xref:System.Single.Parse%2A?displayProperty=nameWithType>, and <xref:System.Single.TryParse%2A?displayProperty=nameWithType> are not IEEE-compliant.</span></span> <span data-ttu-id="b2d3a-105">Sonuç olarak, bir değerin desteklenen herhangi bir standart veya özel biçim dizesiyle gidiş dönüş olacağını garanti etmek olanaksızdır.</span><span class="sxs-lookup"><span data-stu-id="b2d3a-105">As a result, it is impossible to guarantee that a value will roundtrip with any supported standard or custom format string.</span></span> <span data-ttu-id="b2d3a-106">Bazı girişler için, biçimlendirilen bir değeri Ayrıştırma girişimi başarısız olabilir ve diğerleri için ayrıştırılmış değer özgün değere eşit değildir.</span><span class="sxs-lookup"><span data-stu-id="b2d3a-106">For some inputs, the attempt to parse a formatted value can fail, and for others, the parsed value doesn't equal the original value.</span></span>

<span data-ttu-id="b2d3a-107">.NET Core 3,0 ile başlayarak, ayrıştırma ve biçimlendirme işlemleri IEEE 754 ile uyumludur.</span><span class="sxs-lookup"><span data-stu-id="b2d3a-107">Starting with .NET Core 3.0, parsing and formatting operations are IEEE 754-compliant.</span></span> <span data-ttu-id="b2d3a-108">Bu, .NET 'teki kayan nokta türlerinin davranışının C# gibi IEEE uyumlu dillerle eşleştiğinden emin olmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="b2d3a-108">This ensures that the behavior of floating-point types in .NET matches that of IEEE-compliant languages such as C#.</span></span> <span data-ttu-id="b2d3a-109">Daha fazla bilgi için bkz. [.NET Core 3,0 blog gönderisine kayan nokta ayrıştırma ve biçimlendirme geliştirmeleri](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) .</span><span class="sxs-lookup"><span data-stu-id="b2d3a-109">For more information, see the [Floating-point parsing and formatting improvements in .NET Core 3.0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) blog post.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="b2d3a-110">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="b2d3a-110">Version introduced</span></span>

<span data-ttu-id="b2d3a-111">3.0</span><span class="sxs-lookup"><span data-stu-id="b2d3a-111">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="b2d3a-112">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="b2d3a-112">Recommended action</span></span>

<span data-ttu-id="b2d3a-113">.NET Core 3,0 Web günlüğü gönderisine ilişkin [kayan nokta ayrıştırma ve biçimlendirme geliştirmelerinden](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) oluşan "var olan koda etkisi" bölümünde, .net Core 2,2 uygulamalarıyla karşılaştırıldığında bir davranış değişikliği gözlemlerseniz kodunuzda değişiklik yapılması önerilir. Bu, istenen davranışı zorlamak için farklı bir standart veya özel biçim dizesi kullanmayı içerir.</span><span class="sxs-lookup"><span data-stu-id="b2d3a-113">The "Potential impact to existing code" section of the [Floating-point parsing and formatting improvements in .NET Core 3.0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) blog post suggests changes to your code if you observe a change of behavior when compared to .NET Core 2.2 applications Generally, this involves using a different standard or custom format string to enforce the desired behavior.</span></span> <span data-ttu-id="b2d3a-114">Bazı sonuçlar daha önceden yanlış olsaydı geçici bir çözüme sahip olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="b2d3a-114">Some results may not have a workaround if they were previously incorrect.</span></span>

#### <a name="category"></a><span data-ttu-id="b2d3a-115">Kategori</span><span class="sxs-lookup"><span data-stu-id="b2d3a-115">Category</span></span>

<span data-ttu-id="b2d3a-116">Core .NET kitaplıkları</span><span class="sxs-lookup"><span data-stu-id="b2d3a-116">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b2d3a-117">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="b2d3a-117">Affected APIs</span></span>

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
