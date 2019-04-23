---
ms.openlocfilehash: 891c29b731214fb0028e960256b79cfc267d86b9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59805254"
---
### <a name="deserialization-of-objects-across-appdomains-can-fail"></a><span data-ttu-id="40a6c-101">Uygulama etki alanları arasında nesneleri seri durumdan çıkarma başarısız olabilir</span><span class="sxs-lookup"><span data-stu-id="40a6c-101">Deserialization of objects across appdomains can fail</span></span>

|   |   |
|---|---|
|<span data-ttu-id="40a6c-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="40a6c-102">Details</span></span>|<span data-ttu-id="40a6c-103">Bazı durumlarda, iki veya daha fazla uygulama etki alanları ile farklı bir uygulama kullanıyorsa, uygulama temel dizini, uygulama etki alanları arasında nesnelerin mantıksal çağrı bağlamındaki seri durumdan çıkarılmaya çalışılırken bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="40a6c-103">In some cases, when an app uses two or more app domains with different application bases, trying to deserialize objects in the logical call context across app domains throws an exception.</span></span>|
|<span data-ttu-id="40a6c-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="40a6c-104">Suggestion</span></span>|<span data-ttu-id="40a6c-105">Bkz: [azaltma: Uygulama etki alanlarında nesneleri seri durumdan çıkarma](~/docs/framework/migration-guide/mitigation-deserialization-of-objects-across-app-domains.md)</span><span class="sxs-lookup"><span data-stu-id="40a6c-105">See [Mitigation: Deserialization of Objects Across App Domains](~/docs/framework/migration-guide/mitigation-deserialization-of-objects-across-app-domains.md)</span></span>|
|<span data-ttu-id="40a6c-106">Kapsam</span><span class="sxs-lookup"><span data-stu-id="40a6c-106">Scope</span></span>|<span data-ttu-id="40a6c-107">Kenar</span><span class="sxs-lookup"><span data-stu-id="40a6c-107">Edge</span></span>|
|<span data-ttu-id="40a6c-108">Sürüm</span><span class="sxs-lookup"><span data-stu-id="40a6c-108">Version</span></span>|<span data-ttu-id="40a6c-109">4.5.1</span><span class="sxs-lookup"><span data-stu-id="40a6c-109">4.5.1</span></span>|
|<span data-ttu-id="40a6c-110">Tür</span><span class="sxs-lookup"><span data-stu-id="40a6c-110">Type</span></span>|<span data-ttu-id="40a6c-111">Çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="40a6c-111">Runtime</span></span>|
