---
ms.openlocfilehash: 192873aa5069aa4f96a18716afb066c80b223e29
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002451"
---
### <a name="floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception"></a><span data-ttu-id="664cd-101">Kayan nokta ayrıştırma işlemleri artık başarısız olmaz veya bir OverflowException oluşturmaz</span><span class="sxs-lookup"><span data-stu-id="664cd-101">Floating-point parsing operations no longer fail or throw an OverflowException</span></span>

<span data-ttu-id="664cd-102">Kayan nokta ayrıştırma yöntemleri artık, sayısal değeri <xref:System.Single> veya <xref:System.Double> kayan nokta türü aralığının dışında olan bir dizeyi ayrıştırdıklarında <xref:System.OverflowException> ' ı oluşturmaz veya `false` ' i döndürmez.</span><span class="sxs-lookup"><span data-stu-id="664cd-102">The floating-point parsing methods no longer throw an <xref:System.OverflowException> or return `false` when they parse a string whose numeric value is outside the range of the <xref:System.Single> or <xref:System.Double> floating-point type.</span></span>

#### <a name="change-description"></a><span data-ttu-id="664cd-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="664cd-103">Change description</span></span>

<span data-ttu-id="664cd-104">.NET Core 2,2 ve önceki sürümlerinde, <xref:System.Double.Parse%2A?displayProperty=nameWithType> ve <xref:System.Single.Parse%2A?displayProperty=nameWithType> yöntemleri, ilgili türünün aralığı dışında değerler için bir <xref:System.OverflowException> oluşturur.</span><span class="sxs-lookup"><span data-stu-id="664cd-104">In .NET Core 2.2 and earlier versions, the <xref:System.Double.Parse%2A?displayProperty=nameWithType> and <xref:System.Single.Parse%2A?displayProperty=nameWithType> methods throw an <xref:System.OverflowException> for values that outside the range of their respective type.</span></span> <span data-ttu-id="664cd-105">@No__t-0 ve <xref:System.Single.TryParse%2A?displayProperty=nameWithType> yöntemleri, Aralık dışı sayısal değerlerin dize temsilleri için `false` ' i döndürür.</span><span class="sxs-lookup"><span data-stu-id="664cd-105">The <xref:System.Double.TryParse%2A?displayProperty=nameWithType> and <xref:System.Single.TryParse%2A?displayProperty=nameWithType> methods return `false` for the string representations of out-of-range numeric values.</span></span>

<span data-ttu-id="664cd-106">.NET Core 3,0 ile başlayarak, Aralık dışı sayısal dizeler ayrıştırılırken <xref:System.Double.Parse%2A?displayProperty=nameWithType>, <xref:System.Double.TryParse%2A?displayProperty=nameWithType>, <xref:System.Single.Parse%2A?displayProperty=nameWithType> ve <xref:System.Single.TryParse%2A?displayProperty=nameWithType> yöntemleri artık başarısız olmaz.</span><span class="sxs-lookup"><span data-stu-id="664cd-106">Starting with .NET Core 3.0, the <xref:System.Double.Parse%2A?displayProperty=nameWithType>, <xref:System.Double.TryParse%2A?displayProperty=nameWithType>, <xref:System.Single.Parse%2A?displayProperty=nameWithType>, and <xref:System.Single.TryParse%2A?displayProperty=nameWithType> methods no longer fail when parsing out-of-range numeric strings.</span></span> <span data-ttu-id="664cd-107">Bunun yerine, <xref:System.Double> ayrıştırma yöntemleri <xref:System.Double.MaxValue?displayProperty=nameWithType> ' den fazla değerler için <xref:System.Double.PositiveInfinity?displayProperty=nameWithType> döndürür ve <xref:System.Double.MinValue?displayProperty=nameWithType> ' ten küçük değerler için <xref:System.Double.NegativeInfinity?displayProperty=nameWithType> ' ü döndürür.</span><span class="sxs-lookup"><span data-stu-id="664cd-107">Instead, the <xref:System.Double> parsing methods return <xref:System.Double.PositiveInfinity?displayProperty=nameWithType> for values that exceed <xref:System.Double.MaxValue?displayProperty=nameWithType>, and they return <xref:System.Double.NegativeInfinity?displayProperty=nameWithType> for values that are less than <xref:System.Double.MinValue?displayProperty=nameWithType>.</span></span> <span data-ttu-id="664cd-108">Benzer şekilde, <xref:System.Single> ayrıştırma yöntemleri <xref:System.Single.MaxValue?displayProperty=nameWithType> ' den fazla değerler için <xref:System.Single.PositiveInfinity?displayProperty=nameWithType> döndürür ve <xref:System.Single.MinValue?displayProperty=nameWithType> ' ten küçük değerler için <xref:System.Single.NegativeInfinity?displayProperty=nameWithType> ' ü döndürür.</span><span class="sxs-lookup"><span data-stu-id="664cd-108">Similarly, the <xref:System.Single> parsing methods return <xref:System.Single.PositiveInfinity?displayProperty=nameWithType> for values that exceed <xref:System.Single.MaxValue?displayProperty=nameWithType>, and they return <xref:System.Single.NegativeInfinity?displayProperty=nameWithType> for values that are less than <xref:System.Single.MinValue?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="664cd-109">Bu değişiklik, geliştirilmiş IEEE 754:2008 uyumluluğu için yapılmıştır.</span><span class="sxs-lookup"><span data-stu-id="664cd-109">This change was made for improved IEEE 754:2008 compliance.</span></span> 

