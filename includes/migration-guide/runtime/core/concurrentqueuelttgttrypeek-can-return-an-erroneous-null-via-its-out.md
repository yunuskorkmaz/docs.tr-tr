---
ms.openlocfilehash: 02a15f6b9c02002b60c568b9e1d871af49744092
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622143"
---
### <a name="concurrentqueuelttgttrypeek-can-return-an-erroneous-null-via-its-out-parameter"></a><span data-ttu-id="36c0c-101">ConcurrentQueue &lt; T &gt; . Trtypeınfo ek, out parametresi aracılığıyla hatalı bir null döndürebilir</span><span class="sxs-lookup"><span data-stu-id="36c0c-101">ConcurrentQueue&lt;T&gt;.TryPeek can return an erroneous null via its out parameter</span></span>

#### <a name="details"></a><span data-ttu-id="36c0c-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="36c0c-102">Details</span></span>

<span data-ttu-id="36c0c-103">Çok iş parçacıklı senaryolarda, <xref:System.Collections.Concurrent.ConcurrentQueue%601.TryPeek(%600@)?displayProperty=fullName> true döndürebilir, ancak out parametresini boş bir değerle (doğru, atılamıyor değeri yerine) doldurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="36c0c-103">In some multi-threaded scenarios, <xref:System.Collections.Concurrent.ConcurrentQueue%601.TryPeek(%600@)?displayProperty=fullName> can return true, but populate the out parameter with a null value (instead of the correct, peeked value).</span></span>

#### <a name="suggestion"></a><span data-ttu-id="36c0c-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="36c0c-104">Suggestion</span></span>

<span data-ttu-id="36c0c-105">Bu sorun .NET Framework 4.5.1 düzeltilmiştir.</span><span class="sxs-lookup"><span data-stu-id="36c0c-105">This issue is fixed in the .NET Framework 4.5.1.</span></span> <span data-ttu-id="36c0c-106">Bu çerçeveye yükseltmek sorunu çözmeyecektir.</span><span class="sxs-lookup"><span data-stu-id="36c0c-106">Upgrading to that Framework will solve the issue.</span></span>

| <span data-ttu-id="36c0c-107">Name</span><span class="sxs-lookup"><span data-stu-id="36c0c-107">Name</span></span>    | <span data-ttu-id="36c0c-108">Değer</span><span class="sxs-lookup"><span data-stu-id="36c0c-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="36c0c-109">Kapsam</span><span class="sxs-lookup"><span data-stu-id="36c0c-109">Scope</span></span>   |<span data-ttu-id="36c0c-110">Ana</span><span class="sxs-lookup"><span data-stu-id="36c0c-110">Major</span></span>|
|<span data-ttu-id="36c0c-111">Sürüm</span><span class="sxs-lookup"><span data-stu-id="36c0c-111">Version</span></span>|<span data-ttu-id="36c0c-112">4,5</span><span class="sxs-lookup"><span data-stu-id="36c0c-112">4.5</span></span>|
|<span data-ttu-id="36c0c-113">Tür</span><span class="sxs-lookup"><span data-stu-id="36c0c-113">Type</span></span>|<span data-ttu-id="36c0c-114">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="36c0c-114">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="36c0c-115">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="36c0c-115">Affected APIs</span></span>

-<xref:System.Collections.Concurrent.ConcurrentQueue%601.TryPeek(%600@)?displayProperty=nameWithType></li></ul>|
