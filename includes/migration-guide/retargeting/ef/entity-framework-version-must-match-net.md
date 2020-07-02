---
ms.openlocfilehash: 863e7035827537e0f943af05c2f0232029b99db8
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617273"
---
### <a name="entity-framework-version-must-match-the-net-framework-version"></a><span data-ttu-id="7fe5b-101">Entity Framework sürümün .NET Framework sürümüyle eşleşmesi gerekir</span><span class="sxs-lookup"><span data-stu-id="7fe5b-101">Entity Framework version must match the .NET Framework version</span></span>

#### <a name="details"></a><span data-ttu-id="7fe5b-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="7fe5b-102">Details</span></span>

<span data-ttu-id="7fe5b-103">Entity Framework (EF) sürümü .NET Framework sürümüyle eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="7fe5b-103">The Entity Framework (EF) version should be matched with the .NET Framework version.</span></span> <span data-ttu-id="7fe5b-104">Entity Framework 5 .NET Framework 4,5 için önerilir.</span><span class="sxs-lookup"><span data-stu-id="7fe5b-104">Entity Framework 5 is recommended for .NET Framework 4.5.</span></span> <span data-ttu-id="7fe5b-105">İçinde .NET Framework 4,5 projesinde EF 4. x ile ilgili bazı bilinen sorunlar vardır <xref:System.ComponentModel.DataAnnotations> .</span><span class="sxs-lookup"><span data-stu-id="7fe5b-105">There are some known issues with EF 4.x in a .NET Framework 4.5 project around <xref:System.ComponentModel.DataAnnotations>.</span></span> <span data-ttu-id="7fe5b-106">.NET Framework 4,5 ' de, bunlar farklı bir derlemeye taşınmıştır, bu nedenle hangi ek açıklamaların kullanılacağını belirleyen sorunlar var.</span><span class="sxs-lookup"><span data-stu-id="7fe5b-106">In .NET Framework 4.5, these were moved to a different assembly, so there are issues determining which annotations to use.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="7fe5b-107">Öneri</span><span class="sxs-lookup"><span data-stu-id="7fe5b-107">Suggestion</span></span>

<span data-ttu-id="7fe5b-108">.NET Framework 4,5 için Entity Framework 5 sürümüne yükseltin</span><span class="sxs-lookup"><span data-stu-id="7fe5b-108">Upgrade to Entity Framework 5 for .NET Framework 4.5</span></span>

| <span data-ttu-id="7fe5b-109">Name</span><span class="sxs-lookup"><span data-stu-id="7fe5b-109">Name</span></span>    | <span data-ttu-id="7fe5b-110">Değer</span><span class="sxs-lookup"><span data-stu-id="7fe5b-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="7fe5b-111">Kapsam</span><span class="sxs-lookup"><span data-stu-id="7fe5b-111">Scope</span></span>   | <span data-ttu-id="7fe5b-112">Ana</span><span class="sxs-lookup"><span data-stu-id="7fe5b-112">Major</span></span>       |
| <span data-ttu-id="7fe5b-113">Sürüm</span><span class="sxs-lookup"><span data-stu-id="7fe5b-113">Version</span></span> | <span data-ttu-id="7fe5b-114">4,5</span><span class="sxs-lookup"><span data-stu-id="7fe5b-114">4.5</span></span>         |
| <span data-ttu-id="7fe5b-115">Tür</span><span class="sxs-lookup"><span data-stu-id="7fe5b-115">Type</span></span>    | <span data-ttu-id="7fe5b-116">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="7fe5b-116">Retargeting</span></span> |
