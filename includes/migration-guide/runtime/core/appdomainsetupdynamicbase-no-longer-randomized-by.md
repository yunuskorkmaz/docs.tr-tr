---
ms.openlocfilehash: 08ad6fd4ccb6d5ddbbb4fa7ef1b325ce30689748
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621412"
---
### <a name="appdomainsetupdynamicbase-is-no-longer-randomized-by-userandomizedstringhashalgorithm"></a><span data-ttu-id="aa38d-101">AppDomainSetup. DynamicBase artık UseRandomizedStringHashAlgorithm tarafından rasgeleleştirilmedi</span><span class="sxs-lookup"><span data-stu-id="aa38d-101">AppDomainSetup.DynamicBase is no longer randomized by UseRandomizedStringHashAlgorithm</span></span>

#### <a name="details"></a><span data-ttu-id="aa38d-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="aa38d-102">Details</span></span>

<span data-ttu-id="aa38d-103">.NET Framework 4,6 ' dan önce, değeri <xref:System.AppDomainSetup.DynamicBase> uygulama etki alanları arasında rastgele hale getirilir veya UseRandomizedStringHashAlgorithm, uygulamanın yapılandırma dosyasında etkinleştirildiyse, süreçler arasında rasgeledir.</span><span class="sxs-lookup"><span data-stu-id="aa38d-103">Prior to the .NET Framework 4.6, the value of <xref:System.AppDomainSetup.DynamicBase> would be randomized between application domains, or between processes, if UseRandomizedStringHashAlgorithm was enabled in the app's config file.</span></span> <span data-ttu-id="aa38d-104">.NET Framework 4,6 ' den başlayarak, <xref:System.AppDomainSetup.DynamicBase> çalıştıran bir uygulamanın farklı örnekleri arasında ve farklı uygulama etki alanları arasında kararlı bir sonuç döndürür.</span><span class="sxs-lookup"><span data-stu-id="aa38d-104">Beginning in the .NET Framework 4.6, <xref:System.AppDomainSetup.DynamicBase> will return a stable result between different instances of an app running, and between different app domains.</span></span> <span data-ttu-id="aa38d-105">Dinamik tabanlar farklı uygulamalar için hala farklılık gösterir; Bu değişiklik yalnızca aynı uygulamanın farklı örneklerinin rastgele adlandırma öğesini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="aa38d-105">Dynamic bases will still differ for different apps; this change only removes the random naming element for different instances of the same app.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="aa38d-106">Öneri</span><span class="sxs-lookup"><span data-stu-id="aa38d-106">Suggestion</span></span>

<span data-ttu-id="aa38d-107">Etkinleştirmenin rastgele hale gelemeyeceğini unutmayın <code>UseRandomizedStringHashAlgorithm</code> <xref:System.AppDomainSetup.DynamicBase> .</span><span class="sxs-lookup"><span data-stu-id="aa38d-107">Be aware that enabling <code>UseRandomizedStringHashAlgorithm</code> will not result in <xref:System.AppDomainSetup.DynamicBase> being randomized.</span></span> <span data-ttu-id="aa38d-108">Rastgele bir taban gerekliyse, bu API 'nin yerine uygulamanızın kodunda oluşturulması gerekir.</span><span class="sxs-lookup"><span data-stu-id="aa38d-108">If a random base is needed, it must be produced in your app's code rather than via this API.</span></span>

| <span data-ttu-id="aa38d-109">Name</span><span class="sxs-lookup"><span data-stu-id="aa38d-109">Name</span></span>    | <span data-ttu-id="aa38d-110">Değer</span><span class="sxs-lookup"><span data-stu-id="aa38d-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="aa38d-111">Kapsam</span><span class="sxs-lookup"><span data-stu-id="aa38d-111">Scope</span></span>   |<span data-ttu-id="aa38d-112">Edge</span><span class="sxs-lookup"><span data-stu-id="aa38d-112">Edge</span></span>|
|<span data-ttu-id="aa38d-113">Sürüm</span><span class="sxs-lookup"><span data-stu-id="aa38d-113">Version</span></span>|<span data-ttu-id="aa38d-114">4.6</span><span class="sxs-lookup"><span data-stu-id="aa38d-114">4.6</span></span>|
|<span data-ttu-id="aa38d-115">Tür</span><span class="sxs-lookup"><span data-stu-id="aa38d-115">Type</span></span>|<span data-ttu-id="aa38d-116">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="aa38d-116">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="aa38d-117">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="aa38d-117">Affected APIs</span></span>

-<xref:System.AppDomainSetup.DynamicBase?displayProperty=nameWithType></li></ul>|
