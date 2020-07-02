---
ms.openlocfilehash: 9dada93c3330331064b7a944d97d61edb4dea299
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620580"
---
### <a name="listsort-algorithm-changed"></a><span data-ttu-id="35911-101">List. Sort algoritması değişti</span><span class="sxs-lookup"><span data-stu-id="35911-101">List.Sort algorithm changed</span></span>

#### <a name="details"></a><span data-ttu-id="35911-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="35911-102">Details</span></span>

<span data-ttu-id="35911-103">.NET Framework 4,5 ' den başlayarak, <xref:System.Collections.Generic.List%601?displayProperty=fullName> sıralama algoritması değişmiştir (bir hızlı sıralama yerine yönelik sıralaması olacak şekilde).</span><span class="sxs-lookup"><span data-stu-id="35911-103">Beginning in .NET Framework 4.5, <xref:System.Collections.Generic.List%601?displayProperty=fullName>'s sort algorithm has changed (to be an introspective sort instead of a quick sort).</span></span> <span data-ttu-id="35911-104"><xref:System.Collections.Generic.List%601?displayProperty=fullName>sıralaması hiçbir zaman kararlı olmamıştır, ancak bu değişiklik farklı senaryolara karşı tutarlı şekilde sıralama yapılmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="35911-104"><xref:System.Collections.Generic.List%601?displayProperty=fullName>'s sort has never been stable, but this change may cause different scenarios to sort in unstable ways.</span></span> <span data-ttu-id="35911-105">Bu, benzer öğelerin API 'nin sonraki çağrılarında farklı siparişlerde sıralabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="35911-105">That simply means that equivalent items may sort in different orders in subsequent calls of the API.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="35911-106">Öneri</span><span class="sxs-lookup"><span data-stu-id="35911-106">Suggestion</span></span>

<span data-ttu-id="35911-107">Eski sıralama algoritması da kararsız olduğundan (biraz farklı yollarla), her zaman belirli bir sırada sıralama için eşdeğer öğelere bağlı bir kod olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="35911-107">Because the old sort algorithm was also unstable (though in slightly different ways), there should be no code that depends on equivalent items always sorting in a particular order.</span></span> <span data-ttu-id="35911-108">Bu değere bağlı olan ve eski davranışa sahip olan kod örnekleri varsa, bu kod, öğeleri istenen sırada belirleyici olarak sıralayan bir karşılaştırıcı kullanmak için güncelleştirilmeleri gerekir.</span><span class="sxs-lookup"><span data-stu-id="35911-108">If there are instances of code depending upon that and being lucky with the old behavior, that code should be updated to use a comparer that will deterministically sort the items in the desired order.</span></span>

| <span data-ttu-id="35911-109">Name</span><span class="sxs-lookup"><span data-stu-id="35911-109">Name</span></span>    | <span data-ttu-id="35911-110">Değer</span><span class="sxs-lookup"><span data-stu-id="35911-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="35911-111">Kapsam</span><span class="sxs-lookup"><span data-stu-id="35911-111">Scope</span></span>   |<span data-ttu-id="35911-112">Geçirgen</span><span class="sxs-lookup"><span data-stu-id="35911-112">Transparent</span></span>|
|<span data-ttu-id="35911-113">Sürüm</span><span class="sxs-lookup"><span data-stu-id="35911-113">Version</span></span>|<span data-ttu-id="35911-114">4,5</span><span class="sxs-lookup"><span data-stu-id="35911-114">4.5</span></span>|
|<span data-ttu-id="35911-115">Tür</span><span class="sxs-lookup"><span data-stu-id="35911-115">Type</span></span>|<span data-ttu-id="35911-116">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="35911-116">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="35911-117">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="35911-117">Affected APIs</span></span>

-<xref:System.Collections.Generic.List%601.Sort?displayProperty=nameWithType></li><li><xref:System.Collections.Generic.List%601.Sort(System.Collections.Generic.IComparer{%600})?displayProperty=nameWithType></li><li><xref:System.Collections.Generic.List%601.Sort(System.Comparison{%600})?displayProperty=nameWithType></li><li><xref:System.Collections.Generic.List%601.Sort(System.Int32,System.Int32,System.Collections.Generic.IComparer{%600})?displayProperty=nameWithType></li></ul>|
