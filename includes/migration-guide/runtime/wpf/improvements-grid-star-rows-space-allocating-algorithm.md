---
ms.openlocfilehash: 62702de022656e45466a45f4150e518226a3fecc
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622093"
---
### <a name="improvements-to-grid-star-rows-space-allocating-algorithm"></a><span data-ttu-id="5f2a4-101">Kılavuz yıldıza yönelik iyileştirmeler-satırlar alan ayırma algoritması</span><span class="sxs-lookup"><span data-stu-id="5f2a4-101">Improvements to Grid star-rows space allocating algorithm</span></span>

#### <a name="details"></a><span data-ttu-id="5f2a4-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="5f2a4-102">Details</span></span>

<span data-ttu-id="5f2a4-103">.NET Framework 4,7 ' de tanıtılan bir hata, [boyutları ayırma algoritmasında](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-grid-allocation-of-space-to-star-columns.md)düzeltildi) <xref:System.Windows.Controls.Grid> .</span><span class="sxs-lookup"><span data-stu-id="5f2a4-103">Fixed a bug in the [algorithm for allocating sizes to](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-grid-allocation-of-space-to-star-columns.md)) in a <xref:System.Windows.Controls.Grid> introduced in .NET Framework 4.7.</span></span>  <span data-ttu-id="5f2a4-104">Boş satırlar içeren bir ızgara gibi bazı durumlarda, <code>Height=&quot;Auto&quot;</code> satırlar yanlış konuma düzenleniyordu, muhtemelen ızgara dışında.</span><span class="sxs-lookup"><span data-stu-id="5f2a4-104">In some cases, such as a Grid with <code>Height=&quot;Auto&quot;</code> containing empty rows, rows were arranged at the wrong position, possibly outside the Grid altogether.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="5f2a4-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="5f2a4-105">Suggestion</span></span>

<span data-ttu-id="5f2a4-106">Uygulamanın bu değişikliklerden faydalanabilir olması için .NET Framework 4,8 veya sonraki bir sürümde çalışmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5f2a4-106">In order for the application to benefit from these changes, it must run on the .NET Framework 4.8 or later.</span></span>

| <span data-ttu-id="5f2a4-107">Name</span><span class="sxs-lookup"><span data-stu-id="5f2a4-107">Name</span></span>    | <span data-ttu-id="5f2a4-108">Değer</span><span class="sxs-lookup"><span data-stu-id="5f2a4-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="5f2a4-109">Kapsam</span><span class="sxs-lookup"><span data-stu-id="5f2a4-109">Scope</span></span>   |<span data-ttu-id="5f2a4-110">Ana</span><span class="sxs-lookup"><span data-stu-id="5f2a4-110">Major</span></span>|
|<span data-ttu-id="5f2a4-111">Sürüm</span><span class="sxs-lookup"><span data-stu-id="5f2a4-111">Version</span></span>|<span data-ttu-id="5f2a4-112">4,8</span><span class="sxs-lookup"><span data-stu-id="5f2a4-112">4.8</span></span>|
|<span data-ttu-id="5f2a4-113">Tür</span><span class="sxs-lookup"><span data-stu-id="5f2a4-113">Type</span></span>|<span data-ttu-id="5f2a4-114">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="5f2a4-114">Runtime</span></span>|
