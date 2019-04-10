---
ms.openlocfilehash: 891c29b731214fb0028e960256b79cfc267d86b9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235812"
---
### <a name="deserialization-of-objects-across-appdomains-can-fail"></a><span data-ttu-id="1a3dc-101">Uygulama etki alanları arasında nesneleri seri durumdan çıkarma başarısız olabilir</span><span class="sxs-lookup"><span data-stu-id="1a3dc-101">Deserialization of objects across appdomains can fail</span></span>

|   |   |
|---|---|
|<span data-ttu-id="1a3dc-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="1a3dc-102">Details</span></span>|<span data-ttu-id="1a3dc-103">Bazı durumlarda, iki veya daha fazla uygulama etki alanları ile farklı bir uygulama kullanıyorsa, uygulama temel dizini, uygulama etki alanları arasında nesnelerin mantıksal çağrı bağlamındaki seri durumdan çıkarılmaya çalışılırken bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1a3dc-103">In some cases, when an app uses two or more app domains with different application bases, trying to deserialize objects in the logical call context across app domains throws an exception.</span></span>|
|<span data-ttu-id="1a3dc-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="1a3dc-104">Suggestion</span></span>|<span data-ttu-id="1a3dc-105">Bkz: [azaltma: Uygulama etki alanlarında nesneleri seri durumdan çıkarma](~/docs/framework/migration-guide/mitigation-deserialization-of-objects-across-app-domains.md)</span><span class="sxs-lookup"><span data-stu-id="1a3dc-105">See [Mitigation: Deserialization of Objects Across App Domains](~/docs/framework/migration-guide/mitigation-deserialization-of-objects-across-app-domains.md)</span></span>|
|<span data-ttu-id="1a3dc-106">Kapsam</span><span class="sxs-lookup"><span data-stu-id="1a3dc-106">Scope</span></span>|<span data-ttu-id="1a3dc-107">Kenar</span><span class="sxs-lookup"><span data-stu-id="1a3dc-107">Edge</span></span>|
|<span data-ttu-id="1a3dc-108">Sürüm</span><span class="sxs-lookup"><span data-stu-id="1a3dc-108">Version</span></span>|<span data-ttu-id="1a3dc-109">4.5.1</span><span class="sxs-lookup"><span data-stu-id="1a3dc-109">4.5.1</span></span>|
|<span data-ttu-id="1a3dc-110">Tür</span><span class="sxs-lookup"><span data-stu-id="1a3dc-110">Type</span></span>|<span data-ttu-id="1a3dc-111">Çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="1a3dc-111">Runtime</span></span>|
