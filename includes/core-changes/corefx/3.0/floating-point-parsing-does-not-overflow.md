---
ms.openlocfilehash: 30580b3fde5b8a99862896bb7d31c6c4024f97e8
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74568235"
---
### <a name="floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception"></a><span data-ttu-id="65bd9-101">Kayan nokta ayrıştırma işlemleri artık başarısız olmaz veya bir OverflowException oluşturmaz</span><span class="sxs-lookup"><span data-stu-id="65bd9-101">Floating-point parsing operations no longer fail or throw an OverflowException</span></span>

<span data-ttu-id="65bd9-102">Kayan nokta ayrıştırma yöntemleri artık <xref:System.OverflowException> oluşturmaz veya sayısal değeri <xref:System.Single> veya <xref:System.Double> kayan nokta türünde olan bir dizeyi ayrıştırdıklarında `false` döndürmez.</span><span class="sxs-lookup"><span data-stu-id="65bd9-102">The floating-point parsing methods no longer throw an <xref:System.OverflowException> or return `false` when they parse a string whose numeric value is outside the range of the <xref:System.Single> or <xref:System.Double> floating-point type.</span></span>

#### <a name="change-description"></a><span data-ttu-id="65bd9-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="65bd9-103">Change description</span></span>

<span data-ttu-id="65bd9-104">.NET Core 2,2 ve önceki sürümlerinde, <xref:System.Double.Parse%2A?displayProperty=nameWithType> ve <xref:System.Single.Parse%2A?displayProperty=nameWithType> yöntemleri kendi tür aralığının dışında bir <xref:System.OverflowException> oluşturur.</span><span class="sxs-lookup"><span data-stu-id="65bd9-104">In .NET Core 2.2 and earlier versions, the <xref:System.Double.Parse%2A?displayProperty=nameWithType> and <xref:System.Single.Parse%2A?displayProperty=nameWithType> methods throw an <xref:System.OverflowException> for values that outside the range of their respective type.</span></span> <span data-ttu-id="65bd9-105"><xref:System.Double.TryParse%2A?displayProperty=nameWithType> ve <xref:System.Single.TryParse%2A?displayProperty=nameWithType> yöntemleri, Aralık dışı sayısal değerlerin dize temsilleri için `false` döndürür.</span><span class="sxs-lookup"><span data-stu-id="65bd9-105">The <xref:System.Double.TryParse%2A?displayProperty=nameWithType> and <xref:System.Single.TryParse%2A?displayProperty=nameWithType> methods return `false` for the string representations of out-of-range numeric values.</span></span>

