---
ms.openlocfilehash: 5c949b79eefa68ea6f8d4ad27c716c438e24f170
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620561"
---
### <a name="deserialization-of-objects-across-appdomains-can-fail"></a><span data-ttu-id="7c3f3-101">AppDomain 'lerde nesnelerin serisini kaldırma başarısız olabilir</span><span class="sxs-lookup"><span data-stu-id="7c3f3-101">Deserialization of objects across appdomains can fail</span></span>

#### <a name="details"></a><span data-ttu-id="7c3f3-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="7c3f3-102">Details</span></span>

<span data-ttu-id="7c3f3-103">Bazı durumlarda, bir uygulama farklı uygulama temellerine sahip iki veya daha fazla uygulama etki alanı kullandığında, uygulama etki alanlarında mantıksal çağrı bağlamındaki nesnelerin serisini kaldırma girişimi bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7c3f3-103">In some cases, when an app uses two or more app domains with different application bases, trying to deserialize objects in the logical call context across app domains throws an exception.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="7c3f3-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="7c3f3-104">Suggestion</span></span>

<span data-ttu-id="7c3f3-105">Bkz [. azaltma: uygulama etki alanları arasında nesnelerin serisini kaldırma](~/docs/framework/migration-guide/mitigation-deserialization-of-objects-across-app-domains.md)</span><span class="sxs-lookup"><span data-stu-id="7c3f3-105">See [Mitigation: Deserialization of Objects Across App Domains](~/docs/framework/migration-guide/mitigation-deserialization-of-objects-across-app-domains.md)</span></span>

| <span data-ttu-id="7c3f3-106">Name</span><span class="sxs-lookup"><span data-stu-id="7c3f3-106">Name</span></span>    | <span data-ttu-id="7c3f3-107">Değer</span><span class="sxs-lookup"><span data-stu-id="7c3f3-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="7c3f3-108">Kapsam</span><span class="sxs-lookup"><span data-stu-id="7c3f3-108">Scope</span></span>   |<span data-ttu-id="7c3f3-109">Edge</span><span class="sxs-lookup"><span data-stu-id="7c3f3-109">Edge</span></span>|
|<span data-ttu-id="7c3f3-110">Sürüm</span><span class="sxs-lookup"><span data-stu-id="7c3f3-110">Version</span></span>|<span data-ttu-id="7c3f3-111">4.5.1</span><span class="sxs-lookup"><span data-stu-id="7c3f3-111">4.5.1</span></span>|
|<span data-ttu-id="7c3f3-112">Tür</span><span class="sxs-lookup"><span data-stu-id="7c3f3-112">Type</span></span>|<span data-ttu-id="7c3f3-113">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="7c3f3-113">Runtime</span></span>|
