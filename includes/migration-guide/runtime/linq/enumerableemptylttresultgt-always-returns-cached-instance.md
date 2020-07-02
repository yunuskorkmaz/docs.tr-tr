---
ms.openlocfilehash: 9131c91b34f4c24653dea37ea39af6be6e072287
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620633"
---
### <a name="enumerableemptylttresultgt-always-returns-cached-instance"></a><span data-ttu-id="90778-101">Sıralanabilir. boş &lt; TResult &gt; her zaman önbelleğe alınmış örnek döndürür</span><span class="sxs-lookup"><span data-stu-id="90778-101">Enumerable.Empty&lt;TResult&gt; always returns cached instance</span></span>

#### <a name="details"></a><span data-ttu-id="90778-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="90778-102">Details</span></span>

<span data-ttu-id="90778-103">.NET Framework 4,5 ' den başlayarak, <xref:System.Linq.Enumerable.Empty%60%601> her zaman önbelleğe alınmış bir iç örnek döndürür <xref:System.Collections.Generic.IEnumerable%601> . Daha önce, <xref:System.Linq.Enumerable.Empty%60%601> API çağrıldığında boş önbelleğe alma işlemi <xref:System.Collections.Generic.IEnumerable%601> yapılır, yani <xref:System.Linq.Enumerable.Empty%60%601> hızlı ve eşzamanlı olarak çağrılan bazı koşullarda, API 'ye yönelik farklı çağrılar için türün farklı örnekleri döndürülebilir.</span><span class="sxs-lookup"><span data-stu-id="90778-103">Beginning in .NET Framework 4.5, <xref:System.Linq.Enumerable.Empty%60%601> always returns a cached internal instance <xref:System.Collections.Generic.IEnumerable%601>.Previously, <xref:System.Linq.Enumerable.Empty%60%601> would cache an empty <xref:System.Collections.Generic.IEnumerable%601> at the time the API was called, meaning that in some conditions in which <xref:System.Linq.Enumerable.Empty%60%601> was called rapidly and concurrently, different instances of the type could be returned for different calls to the API.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="90778-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="90778-104">Suggestion</span></span>

<span data-ttu-id="90778-105">Önceki davranış belirleyici olmadığı için kodun bağımlı olması olası değildir.</span><span class="sxs-lookup"><span data-stu-id="90778-105">Because the previous behavior was non-deterministic, code is unlikely to depend on it.</span></span> <span data-ttu-id="90778-106">Ancak, boş numaralar karşılaştırılan ve bazen eşit olmayan bir şekilde bekleniyorsa, kullanmak yerine açık boş diziler oluşturulmalıdır ( <code>new T[0]</code> ) <xref:System.Linq.Enumerable.Empty%60%601> .</span><span class="sxs-lookup"><span data-stu-id="90778-106">However, in the unlikely case that empty enumerables are being compared and expected to sometimes be unequal, explicit empty arrays should be created (<code>new T[0]</code>) instead of using <xref:System.Linq.Enumerable.Empty%60%601>.</span></span>

| <span data-ttu-id="90778-107">Name</span><span class="sxs-lookup"><span data-stu-id="90778-107">Name</span></span>    | <span data-ttu-id="90778-108">Değer</span><span class="sxs-lookup"><span data-stu-id="90778-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="90778-109">Kapsam</span><span class="sxs-lookup"><span data-stu-id="90778-109">Scope</span></span>   |<span data-ttu-id="90778-110">Edge</span><span class="sxs-lookup"><span data-stu-id="90778-110">Edge</span></span>|
|<span data-ttu-id="90778-111">Sürüm</span><span class="sxs-lookup"><span data-stu-id="90778-111">Version</span></span>|<span data-ttu-id="90778-112">4,5</span><span class="sxs-lookup"><span data-stu-id="90778-112">4.5</span></span>|
|<span data-ttu-id="90778-113">Tür</span><span class="sxs-lookup"><span data-stu-id="90778-113">Type</span></span>|<span data-ttu-id="90778-114">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="90778-114">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="90778-115">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="90778-115">Affected APIs</span></span>

-<xref:System.Linq.Enumerable.Empty%60%601?displayProperty=nameWithType></li></ul>|
