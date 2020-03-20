---
ms.openlocfilehash: 439a4976482639cd2e4e17315ec1a53ca54aa477
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67803267"
---
### <a name="profiling-aspnet-mvc4-apps-can-lead-to-fatal-execution-engine-error"></a><span data-ttu-id="58ad0-101">MVC4 uygulamaları ASP.Net profil oluşturma Ölümcül Yürütme Motoru Hatasına yol açabilir</span><span class="sxs-lookup"><span data-stu-id="58ad0-101">Profiling ASP.Net MVC4 apps can lead to Fatal Execution Engine Error</span></span>

|   |   |
|---|---|
|<span data-ttu-id="58ad0-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="58ad0-102">Details</span></span>|<span data-ttu-id="58ad0-103">NGEN /Profil montajları kullanan profilciler, başlangıç ASP.NET MVC4 uygulamalarında profillenmiş olarak 'Fatal Execution Engine Exception' ile çökebilir</span><span class="sxs-lookup"><span data-stu-id="58ad0-103">Profilers using NGEN /Profile assemblies may crash profiled ASP.NET MVC4 applications on startup with a 'Fatal Execution Engine Exception'</span></span>|
|<span data-ttu-id="58ad0-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="58ad0-104">Suggestion</span></span>|<span data-ttu-id="58ad0-105">Bu sorun .NET Framework 4.5.2'de giderilmiştir.</span><span class="sxs-lookup"><span data-stu-id="58ad0-105">This issue is fixed in the .NET Framework 4.5.2.</span></span> <span data-ttu-id="58ad0-106">Alternatif olarak, profil oluşturucu olay maskesini belirterek <code>COR_PRF_DISABLE_ALL_NGEN_IMAGES</code> bu sorunu önleyebilir.</span><span class="sxs-lookup"><span data-stu-id="58ad0-106">Alternatively, the profiler may avoid this issue by specifying <code>COR_PRF_DISABLE_ALL_NGEN_IMAGES</code> in its event mask.</span></span>|
|<span data-ttu-id="58ad0-107">Kapsam</span><span class="sxs-lookup"><span data-stu-id="58ad0-107">Scope</span></span>|<span data-ttu-id="58ad0-108">Edge</span><span class="sxs-lookup"><span data-stu-id="58ad0-108">Edge</span></span>|
|<span data-ttu-id="58ad0-109">Sürüm</span><span class="sxs-lookup"><span data-stu-id="58ad0-109">Version</span></span>|<span data-ttu-id="58ad0-110">4,5</span><span class="sxs-lookup"><span data-stu-id="58ad0-110">4.5</span></span>|
|<span data-ttu-id="58ad0-111">Tür</span><span class="sxs-lookup"><span data-stu-id="58ad0-111">Type</span></span>|<span data-ttu-id="58ad0-112">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="58ad0-112">Runtime</span></span>|
