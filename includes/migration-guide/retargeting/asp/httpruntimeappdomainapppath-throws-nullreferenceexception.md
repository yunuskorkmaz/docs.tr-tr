---
ms.openlocfilehash: e7154919d6a09a04e650d5546feb2ae6c6cc912f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234987"
---
### <a name="httpruntimeappdomainapppath-throws-a-nullreferenceexception"></a><span data-ttu-id="d47fd-101">NullReferenceException HttpRuntime.AppDomainAppPath oluşturur</span><span class="sxs-lookup"><span data-stu-id="d47fd-101">HttpRuntime.AppDomainAppPath Throws a NullReferenceException</span></span>

|   |   |
|---|---|
|<span data-ttu-id="d47fd-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="d47fd-102">Details</span></span>|<span data-ttu-id="d47fd-103">.NET Framework 4.6.2, çalışma zamanı oluşturur bir <code>T:System.NullReferenceException</code> alınırken bir <code>P:System.Web.HttpRuntime.AppDomainAppPath</code> null karakterleri içeren bir değer. .NET Framework 4.6.1 ve önceki sürümlerinde, çalışma zamanı oluşturur bir <code>T:System.ArgumentNullException</code>.</span><span class="sxs-lookup"><span data-stu-id="d47fd-103">In the .NET Framework 4.6.2, the runtime throws a <code>T:System.NullReferenceException</code> when retrieving a <code>P:System.Web.HttpRuntime.AppDomainAppPath</code> value that includes null characters.In the .NET Framework 4.6.1 and earlier versions, the runtime throws an <code>T:System.ArgumentNullException</code>.</span></span>|
|<span data-ttu-id="d47fd-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="d47fd-104">Suggestion</span></span>|<span data-ttu-id="d47fd-105">Bu değişiklik yanıt vermek için izleme birini yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="d47fd-105">You can do either of the follow to respond to this change:</span></span><ul><li><span data-ttu-id="d47fd-106">Tanıtıcı <code>T:System.NullReferenceException</code> uygulamanız .NET Framework 4.6.2 çalışıyorsa.</span><span class="sxs-lookup"><span data-stu-id="d47fd-106">Handle the <code>T:System.NullReferenceException</code> if you application is running on the .NET Framework 4.6.2.</span></span></li><li><span data-ttu-id="d47fd-107">Önceki davranış geri yükler ve oluşturur .NET Framework 4.7, yükseltme bir <code>T:System.ArgumentNullException</code>.</span><span class="sxs-lookup"><span data-stu-id="d47fd-107">Upgrade to the .NET Framework 4.7, which restores the previous behavior and throws an <code>T:System.ArgumentNullException</code>.</span></span></li></ul>|
|<span data-ttu-id="d47fd-108">Kapsam</span><span class="sxs-lookup"><span data-stu-id="d47fd-108">Scope</span></span>|<span data-ttu-id="d47fd-109">Kenar</span><span class="sxs-lookup"><span data-stu-id="d47fd-109">Edge</span></span>|
|<span data-ttu-id="d47fd-110">Sürüm</span><span class="sxs-lookup"><span data-stu-id="d47fd-110">Version</span></span>|<span data-ttu-id="d47fd-111">4.6.2</span><span class="sxs-lookup"><span data-stu-id="d47fd-111">4.6.2</span></span>|
|<span data-ttu-id="d47fd-112">Tür</span><span class="sxs-lookup"><span data-stu-id="d47fd-112">Type</span></span>|<span data-ttu-id="d47fd-113">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="d47fd-113">Retargeting</span></span>|
|<span data-ttu-id="d47fd-114">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="d47fd-114">Affected APIs</span></span>|<ul><li><xref:System.Web.HttpRuntime.AppDomainAppPath?displayProperty=nameWithType></li></ul>|
