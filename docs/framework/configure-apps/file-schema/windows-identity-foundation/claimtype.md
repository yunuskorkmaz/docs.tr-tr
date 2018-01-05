---
title: '&lt;claimType&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d17b5831-9a2c-45c4-b0d1-68f48e72e861
caps.latest.revision: "4"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: ae572ff3a8a2335a4259bdce2af5f6922fb0596f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltclaimtypegt"></a><span data-ttu-id="35af3-102">&lt;claimType&gt;</span><span class="sxs-lookup"><span data-stu-id="35af3-102">&lt;claimType&gt;</span></span>
<span data-ttu-id="35af3-103">Gelen güvenlik belirteçlerinin için tek bir isteğe bağlı veya gerekli talep belirtir.</span><span class="sxs-lookup"><span data-stu-id="35af3-103">Specifies a single optional or required claim for incoming security tokens.</span></span>  
  
 <span data-ttu-id="35af3-104">\<System.IdentityModel ></span><span class="sxs-lookup"><span data-stu-id="35af3-104">\<system.identityModel></span></span>  
<span data-ttu-id="35af3-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="35af3-105">\<identityConfiguration></span></span>  
<span data-ttu-id="35af3-106">\<claimTypeRequired ></span><span class="sxs-lookup"><span data-stu-id="35af3-106">\<claimTypeRequired></span></span>  
<span data-ttu-id="35af3-107">\<claimType ></span><span class="sxs-lookup"><span data-stu-id="35af3-107">\<claimType></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35af3-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="35af3-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="35af3-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="35af3-109">Attributes and Elements</span></span>  
 <span data-ttu-id="35af3-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="35af3-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="35af3-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="35af3-111">Attributes</span></span>  
  
|<span data-ttu-id="35af3-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="35af3-112">Attribute</span></span>|<span data-ttu-id="35af3-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="35af3-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="35af3-114">türü</span><span class="sxs-lookup"><span data-stu-id="35af3-114">type</span></span>|<span data-ttu-id="35af3-115">Talep türü.</span><span class="sxs-lookup"><span data-stu-id="35af3-115">The claim type.</span></span> <span data-ttu-id="35af3-116">Tipik olarak bir URI.</span><span class="sxs-lookup"><span data-stu-id="35af3-116">Typically a URI.</span></span> <span data-ttu-id="35af3-117">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="35af3-117">Required.</span></span>|  
|<span data-ttu-id="35af3-118">isteğe bağlı</span><span class="sxs-lookup"><span data-stu-id="35af3-118">optional</span></span>|<span data-ttu-id="35af3-119">Talep türü isteğe bağlı olup olmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="35af3-119">A boolean value that specifies whether the claim type is optional.</span></span> <span data-ttu-id="35af3-120">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="35af3-120">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="35af3-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="35af3-121">Child Elements</span></span>  
 <span data-ttu-id="35af3-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="35af3-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="35af3-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="35af3-123">Parent Elements</span></span>  
  
|<span data-ttu-id="35af3-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="35af3-124">Element</span></span>|<span data-ttu-id="35af3-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="35af3-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="35af3-126">\<claimTypeRequired ></span><span class="sxs-lookup"><span data-stu-id="35af3-126">\<claimTypeRequired></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimtyperequired.md)|<span data-ttu-id="35af3-127">Gelen güvenlik belirteçlerinin için gerekli talep kümesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="35af3-127">Specifies the set of required claims for incoming security tokens.</span></span>|