<span data-ttu-id="65bd9-106">.NET Core 3,0 ile başlayarak, Aralık dışı sayısal dizeler ayrıştırılırken <xref:System.Double.Parse%2A?displayProperty=nameWithType>, <xref:System.Double.TryParse%2A?displayProperty=nameWithType>, <xref:System.Single.Parse%2A?displayProperty=nameWithType>ve <xref:System.Single.TryParse%2A?displayProperty=nameWithType> yöntemleri artık başarısız olmaz.</span><span class="sxs-lookup"><span data-stu-id="65bd9-106">Starting with .NET Core 3.0, the <xref:System.Double.Parse%2A?displayProperty=nameWithType>, <xref:System.Double.TryParse%2A?displayProperty=nameWithType>, <xref:System.Single.Parse%2A?displayProperty=nameWithType>, and <xref:System.Single.TryParse%2A?displayProperty=nameWithType> methods no longer fail when parsing out-of-range numeric strings.</span></span> <span data-ttu-id="65bd9-107">Bunun yerine, <xref:System.Double> ayrıştırma yöntemleri <xref:System.Double.MaxValue?displayProperty=nameWithType>aşan değerler için <xref:System.Double.PositiveInfinity?displayProperty=nameWithType> döndürür ve <xref:System.Double.MinValue?displayProperty=nameWithType>küçük değerler için <xref:System.Double.NegativeInfinity?displayProperty=nameWithType> döndürür.</span><span class="sxs-lookup"><span data-stu-id="65bd9-107">Instead, the <xref:System.Double> parsing methods return <xref:System.Double.PositiveInfinity?displayProperty=nameWithType> for values that exceed <xref:System.Double.MaxValue?displayProperty=nameWithType>, and they return <xref:System.Double.NegativeInfinity?displayProperty=nameWithType> for values that are less than <xref:System.Double.MinValue?displayProperty=nameWithType>.</span></span> <span data-ttu-id="65bd9-108">Benzer şekilde, <xref:System.Single> ayrıştırma yöntemleri <xref:System.Single.MaxValue?displayProperty=nameWithType>aşan değerler için <xref:System.Single.PositiveInfinity?displayProperty=nameWithType> döndürür ve <xref:System.Single.MinValue?displayProperty=nameWithType>küçük değerler için <xref:System.Single.NegativeInfinity?displayProperty=nameWithType> döndürür.</span><span class="sxs-lookup"><span data-stu-id="65bd9-108">Similarly, the <xref:System.Single> parsing methods return <xref:System.Single.PositiveInfinity?displayProperty=nameWithType> for values that exceed <xref:System.Single.MaxValue?displayProperty=nameWithType>, and they return <xref:System.Single.NegativeInfinity?displayProperty=nameWithType> for values that are less than <xref:System.Single.MinValue?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="65bd9-109">Bu değişiklik, geliştirilmiş IEEE 754:2008 uyumluluğu için yapılmıştır.</span><span class="sxs-lookup"><span data-stu-id="65bd9-109">This change was made for improved IEEE 754:2008 compliance.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="65bd9-110">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="65bd9-110">Version introduced</span></span>

<span data-ttu-id="65bd9-111">3.0</span><span class="sxs-lookup"><span data-stu-id="65bd9-111">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="65bd9-112">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="65bd9-112">Recommended action</span></span>

<span data-ttu-id="65bd9-113">Bu değişiklik, kodunuzun ikisini de iki şekilde etkileyebilir:</span><span class="sxs-lookup"><span data-stu-id="65bd9-113">This change can affect your code in either of two ways:</span></span>

- <span data-ttu-id="65bd9-114">Kodunuz, bir taşma oluştuğunda yürütülecek <xref:System.OverflowException> işleyicisine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="65bd9-114">Your code depends on the handler for the <xref:System.OverflowException> to execute when an overflow occurs.</span></span> <span data-ttu-id="65bd9-115">Bu durumda `catch` ifadesini kaldırmalı ve gerekli kodu <xref:System.Double.IsInfinity%2A?displayProperty=nameWithType> ya da <xref:System.Single.IsInfinity%2A?displayProperty=nameWithType> `true`olup olmadığını test eden bir `If` bildirimine yerleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="65bd9-115">In this case, you should remove the `catch` statement and place any necessary code in an `If` statement that tests whether <xref:System.Double.IsInfinity%2A?displayProperty=nameWithType> or <xref:System.Single.IsInfinity%2A?displayProperty=nameWithType> is `true`.</span></span>

- <span data-ttu-id="65bd9-116">Kodunuz, kayan nokta değerlerinin `Infinity`değil olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="65bd9-116">Your code assumes that floating-point values are not `Infinity`.</span></span> <span data-ttu-id="65bd9-117">Bu durumda, `PositiveInfinity` ve `NegativeInfinity`kayan nokta değerlerini denetlemek için gerekli kodu eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="65bd9-117">In this case, you should add the necessary code to check for floating-point values of `PositiveInfinity` and `NegativeInfinity`.</span></span>

#### <a name="category"></a><span data-ttu-id="65bd9-118">Kategori</span><span class="sxs-lookup"><span data-stu-id="65bd9-118">Category</span></span>

<span data-ttu-id="65bd9-119">CoreFx</span><span class="sxs-lookup"><span data-stu-id="65bd9-119">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="65bd9-120">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="65bd9-120">Affected APIs</span></span>

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