#### <a name="version-introduced"></a><span data-ttu-id="664cd-110">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="664cd-110">Version introduced</span></span>

<span data-ttu-id="664cd-111">3.0</span><span class="sxs-lookup"><span data-stu-id="664cd-111">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="664cd-112">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="664cd-112">Recommended action</span></span>

<span data-ttu-id="664cd-113">Bu değişiklik, kodunuzun ikisini de iki şekilde etkileyebilir:</span><span class="sxs-lookup"><span data-stu-id="664cd-113">This change can affect your code in either of two ways:</span></span>

- <span data-ttu-id="664cd-114">Kodunuz, bir taşma oluştuğunda yürütülecek <xref:System.OverflowException> işleyicisine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="664cd-114">Your code depends on the handler for the <xref:System.OverflowException> to execute when an overflow occurs.</span></span> <span data-ttu-id="664cd-115">Bu durumda, `catch` ifadesini kaldırmalı ve gerekli kodu <xref:System.Double.IsInfinity%2A?displayProperty=nameWithType> veya <xref:System.Single.IsInfinity%2A?displayProperty=nameWithType> `true` olup olmadığını test eden bir `If` ifadesine yerleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="664cd-115">In this case, you should remove the `catch` statement and place any necessary code in an `If` statement that tests whether <xref:System.Double.IsInfinity%2A?displayProperty=nameWithType> or <xref:System.Single.IsInfinity%2A?displayProperty=nameWithType> is `true`.</span></span>

- <span data-ttu-id="664cd-116">Kodunuz, kayan nokta değerlerinin `Infinity` olmadığı varsayılır.</span><span class="sxs-lookup"><span data-stu-id="664cd-116">Your code assumes that floating-point values are not `Infinity`.</span></span> <span data-ttu-id="664cd-117">Bu durumda, `PositiveInfinity` ve `NegativeInfinity` ' in kayan nokta değerlerini denetlemek için gerekli kodu eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="664cd-117">In this case, you should add the necessary code to check for floating-point values of `PositiveInfinity` and `NegativeInfinity`.</span></span>

#### <a name="category"></a><span data-ttu-id="664cd-118">Kategori</span><span class="sxs-lookup"><span data-stu-id="664cd-118">Category</span></span>

<span data-ttu-id="664cd-119">CoreFx</span><span class="sxs-lookup"><span data-stu-id="664cd-119">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="664cd-120">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="664cd-120">Affected APIs</span></span>

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
