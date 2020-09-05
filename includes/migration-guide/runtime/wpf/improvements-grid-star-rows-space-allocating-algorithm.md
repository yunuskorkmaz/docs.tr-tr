---
ms.openlocfilehash: 415eb1960c20fb662469e126560d6f366309eb0d
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497458"
---
### <a name="improvements-to-grid-star-rows-space-allocating-algorithm"></a><span data-ttu-id="e410e-101">Kılavuz yıldıza yönelik iyileştirmeler-satırlar alan ayırma algoritması</span><span class="sxs-lookup"><span data-stu-id="e410e-101">Improvements to Grid star-rows space allocating algorithm</span></span>

#### <a name="details"></a><span data-ttu-id="e410e-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="e410e-102">Details</span></span>

<span data-ttu-id="e410e-103">.NET Framework 4,7 ' de tanıtılan bir hata, [boyutları ayırma algoritmasında](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-grid-allocation-of-space-to-star-columns.md)düzeltildi) <xref:System.Windows.Controls.Grid> .</span><span class="sxs-lookup"><span data-stu-id="e410e-103">Fixed a bug in the [algorithm for allocating sizes to](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-grid-allocation-of-space-to-star-columns.md)) in a <xref:System.Windows.Controls.Grid> introduced in .NET Framework 4.7.</span></span>  <span data-ttu-id="e410e-104">Boş satırlar içeren bir ızgara gibi bazı durumlarda, <code>Height=&quot;Auto&quot;</code> satırlar yanlış konuma düzenleniyordu, muhtemelen ızgara dışında.</span><span class="sxs-lookup"><span data-stu-id="e410e-104">In some cases, such as a Grid with <code>Height=&quot;Auto&quot;</code> containing empty rows, rows were arranged at the wrong position, possibly outside the Grid altogether.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="e410e-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="e410e-105">Suggestion</span></span>

<span data-ttu-id="e410e-106">Uygulamanın bu değişikliklerden faydalanabilir olması için .NET Framework 4,8 veya sonraki bir sürümde çalışmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e410e-106">In order for the application to benefit from these changes, it must run on the .NET Framework 4.8 or later.</span></span>

| <span data-ttu-id="e410e-107">Name</span><span class="sxs-lookup"><span data-stu-id="e410e-107">Name</span></span>    | <span data-ttu-id="e410e-108">Değer</span><span class="sxs-lookup"><span data-stu-id="e410e-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="e410e-109">Kapsam</span><span class="sxs-lookup"><span data-stu-id="e410e-109">Scope</span></span>   |<span data-ttu-id="e410e-110">Ana</span><span class="sxs-lookup"><span data-stu-id="e410e-110">Major</span></span>|
|<span data-ttu-id="e410e-111">Sürüm</span><span class="sxs-lookup"><span data-stu-id="e410e-111">Version</span></span>|<span data-ttu-id="e410e-112">4,8</span><span class="sxs-lookup"><span data-stu-id="e410e-112">4.8</span></span>|
|<span data-ttu-id="e410e-113">Tür</span><span class="sxs-lookup"><span data-stu-id="e410e-113">Type</span></span>|<span data-ttu-id="e410e-114">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="e410e-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="e410e-115">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="e410e-115">Affected APIs</span></span>

<span data-ttu-id="e410e-116">API analizi aracılığıyla algılanamaz.</span><span class="sxs-lookup"><span data-stu-id="e410e-116">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
