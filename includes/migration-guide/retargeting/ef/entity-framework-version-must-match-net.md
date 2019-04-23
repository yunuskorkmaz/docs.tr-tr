---
ms.openlocfilehash: 4c6a89f9753989a5ad061e847dff70d2af0b3cf4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59774427"
---
### <a name="entity-framework-version-must-match-the-net-framework-version"></a><span data-ttu-id="bd3f9-101">Entity Framework sürümü .NET Framework sürümü ile eşleşmelidir</span><span class="sxs-lookup"><span data-stu-id="bd3f9-101">Entity Framework version must match the .NET Framework version</span></span>

|   |   |
|---|---|
|<span data-ttu-id="bd3f9-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="bd3f9-102">Details</span></span>|<span data-ttu-id="bd3f9-103">Entity framework sürümü .NET framework sürümüyle eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="bd3f9-103">The entity framework version should be matched with the .NET framework version.</span></span> <span data-ttu-id="bd3f9-104">Entity Framework 5, .NET Framework 4.5 için önerilir.</span><span class="sxs-lookup"><span data-stu-id="bd3f9-104">Entity Framework 5 is recommended for .NET Framework 4.5.</span></span> <span data-ttu-id="bd3f9-105">EF ile ilgili bazı bilinen sorunlar vardır bir .NET Framework 4.5 projedeki 4.x <xref:System.ComponentModel.DataAnnotations>.</span><span class="sxs-lookup"><span data-stu-id="bd3f9-105">There are some known issues with EF 4.x in a .NET Framework 4.5 project around <xref:System.ComponentModel.DataAnnotations>.</span></span> <span data-ttu-id="bd3f9-106">Sorunları belirleme kullanmak için hangi ek açıklamaları olduklarından .NET 4.5, bunlar farklı bir derleme için taşındı.</span><span class="sxs-lookup"><span data-stu-id="bd3f9-106">In .NET 4.5, these were moved to a different assembly, so there are issues determining which annotations to use.</span></span>|
|<span data-ttu-id="bd3f9-107">Öneri</span><span class="sxs-lookup"><span data-stu-id="bd3f9-107">Suggestion</span></span>|<span data-ttu-id="bd3f9-108">.NET Framework 4.5 için Entity Framework 5 yükseltme</span><span class="sxs-lookup"><span data-stu-id="bd3f9-108">Upgrade to Entity Framework 5 for .NET Framework 4.5</span></span>|
|<span data-ttu-id="bd3f9-109">Kapsam</span><span class="sxs-lookup"><span data-stu-id="bd3f9-109">Scope</span></span>|<span data-ttu-id="bd3f9-110">Ana</span><span class="sxs-lookup"><span data-stu-id="bd3f9-110">Major</span></span>|
|<span data-ttu-id="bd3f9-111">Sürüm</span><span class="sxs-lookup"><span data-stu-id="bd3f9-111">Version</span></span>|<span data-ttu-id="bd3f9-112">4,5</span><span class="sxs-lookup"><span data-stu-id="bd3f9-112">4.5</span></span>|
|<span data-ttu-id="bd3f9-113">Tür</span><span class="sxs-lookup"><span data-stu-id="bd3f9-113">Type</span></span>|<span data-ttu-id="bd3f9-114">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="bd3f9-114">Retargeting</span></span>|
