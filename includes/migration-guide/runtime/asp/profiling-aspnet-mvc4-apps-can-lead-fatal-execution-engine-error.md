---
ms.openlocfilehash: 439a4976482639cd2e4e17315ec1a53ca54aa477
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59805319"
---
### <a name="profiling-aspnet-mvc4-apps-can-lead-to-fatal-execution-engine-error"></a><span data-ttu-id="ceeff-101">ASP.Net MVC4 uygulamaları profil oluşturma için önemli yürütme altyapısı hata neden olabilir</span><span class="sxs-lookup"><span data-stu-id="ceeff-101">Profiling ASP.Net MVC4 apps can lead to Fatal Execution Engine Error</span></span>

|   |   |
|---|---|
|<span data-ttu-id="ceeff-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="ceeff-102">Details</span></span>|<span data-ttu-id="ceeff-103">NGEN/profile bütünleştirilmiş kodları kullanarak profil oluşturucular başlangıçta 'Önemli yürütme altyapısı bir özel durum' ile profili oluşturulmuş ASP.NET MVC4 uygulamalarının çökebilir</span><span class="sxs-lookup"><span data-stu-id="ceeff-103">Profilers using NGEN /Profile assemblies may crash profiled ASP.NET MVC4 applications on startup with a 'Fatal Execution Engine Exception'</span></span>|
|<span data-ttu-id="ceeff-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="ceeff-104">Suggestion</span></span>|<span data-ttu-id="ceeff-105">.NET Framework 4.5.2 Bu sorun düzeltilmiştir.</span><span class="sxs-lookup"><span data-stu-id="ceeff-105">This issue is fixed in the .NET Framework 4.5.2.</span></span> <span data-ttu-id="ceeff-106">Alternatif olarak, profil oluşturucu bu sorunu belirterek önlemek <code>COR_PRF_DISABLE_ALL_NGEN_IMAGES</code> kendi olay maske.</span><span class="sxs-lookup"><span data-stu-id="ceeff-106">Alternatively, the profiler may avoid this issue by specifying <code>COR_PRF_DISABLE_ALL_NGEN_IMAGES</code> in its event mask.</span></span>|
|<span data-ttu-id="ceeff-107">Kapsam</span><span class="sxs-lookup"><span data-stu-id="ceeff-107">Scope</span></span>|<span data-ttu-id="ceeff-108">Kenar</span><span class="sxs-lookup"><span data-stu-id="ceeff-108">Edge</span></span>|
|<span data-ttu-id="ceeff-109">Sürüm</span><span class="sxs-lookup"><span data-stu-id="ceeff-109">Version</span></span>|<span data-ttu-id="ceeff-110">4,5</span><span class="sxs-lookup"><span data-stu-id="ceeff-110">4.5</span></span>|
|<span data-ttu-id="ceeff-111">Tür</span><span class="sxs-lookup"><span data-stu-id="ceeff-111">Type</span></span>|<span data-ttu-id="ceeff-112">Çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="ceeff-112">Runtime</span></span>|
