---
ms.openlocfilehash: 935d9b2368ea4a0eeca7943dcbd584d24d2a6633
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721249"
---
### <a name="floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception"></a><span data-ttu-id="8e896-101">Kayan nokta ayrıştırma işlemleri artık başarısız olmaz veya bir OverflowException oluşturmaz</span><span class="sxs-lookup"><span data-stu-id="8e896-101">Floating-point parsing operations no longer fail or throw an OverflowException</span></span>

<span data-ttu-id="8e896-102">Kayan nokta ayrıştırma yöntemleri, <xref:System.OverflowException> `false` sayısal değeri <xref:System.Single> veya kayan nokta türü aralığının dışında olan bir dizeyi ayrıştırdıklarında artık bir veya döndürmez <xref:System.Double> .</span><span class="sxs-lookup"><span data-stu-id="8e896-102">The floating-point parsing methods no longer throw an <xref:System.OverflowException> or return `false` when they parse a string whose numeric value is outside the range of the <xref:System.Single> or <xref:System.Double> floating-point type.</span></span>

#### <a name="change-description"></a><span data-ttu-id="8e896-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="8e896-103">Change description</span></span>

<span data-ttu-id="8e896-104">.NET Core 2,2 ve önceki sürümlerinde, <xref:System.Double.Parse%2A?displayProperty=nameWithType> ve yöntemleri kendi <xref:System.Single.Parse%2A?displayProperty=nameWithType> <xref:System.OverflowException> türü aralığının dışında bir değer oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8e896-104">In .NET Core 2.2 and earlier versions, the <xref:System.Double.Parse%2A?displayProperty=nameWithType> and <xref:System.Single.Parse%2A?displayProperty=nameWithType> methods throw an <xref:System.OverflowException> for values that outside the range of their respective type.</span></span> <span data-ttu-id="8e896-105"><xref:System.Double.TryParse%2A?displayProperty=nameWithType>Ve <xref:System.Single.TryParse%2A?displayProperty=nameWithType> yöntemleri, `false` Aralık dışı sayısal değerlerin dize temsillerine yönelik döndürülür.</span><span class="sxs-lookup"><span data-stu-id="8e896-105">The <xref:System.Double.TryParse%2A?displayProperty=nameWithType> and <xref:System.Single.TryParse%2A?displayProperty=nameWithType> methods return `false` for the string representations of out-of-range numeric values.</span></span>

<span data-ttu-id="8e896-106">.NET Core 3,0 ile başlayarak,, <xref:System.Double.Parse%2A?displayProperty=nameWithType> , <xref:System.Double.TryParse%2A?displayProperty=nameWithType> <xref:System.Single.Parse%2A?displayProperty=nameWithType> ve <xref:System.Single.TryParse%2A?displayProperty=nameWithType> yöntemleri Aralık dışı sayısal dizeler ayrıştırılırken artık başarısız olmaz.</span><span class="sxs-lookup"><span data-stu-id="8e896-106">Starting with .NET Core 3.0, the <xref:System.Double.Parse%2A?displayProperty=nameWithType>, <xref:System.Double.TryParse%2A?displayProperty=nameWithType>, <xref:System.Single.Parse%2A?displayProperty=nameWithType>, and <xref:System.Single.TryParse%2A?displayProperty=nameWithType> methods no longer fail when parsing out-of-range numeric strings.</span></span> <span data-ttu-id="8e896-107">Bunun yerine, <xref:System.Double> ayrıştırma yöntemleri <xref:System.Double.PositiveInfinity?displayProperty=nameWithType> , aşan değerler için döndürülür <xref:System.Double.MaxValue?displayProperty=nameWithType> ve ' <xref:System.Double.NegativeInfinity?displayProperty=nameWithType> den küçük değerler için geri döner <xref:System.Double.MinValue?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="8e896-107">Instead, the <xref:System.Double> parsing methods return <xref:System.Double.PositiveInfinity?displayProperty=nameWithType> for values that exceed <xref:System.Double.MaxValue?displayProperty=nameWithType>, and they return <xref:System.Double.NegativeInfinity?displayProperty=nameWithType> for values that are less than <xref:System.Double.MinValue?displayProperty=nameWithType>.</span></span> <span data-ttu-id="8e896-108">Benzer şekilde, <xref:System.Single> ayrıştırma yöntemleri <xref:System.Single.PositiveInfinity?displayProperty=nameWithType> , aşan değerler için döndürülür <xref:System.Single.MaxValue?displayProperty=nameWithType> ve ' <xref:System.Single.NegativeInfinity?displayProperty=nameWithType> den küçük değerler için geri döner <xref:System.Single.MinValue?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="8e896-108">Similarly, the <xref:System.Single> parsing methods return <xref:System.Single.PositiveInfinity?displayProperty=nameWithType> for values that exceed <xref:System.Single.MaxValue?displayProperty=nameWithType>, and they return <xref:System.Single.NegativeInfinity?displayProperty=nameWithType> for values that are less than <xref:System.Single.MinValue?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="8e896-109">Bu değişiklik, geliştirilmiş IEEE 754:2008 uyumluluğu için yapılmıştır.</span><span class="sxs-lookup"><span data-stu-id="8e896-109">This change was made for improved IEEE 754:2008 compliance.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="8e896-110">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="8e896-110">Version introduced</span></span>

