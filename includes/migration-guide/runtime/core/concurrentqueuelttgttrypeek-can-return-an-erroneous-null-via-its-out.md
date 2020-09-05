---
ms.openlocfilehash: 004e2d1883b631e88ab5e164b1120c3b081b7041
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497121"
---
### <a name="concurrentqueuelttgttrypeek-can-return-an-erroneous-null-via-its-out-parameter"></a><span data-ttu-id="6a77a-101">ConcurrentQueue &lt; T &gt; . Trtypeınfo ek, out parametresi aracılığıyla hatalı bir null döndürebilir</span><span class="sxs-lookup"><span data-stu-id="6a77a-101">ConcurrentQueue&lt;T&gt;.TryPeek can return an erroneous null via its out parameter</span></span>

#### <a name="details"></a><span data-ttu-id="6a77a-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="6a77a-102">Details</span></span>

<span data-ttu-id="6a77a-103">Çok iş parçacıklı senaryolarda, <xref:System.Collections.Concurrent.ConcurrentQueue%601.TryPeek(%600@)?displayProperty=fullName> true döndürebilir, ancak out parametresini boş bir değerle (doğru, atılamıyor değeri yerine) doldurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6a77a-103">In some multi-threaded scenarios, <xref:System.Collections.Concurrent.ConcurrentQueue%601.TryPeek(%600@)?displayProperty=fullName> can return true, but populate the out parameter with a null value (instead of the correct, peeked value).</span></span>

#### <a name="suggestion"></a><span data-ttu-id="6a77a-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="6a77a-104">Suggestion</span></span>

<span data-ttu-id="6a77a-105">Bu sorun .NET Framework 4.5.1 düzeltilmiştir.</span><span class="sxs-lookup"><span data-stu-id="6a77a-105">This issue is fixed in the .NET Framework 4.5.1.</span></span> <span data-ttu-id="6a77a-106">Bu çerçeveye yükseltmek sorunu çözmeyecektir.</span><span class="sxs-lookup"><span data-stu-id="6a77a-106">Upgrading to that Framework will solve the issue.</span></span>

| <span data-ttu-id="6a77a-107">Name</span><span class="sxs-lookup"><span data-stu-id="6a77a-107">Name</span></span>    | <span data-ttu-id="6a77a-108">Değer</span><span class="sxs-lookup"><span data-stu-id="6a77a-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="6a77a-109">Kapsam</span><span class="sxs-lookup"><span data-stu-id="6a77a-109">Scope</span></span>   |<span data-ttu-id="6a77a-110">Ana</span><span class="sxs-lookup"><span data-stu-id="6a77a-110">Major</span></span>|
|<span data-ttu-id="6a77a-111">Sürüm</span><span class="sxs-lookup"><span data-stu-id="6a77a-111">Version</span></span>|<span data-ttu-id="6a77a-112">4,5</span><span class="sxs-lookup"><span data-stu-id="6a77a-112">4.5</span></span>|
|<span data-ttu-id="6a77a-113">Tür</span><span class="sxs-lookup"><span data-stu-id="6a77a-113">Type</span></span>|<span data-ttu-id="6a77a-114">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="6a77a-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="6a77a-115">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="6a77a-115">Affected APIs</span></span>

- <xref:System.Collections.Concurrent.ConcurrentQueue%601.TryPeek(%600@)?displayProperty=nameWithType>

<!--

#### Affected APIs

- ``M:System.Collections.Concurrent.ConcurrentQueue`1.TryPeek(`0@)``

-->
