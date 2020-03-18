---
ms.openlocfilehash: 30580b3fde5b8a99862896bb7d31c6c4024f97e8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74568235"
---
### <a name="floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception"></a><span data-ttu-id="af5fc-101">Kayan nokta ayrışma işlemleri artık başarısız veya bir OverflowException atmak</span><span class="sxs-lookup"><span data-stu-id="af5fc-101">Floating-point parsing operations no longer fail or throw an OverflowException</span></span>

<span data-ttu-id="af5fc-102">Kayan nokta ayrıştırma yöntemleri, <xref:System.OverflowException> sayısal `false` değeri <xref:System.Single> veya <xref:System.Double> kayan nokta türünün aralığının dışında olan bir dizeyi ayrıştırdıkları zaman artık bir veya geri dönüş atmaz.</span><span class="sxs-lookup"><span data-stu-id="af5fc-102">The floating-point parsing methods no longer throw an <xref:System.OverflowException> or return `false` when they parse a string whose numeric value is outside the range of the <xref:System.Single> or <xref:System.Double> floating-point type.</span></span>

#### <a name="change-description"></a><span data-ttu-id="af5fc-103">Açıklamayı değiştir</span><span class="sxs-lookup"><span data-stu-id="af5fc-103">Change description</span></span>

<span data-ttu-id="af5fc-104">.NET Core 2.2 ve önceki <xref:System.Double.Parse%2A?displayProperty=nameWithType> <xref:System.Single.Parse%2A?displayProperty=nameWithType> sürümlerinde, <xref:System.OverflowException> ve yöntemler kendi türüaralığının dışında olan değerler için bir değer atar.</span><span class="sxs-lookup"><span data-stu-id="af5fc-104">In .NET Core 2.2 and earlier versions, the <xref:System.Double.Parse%2A?displayProperty=nameWithType> and <xref:System.Single.Parse%2A?displayProperty=nameWithType> methods throw an <xref:System.OverflowException> for values that outside the range of their respective type.</span></span> <span data-ttu-id="af5fc-105">Ve <xref:System.Double.TryParse%2A?displayProperty=nameWithType> <xref:System.Single.TryParse%2A?displayProperty=nameWithType> yöntemler, `false` aralık dışı sayısal değerlerin dize gösterimleri için döndürür.</span><span class="sxs-lookup"><span data-stu-id="af5fc-105">The <xref:System.Double.TryParse%2A?displayProperty=nameWithType> and <xref:System.Single.TryParse%2A?displayProperty=nameWithType> methods return `false` for the string representations of out-of-range numeric values.</span></span>

