---
ms.openlocfilehash: 8b70df0fb2072fd5243d9e46a4a20c22cc7fd677
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2020
ms.locfileid: "91607804"
---
### <a name="profiling-aspnet-mvc4-apps-can-lead-to-fatal-execution-engine-error"></a><span data-ttu-id="73489-101">Profil oluşturma ASP.NET MVC4 Apps önemli yürütme altyapısı hatasına neden olabilir</span><span class="sxs-lookup"><span data-stu-id="73489-101">Profiling ASP.NET MVC4 apps can lead to Fatal Execution Engine Error</span></span>

#### <a name="details"></a><span data-ttu-id="73489-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="73489-102">Details</span></span>

<span data-ttu-id="73489-103">NGEN/profile derlemeleri kullanılarak profil oluşturucular, bir ' önemli yürütme altyapısı özel durumu ile başlangıçtaki profili oluşturulmuş ASP.NET MVC4 uygulamalarını çökebilir</span><span class="sxs-lookup"><span data-stu-id="73489-103">Profilers using NGEN /Profile assemblies may crash profiled ASP.NET MVC4 applications on startup with a 'Fatal Execution Engine Exception'</span></span>

#### <a name="suggestion"></a><span data-ttu-id="73489-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="73489-104">Suggestion</span></span>

<span data-ttu-id="73489-105">Bu sorun .NET Framework 4.5.2 düzeltilmiştir.</span><span class="sxs-lookup"><span data-stu-id="73489-105">This issue is fixed in the .NET Framework 4.5.2.</span></span> <span data-ttu-id="73489-106">Alternatif olarak, profil oluşturucu kendi olay maskesini belirterek bu sorundan kaçınabilir <code>COR_PRF_DISABLE_ALL_NGEN_IMAGES</code> .</span><span class="sxs-lookup"><span data-stu-id="73489-106">Alternatively, the profiler may avoid this issue by specifying <code>COR_PRF_DISABLE_ALL_NGEN_IMAGES</code> in its event mask.</span></span>

| <span data-ttu-id="73489-107">Name</span><span class="sxs-lookup"><span data-stu-id="73489-107">Name</span></span>    | <span data-ttu-id="73489-108">Değer</span><span class="sxs-lookup"><span data-stu-id="73489-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="73489-109">Kapsam</span><span class="sxs-lookup"><span data-stu-id="73489-109">Scope</span></span>   |<span data-ttu-id="73489-110">Edge</span><span class="sxs-lookup"><span data-stu-id="73489-110">Edge</span></span>|
|<span data-ttu-id="73489-111">Sürüm</span><span class="sxs-lookup"><span data-stu-id="73489-111">Version</span></span>|<span data-ttu-id="73489-112">4,5</span><span class="sxs-lookup"><span data-stu-id="73489-112">4.5</span></span>|
|<span data-ttu-id="73489-113">Tür</span><span class="sxs-lookup"><span data-stu-id="73489-113">Type</span></span>|<span data-ttu-id="73489-114">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="73489-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="73489-115">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="73489-115">Affected APIs</span></span>

<span data-ttu-id="73489-116">API analizi aracılığıyla algılanamaz.</span><span class="sxs-lookup"><span data-stu-id="73489-116">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
