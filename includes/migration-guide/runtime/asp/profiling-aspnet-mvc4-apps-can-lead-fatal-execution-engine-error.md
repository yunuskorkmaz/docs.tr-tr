---
ms.openlocfilehash: 2e13268d4983af5d2fdd6d12b4d9e67d61d07f3d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622132"
---
### <a name="profiling-aspnet-mvc4-apps-can-lead-to-fatal-execution-engine-error"></a><span data-ttu-id="7fd28-101">Profil oluşturma ASP.Net MVC4 Apps önemli yürütme altyapısı hatasına neden olabilir</span><span class="sxs-lookup"><span data-stu-id="7fd28-101">Profiling ASP.Net MVC4 apps can lead to Fatal Execution Engine Error</span></span>

#### <a name="details"></a><span data-ttu-id="7fd28-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="7fd28-102">Details</span></span>

<span data-ttu-id="7fd28-103">NGEN/profile derlemeleri kullanılarak profil oluşturucular, bir ' önemli yürütme altyapısı özel durumu ile başlangıçtaki profili oluşturulmuş ASP.NET MVC4 uygulamalarını çökebilir</span><span class="sxs-lookup"><span data-stu-id="7fd28-103">Profilers using NGEN /Profile assemblies may crash profiled ASP.NET MVC4 applications on startup with a 'Fatal Execution Engine Exception'</span></span>

#### <a name="suggestion"></a><span data-ttu-id="7fd28-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="7fd28-104">Suggestion</span></span>

<span data-ttu-id="7fd28-105">Bu sorun .NET Framework 4.5.2 düzeltilmiştir.</span><span class="sxs-lookup"><span data-stu-id="7fd28-105">This issue is fixed in the .NET Framework 4.5.2.</span></span> <span data-ttu-id="7fd28-106">Alternatif olarak, profil oluşturucu kendi olay maskesini belirterek bu sorundan kaçınabilir <code>COR_PRF_DISABLE_ALL_NGEN_IMAGES</code> .</span><span class="sxs-lookup"><span data-stu-id="7fd28-106">Alternatively, the profiler may avoid this issue by specifying <code>COR_PRF_DISABLE_ALL_NGEN_IMAGES</code> in its event mask.</span></span>

| <span data-ttu-id="7fd28-107">Name</span><span class="sxs-lookup"><span data-stu-id="7fd28-107">Name</span></span>    | <span data-ttu-id="7fd28-108">Değer</span><span class="sxs-lookup"><span data-stu-id="7fd28-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="7fd28-109">Kapsam</span><span class="sxs-lookup"><span data-stu-id="7fd28-109">Scope</span></span>   |<span data-ttu-id="7fd28-110">Edge</span><span class="sxs-lookup"><span data-stu-id="7fd28-110">Edge</span></span>|
|<span data-ttu-id="7fd28-111">Sürüm</span><span class="sxs-lookup"><span data-stu-id="7fd28-111">Version</span></span>|<span data-ttu-id="7fd28-112">4,5</span><span class="sxs-lookup"><span data-stu-id="7fd28-112">4.5</span></span>|
|<span data-ttu-id="7fd28-113">Tür</span><span class="sxs-lookup"><span data-stu-id="7fd28-113">Type</span></span>|<span data-ttu-id="7fd28-114">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="7fd28-114">Runtime</span></span>|
