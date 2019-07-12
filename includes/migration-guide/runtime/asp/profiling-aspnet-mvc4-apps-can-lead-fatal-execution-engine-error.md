---
ms.openlocfilehash: 107b34c7bd26e1396e8a6638d6929c15de92b8e4
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67803267"
---
### <a name="profiling-aspnet-mvc4-apps-can-lead-to-fatal-execution-engine-error"></a><span data-ttu-id="086f0-101">ASP.Net MVC4 uygulamaları profil oluşturma için önemli yürütme altyapısı hata neden olabilir</span><span class="sxs-lookup"><span data-stu-id="086f0-101">Profiling ASP.Net MVC4 apps can lead to Fatal Execution Engine Error</span></span>

|   |   |
|---|---|
|<span data-ttu-id="086f0-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="086f0-102">Details</span></span>|<span data-ttu-id="086f0-103">NGEN/profile bütünleştirilmiş kodları kullanarak profil oluşturucular başlangıçta 'Önemli yürütme altyapısı bir özel durum' ile profili oluşturulmuş ASP.NET MVC4 uygulamalarının çökebilir</span><span class="sxs-lookup"><span data-stu-id="086f0-103">Profilers using NGEN /Profile assemblies may crash profiled ASP.NET MVC4 applications on startup with a 'Fatal Execution Engine Exception'</span></span>|
|<span data-ttu-id="086f0-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="086f0-104">Suggestion</span></span>|<span data-ttu-id="086f0-105">.NET Framework 4.5.2 Bu sorun düzeltilmiştir.</span><span class="sxs-lookup"><span data-stu-id="086f0-105">This issue is fixed in the .NET Framework 4.5.2.</span></span> <span data-ttu-id="086f0-106">Alternatif olarak, profil oluşturucu bu sorunu belirterek önlemek <code>COR_PRF_DISABLE_ALL_NGEN_IMAGES</code> kendi olay maske.</span><span class="sxs-lookup"><span data-stu-id="086f0-106">Alternatively, the profiler may avoid this issue by specifying <code>COR_PRF_DISABLE_ALL_NGEN_IMAGES</code> in its event mask.</span></span>|
|<span data-ttu-id="086f0-107">Kapsam</span><span class="sxs-lookup"><span data-stu-id="086f0-107">Scope</span></span>|<span data-ttu-id="086f0-108">Kenar</span><span class="sxs-lookup"><span data-stu-id="086f0-108">Edge</span></span>|
|<span data-ttu-id="086f0-109">Sürüm</span><span class="sxs-lookup"><span data-stu-id="086f0-109">Version</span></span>|<span data-ttu-id="086f0-110">4,5</span><span class="sxs-lookup"><span data-stu-id="086f0-110">4.5</span></span>|
|<span data-ttu-id="086f0-111">Tür</span><span class="sxs-lookup"><span data-stu-id="086f0-111">Type</span></span>|<span data-ttu-id="086f0-112">Çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="086f0-112">Runtime</span></span>|

