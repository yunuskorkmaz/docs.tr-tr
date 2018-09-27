---
title: '&lt;ClaimType&gt;'
ms.date: 03/30/2017
ms.assetid: d17b5831-9a2c-45c4-b0d1-68f48e72e861
author: BrucePerlerMS
ms.openlocfilehash: 805377565b6e835fd9ffba915a003bc56529a3b6
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47234971"
---
# <a name="ltclaimtypegt"></a><span data-ttu-id="5fe4e-102">&lt;ClaimType&gt;</span><span class="sxs-lookup"><span data-stu-id="5fe4e-102">&lt;claimType&gt;</span></span>
<span data-ttu-id="5fe4e-103">Gelen güvenlik belirteçleri için tek bir isteğe bağlı veya gerekli talep belirtir.</span><span class="sxs-lookup"><span data-stu-id="5fe4e-103">Specifies a single optional or required claim for incoming security tokens.</span></span>  
  
 <span data-ttu-id="5fe4e-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="5fe4e-104">\<system.identityModel></span></span>  
<span data-ttu-id="5fe4e-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="5fe4e-105">\<identityConfiguration></span></span>  
<span data-ttu-id="5fe4e-106">\<claimTypeRequired ></span><span class="sxs-lookup"><span data-stu-id="5fe4e-106">\<claimTypeRequired></span></span>  
<span data-ttu-id="5fe4e-107">\<claimType ></span><span class="sxs-lookup"><span data-stu-id="5fe4e-107">\<claimType></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5fe4e-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5fe4e-108">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimTypeRequired>  
      <claimType type=URI optional=xs:boolean >  
      </claimType>  
    </claimTypeRequired>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5fe4e-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5fe4e-109">Attributes and Elements</span></span>  
 <span data-ttu-id="5fe4e-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5fe4e-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5fe4e-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5fe4e-111">Attributes</span></span>  
  
|<span data-ttu-id="5fe4e-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="5fe4e-112">Attribute</span></span>|<span data-ttu-id="5fe4e-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5fe4e-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5fe4e-114">türü</span><span class="sxs-lookup"><span data-stu-id="5fe4e-114">type</span></span>|<span data-ttu-id="5fe4e-115">Talep türü.</span><span class="sxs-lookup"><span data-stu-id="5fe4e-115">The claim type.</span></span> <span data-ttu-id="5fe4e-116">Genellikle bir URI.</span><span class="sxs-lookup"><span data-stu-id="5fe4e-116">Typically a URI.</span></span> <span data-ttu-id="5fe4e-117">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="5fe4e-117">Required.</span></span>|  
|<span data-ttu-id="5fe4e-118">isteğe bağlı</span><span class="sxs-lookup"><span data-stu-id="5fe4e-118">optional</span></span>|<span data-ttu-id="5fe4e-119">Talep türü isteğe bağlı olup olmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="5fe4e-119">A boolean value that specifies whether the claim type is optional.</span></span> <span data-ttu-id="5fe4e-120">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="5fe4e-120">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5fe4e-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5fe4e-121">Child Elements</span></span>  
 <span data-ttu-id="5fe4e-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="5fe4e-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5fe4e-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5fe4e-123">Parent Elements</span></span>  
  
|<span data-ttu-id="5fe4e-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="5fe4e-124">Element</span></span>|<span data-ttu-id="5fe4e-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5fe4e-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5fe4e-126">\<claimTypeRequired ></span><span class="sxs-lookup"><span data-stu-id="5fe4e-126">\<claimTypeRequired></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimtyperequired.md)|<span data-ttu-id="5fe4e-127">Gelen güvenlik belirteçleri için gerekli talep kümesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5fe4e-127">Specifies the set of required claims for incoming security tokens.</span></span>|
