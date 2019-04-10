---
ms.openlocfilehash: a93fbbd787aa50f080337a6170cf8f56d0d24e31
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59236717"
---
### <a name="concurrentqueuettrypeek-can-return-an-erroneous-null-via-its-out-parameter"></a><span data-ttu-id="04894-101">ConcurrentQueue\<T >. TryPeek, out parametresinin hatalı bir null döndürebilir</span><span class="sxs-lookup"><span data-stu-id="04894-101">ConcurrentQueue\<T>.TryPeek can return an erroneous null via its out parameter</span></span>

|   |   |
|---|---|
|<span data-ttu-id="04894-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="04894-102">Details</span></span>|<span data-ttu-id="04894-103">Çok iş parçacıklı bazı senaryolarda <xref:System.Collections.Concurrent.ConcurrentQueue%601.TryPeek(%600@)?displayProperty=name> true döndürür ancak out parametresi (doğru baktı değeri) yerine null bir değerle doldurun.</span><span class="sxs-lookup"><span data-stu-id="04894-103">In some multi-threaded scenarios, <xref:System.Collections.Concurrent.ConcurrentQueue%601.TryPeek(%600@)?displayProperty=name> can return true, but populate the out parameter with a null value (instead of the correct, peeked value).</span></span>|
|<span data-ttu-id="04894-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="04894-104">Suggestion</span></span>|<span data-ttu-id="04894-105">.NET Framework 4.5.1 Bu sorun düzeltilmiştir.</span><span class="sxs-lookup"><span data-stu-id="04894-105">This issue is fixed in the .NET Framework 4.5.1.</span></span> <span data-ttu-id="04894-106">Bu çerçeve için yükseltme sorunu çözün.</span><span class="sxs-lookup"><span data-stu-id="04894-106">Upgrading to that Framework will solve the issue.</span></span>|
|<span data-ttu-id="04894-107">Kapsam</span><span class="sxs-lookup"><span data-stu-id="04894-107">Scope</span></span>|<span data-ttu-id="04894-108">Ana</span><span class="sxs-lookup"><span data-stu-id="04894-108">Major</span></span>|
|<span data-ttu-id="04894-109">Sürüm</span><span class="sxs-lookup"><span data-stu-id="04894-109">Version</span></span>|<span data-ttu-id="04894-110">4,5</span><span class="sxs-lookup"><span data-stu-id="04894-110">4.5</span></span>|
|<span data-ttu-id="04894-111">Tür</span><span class="sxs-lookup"><span data-stu-id="04894-111">Type</span></span>|<span data-ttu-id="04894-112">Çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="04894-112">Runtime</span></span>|
|<span data-ttu-id="04894-113">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="04894-113">Affected APIs</span></span>|<ul><li><xref:System.Collections.Concurrent.ConcurrentQueue%601.TryPeek(%600@)?displayProperty=nameWithType></li></ul>|