<span data-ttu-id="8e896-111">3.0</span><span class="sxs-lookup"><span data-stu-id="8e896-111">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="8e896-112">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="8e896-112">Recommended action</span></span>

<span data-ttu-id="8e896-113">Bu değişiklik, kodunuzun ikisini de iki şekilde etkileyebilir:</span><span class="sxs-lookup"><span data-stu-id="8e896-113">This change can affect your code in either of two ways:</span></span>

- <span data-ttu-id="8e896-114">Kodunuz, <xref:System.OverflowException> bir taşma oluştuğunda yürütülmesi için işleyicisine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="8e896-114">Your code depends on the handler for the <xref:System.OverflowException> to execute when an overflow occurs.</span></span> <span data-ttu-id="8e896-115">Bu durumda, `catch` ifadesini kaldırmalı ve gerekli kodu `If` , veya olup olmadığını test eden bir deyime yerleştirmeniz gerekir <xref:System.Double.IsInfinity%2A?displayProperty=nameWithType> <xref:System.Single.IsInfinity%2A?displayProperty=nameWithType> `true` .</span><span class="sxs-lookup"><span data-stu-id="8e896-115">In this case, you should remove the `catch` statement and place any necessary code in an `If` statement that tests whether <xref:System.Double.IsInfinity%2A?displayProperty=nameWithType> or <xref:System.Single.IsInfinity%2A?displayProperty=nameWithType> is `true`.</span></span>

- <span data-ttu-id="8e896-116">Kodunuz, kayan nokta değerlerinin değil olduğunu varsayar `Infinity` .</span><span class="sxs-lookup"><span data-stu-id="8e896-116">Your code assumes that floating-point values are not `Infinity`.</span></span> <span data-ttu-id="8e896-117">Bu durumda, ve ' ın kayan nokta değerlerini denetlemek için gerekli kodu eklemelisiniz `PositiveInfinity` `NegativeInfinity` .</span><span class="sxs-lookup"><span data-stu-id="8e896-117">In this case, you should add the necessary code to check for floating-point values of `PositiveInfinity` and `NegativeInfinity`.</span></span>

#### <a name="category"></a><span data-ttu-id="8e896-118">Kategori</span><span class="sxs-lookup"><span data-stu-id="8e896-118">Category</span></span>

<span data-ttu-id="8e896-119">Core .NET kitaplıkları</span><span class="sxs-lookup"><span data-stu-id="8e896-119">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="8e896-120">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="8e896-120">Affected APIs</span></span>

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