<span data-ttu-id="af5fc-106">.NET Core 3.0 ile <xref:System.Double.Parse%2A?displayProperty=nameWithType> <xref:System.Double.TryParse%2A?displayProperty=nameWithType>başlayarak, aralık dışı sayısal dizeleri ayrıştirırken , , <xref:System.Single.Parse%2A?displayProperty=nameWithType>ve <xref:System.Single.TryParse%2A?displayProperty=nameWithType> yöntemler artık başarısız olmaz.</span><span class="sxs-lookup"><span data-stu-id="af5fc-106">Starting with .NET Core 3.0, the <xref:System.Double.Parse%2A?displayProperty=nameWithType>, <xref:System.Double.TryParse%2A?displayProperty=nameWithType>, <xref:System.Single.Parse%2A?displayProperty=nameWithType>, and <xref:System.Single.TryParse%2A?displayProperty=nameWithType> methods no longer fail when parsing out-of-range numeric strings.</span></span> <span data-ttu-id="af5fc-107">Bunun <xref:System.Double> yerine, ayrıştırma yöntemleri aşan <xref:System.Double.PositiveInfinity?displayProperty=nameWithType> <xref:System.Double.MaxValue?displayProperty=nameWithType>değerler <xref:System.Double.NegativeInfinity?displayProperty=nameWithType> için döndürür <xref:System.Double.MinValue?displayProperty=nameWithType>ve daha az olan değerler için geri döner.</span><span class="sxs-lookup"><span data-stu-id="af5fc-107">Instead, the <xref:System.Double> parsing methods return <xref:System.Double.PositiveInfinity?displayProperty=nameWithType> for values that exceed <xref:System.Double.MaxValue?displayProperty=nameWithType>, and they return <xref:System.Double.NegativeInfinity?displayProperty=nameWithType> for values that are less than <xref:System.Double.MinValue?displayProperty=nameWithType>.</span></span> <span data-ttu-id="af5fc-108">Benzer şekilde, <xref:System.Single> ayrıştırma <xref:System.Single.PositiveInfinity?displayProperty=nameWithType> yöntemleri aşan <xref:System.Single.MaxValue?displayProperty=nameWithType>değerler için <xref:System.Single.NegativeInfinity?displayProperty=nameWithType> döndürür ve <xref:System.Single.MinValue?displayProperty=nameWithType>daha az olan değerler için geri döner.</span><span class="sxs-lookup"><span data-stu-id="af5fc-108">Similarly, the <xref:System.Single> parsing methods return <xref:System.Single.PositiveInfinity?displayProperty=nameWithType> for values that exceed <xref:System.Single.MaxValue?displayProperty=nameWithType>, and they return <xref:System.Single.NegativeInfinity?displayProperty=nameWithType> for values that are less than <xref:System.Single.MinValue?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="af5fc-109">Bu değişiklik geliştirilmiş IEEE 754:2008 uyumluluğu için yapılmıştır.</span><span class="sxs-lookup"><span data-stu-id="af5fc-109">This change was made for improved IEEE 754:2008 compliance.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="af5fc-110">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="af5fc-110">Version introduced</span></span>

<span data-ttu-id="af5fc-111">3,0</span><span class="sxs-lookup"><span data-stu-id="af5fc-111">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="af5fc-112">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="af5fc-112">Recommended action</span></span>

<span data-ttu-id="af5fc-113">Bu değişiklik kodunuzu iki şekilde etkileyebilir:</span><span class="sxs-lookup"><span data-stu-id="af5fc-113">This change can affect your code in either of two ways:</span></span>

- <span data-ttu-id="af5fc-114">Kodunuz, taşma oluştuğunda <xref:System.OverflowException> yürütülmesi için işleyiciye bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="af5fc-114">Your code depends on the handler for the <xref:System.OverflowException> to execute when an overflow occurs.</span></span> <span data-ttu-id="af5fc-115">`catch` Bu durumda, deyimi kaldırmalı ve gerekli kodu `If` bir ifadeye <xref:System.Double.IsInfinity%2A?displayProperty=nameWithType> <xref:System.Single.IsInfinity%2A?displayProperty=nameWithType> yerleştirmeli ve bu kodu sınama. `true`</span><span class="sxs-lookup"><span data-stu-id="af5fc-115">In this case, you should remove the `catch` statement and place any necessary code in an `If` statement that tests whether <xref:System.Double.IsInfinity%2A?displayProperty=nameWithType> or <xref:System.Single.IsInfinity%2A?displayProperty=nameWithType> is `true`.</span></span>

- <span data-ttu-id="af5fc-116">Kodunuz kayan nokta değerlerinin `Infinity`.</span><span class="sxs-lookup"><span data-stu-id="af5fc-116">Your code assumes that floating-point values are not `Infinity`.</span></span> <span data-ttu-id="af5fc-117">Bu durumda, kayan nokta değerlerini denetlemek için gerekli kodu `PositiveInfinity` `NegativeInfinity`eklemeniz gerekir ve.</span><span class="sxs-lookup"><span data-stu-id="af5fc-117">In this case, you should add the necessary code to check for floating-point values of `PositiveInfinity` and `NegativeInfinity`.</span></span>

#### <a name="category"></a><span data-ttu-id="af5fc-118">Kategori</span><span class="sxs-lookup"><span data-stu-id="af5fc-118">Category</span></span>

<span data-ttu-id="af5fc-119">CoreFx</span><span class="sxs-lookup"><span data-stu-id="af5fc-119">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="af5fc-120">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="af5fc-120">Affected APIs</span></span>

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
