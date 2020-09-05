---
ms.openlocfilehash: 3f82a4daac3b5d8981532f0c82e9a76f13c68b6e
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497718"
---
### <a name="deserialization-of-objects-across-appdomains-can-fail"></a><span data-ttu-id="39461-101">AppDomain 'lerde nesnelerin serisini kaldırma başarısız olabilir</span><span class="sxs-lookup"><span data-stu-id="39461-101">Deserialization of objects across appdomains can fail</span></span>

#### <a name="details"></a><span data-ttu-id="39461-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="39461-102">Details</span></span>

<span data-ttu-id="39461-103">Bazı durumlarda, bir uygulama farklı uygulama temellerine sahip iki veya daha fazla uygulama etki alanı kullandığında, uygulama etki alanlarında mantıksal çağrı bağlamındaki nesnelerin serisini kaldırma girişimi bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="39461-103">In some cases, when an app uses two or more app domains with different application bases, trying to deserialize objects in the logical call context across app domains throws an exception.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="39461-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="39461-104">Suggestion</span></span>

<span data-ttu-id="39461-105">Bkz [. azaltma: uygulama etki alanları arasında nesnelerin serisini kaldırma](~/docs/framework/migration-guide/mitigation-deserialization-of-objects-across-app-domains.md)</span><span class="sxs-lookup"><span data-stu-id="39461-105">See [Mitigation: Deserialization of Objects Across App Domains](~/docs/framework/migration-guide/mitigation-deserialization-of-objects-across-app-domains.md)</span></span>

| <span data-ttu-id="39461-106">Name</span><span class="sxs-lookup"><span data-stu-id="39461-106">Name</span></span>    | <span data-ttu-id="39461-107">Değer</span><span class="sxs-lookup"><span data-stu-id="39461-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="39461-108">Kapsam</span><span class="sxs-lookup"><span data-stu-id="39461-108">Scope</span></span>   |<span data-ttu-id="39461-109">Edge</span><span class="sxs-lookup"><span data-stu-id="39461-109">Edge</span></span>|
|<span data-ttu-id="39461-110">Sürüm</span><span class="sxs-lookup"><span data-stu-id="39461-110">Version</span></span>|<span data-ttu-id="39461-111">4.5.1</span><span class="sxs-lookup"><span data-stu-id="39461-111">4.5.1</span></span>|
|<span data-ttu-id="39461-112">Tür</span><span class="sxs-lookup"><span data-stu-id="39461-112">Type</span></span>|<span data-ttu-id="39461-113">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="39461-113">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="39461-114">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="39461-114">Affected APIs</span></span>

<span data-ttu-id="39461-115">API analizi aracılığıyla algılanamaz.</span><span class="sxs-lookup"><span data-stu-id="39461-115">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
