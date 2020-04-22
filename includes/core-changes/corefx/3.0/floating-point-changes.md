---
ms.openlocfilehash: 22dbb1e982f83687a9e0eb288ed72c78c676db77
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021634"
---
### <a name="floating-point-formatting-and-parsing-behavior-changed"></a><span data-ttu-id="10051-101">Kayan nokta biçimlendirme ve ayrıştma davranışı değiştirildi</span><span class="sxs-lookup"><span data-stu-id="10051-101">Floating-point formatting and parsing behavior changed</span></span>

<span data-ttu-id="10051-102">Kayan nokta ayrıştırma ve biçimlendirme <xref:System.Single> davranışı (ve <xref:System.Double> türleri tarafından) artık IEEE uyumludur.</span><span class="sxs-lookup"><span data-stu-id="10051-102">Floating point parsing and formatting behavior (by the <xref:System.Double> and <xref:System.Single> types) are now IEEE-compliant.</span></span>

#### <a name="change-description"></a><span data-ttu-id="10051-103">Açıklamayı değiştir</span><span class="sxs-lookup"><span data-stu-id="10051-103">Change description</span></span>

<span data-ttu-id="10051-104">.NET Core 2.2 <xref:System.Double.ToString%2A?displayProperty=nameWithType> ve önceki sürümlerde, biçimlendirme ve <xref:System.Double.Parse%2A?displayProperty=nameWithType> <xref:System.Double.TryParse%2A?displayProperty=nameWithType> <xref:System.Single.Parse%2A?displayProperty=nameWithType> <xref:System.Single.TryParse%2A?displayProperty=nameWithType> <xref:System.Single.ToString%2A?displayProperty=nameWithType>, , , , ile ayrışma ve IEEE uyumlu değildir.</span><span class="sxs-lookup"><span data-stu-id="10051-104">In .NET Core 2.2 and earlier versions, formatting with <xref:System.Double.ToString%2A?displayProperty=nameWithType> and <xref:System.Single.ToString%2A?displayProperty=nameWithType>, and parsing with <xref:System.Double.Parse%2A?displayProperty=nameWithType>, <xref:System.Double.TryParse%2A?displayProperty=nameWithType>, <xref:System.Single.Parse%2A?displayProperty=nameWithType>, and <xref:System.Single.TryParse%2A?displayProperty=nameWithType> are not IEEE-compliant.</span></span> <span data-ttu-id="10051-105">Sonuç olarak, desteklenen herhangi bir standart veya özel biçim dizesiyle bir değerin gidiş dönüş olacağını garanti etmek mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="10051-105">As a result, it is impossible to guarantee that a value will roundtrip with any supported standard or custom format string.</span></span> <span data-ttu-id="10051-106">Bazı girişler için biçimlendirilmiş bir değeri ayrışdırma girişimi başarısız olabilir ve diğerleri için ayrıştı değer özgün değere eşit değildir.</span><span class="sxs-lookup"><span data-stu-id="10051-106">For some inputs, the attempt to parse a formatted value can fail, and for others, the parsed value doesn't equal the original value.</span></span>

<span data-ttu-id="10051-107">.NET Core 3.0 ile başlayan ayrışma ve biçimlendirme işlemleri IEEE 754 uyumlu.</span><span class="sxs-lookup"><span data-stu-id="10051-107">Starting with .NET Core 3.0, parsing and formatting operations are IEEE 754-compliant.</span></span> <span data-ttu-id="10051-108">Bu, .NET'teki kayan nokta türlerinin davranışının C# gibi IEEE uyumlu dillerinkiyle eşleşmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="10051-108">This ensures that the behavior of floating-point types in .NET matches that of IEEE-compliant languages such as C#.</span></span> <span data-ttu-id="10051-109">Daha fazla bilgi için [.NET Core 3.0 blog gönderisinde Kayan nokta ayrıştırma ve biçimlendirme geliştirmelerine](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) bakın.</span><span class="sxs-lookup"><span data-stu-id="10051-109">For more information, see the [Floating-point parsing and formatting improvements in .NET Core 3.0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) blog post.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="10051-110">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="10051-110">Version introduced</span></span>

<span data-ttu-id="10051-111">3,0</span><span class="sxs-lookup"><span data-stu-id="10051-111">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="10051-112">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="10051-112">Recommended action</span></span>

<span data-ttu-id="10051-113">[.NET Core 3.0 blog gönderisinde Kayan nokta ayrıştırma ve biçimlendirme geliştirmeleri](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) bölümünün "Varolan koda olası etkisi" bölümü, .NET Core 2.2 uygulamalarına kıyasla davranış değişikliğini gözlemlerseniz kodunuzda değişiklikler önerir, bu, istenen davranışı uygulamak için farklı bir standart veya özel biçim dizesi kullanmayı içerir.</span><span class="sxs-lookup"><span data-stu-id="10051-113">The "Potential impact to existing code" section of the [Floating-point parsing and formatting improvements in .NET Core 3.0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) blog post suggests changes to your code if you observe a change of behavior when compared to .NET Core 2.2 applications Generally, this involves using a different standard or custom format string to enforce the desired behavior.</span></span> <span data-ttu-id="10051-114">Daha önce yanlış sayılsalardı, bazı sonuçların geçici çözüm eki olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="10051-114">Some results may not have a workaround if they were previously incorrect.</span></span>

#### <a name="category"></a><span data-ttu-id="10051-115">Kategori</span><span class="sxs-lookup"><span data-stu-id="10051-115">Category</span></span>

<span data-ttu-id="10051-116">Çekirdek .NET kitaplıkları</span><span class="sxs-lookup"><span data-stu-id="10051-116">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="10051-117">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="10051-117">Affected APIs</span></span>

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
