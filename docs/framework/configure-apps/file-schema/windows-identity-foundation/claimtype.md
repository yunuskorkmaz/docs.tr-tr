---
title: '&lt;claimType&gt;'
ms.date: 03/30/2017
ms.assetid: d17b5831-9a2c-45c4-b0d1-68f48e72e861
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 94f8586a9ca63b8c1f1128cdda4a74ccfe0f5416
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32767433"
---
# <a name="ltclaimtypegt"></a><span data-ttu-id="7ce55-102">&lt;claimType&gt;</span><span class="sxs-lookup"><span data-stu-id="7ce55-102">&lt;claimType&gt;</span></span>
<span data-ttu-id="7ce55-103">Gelen güvenlik belirteçlerinin için tek bir isteğe bağlı veya gerekli talep belirtir.</span><span class="sxs-lookup"><span data-stu-id="7ce55-103">Specifies a single optional or required claim for incoming security tokens.</span></span>  
  
 <span data-ttu-id="7ce55-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="7ce55-104">\<system.identityModel></span></span>  
<span data-ttu-id="7ce55-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="7ce55-105">\<identityConfiguration></span></span>  
<span data-ttu-id="7ce55-106">\<claimTypeRequired ></span><span class="sxs-lookup"><span data-stu-id="7ce55-106">\<claimTypeRequired></span></span>  
<span data-ttu-id="7ce55-107">\<claimType ></span><span class="sxs-lookup"><span data-stu-id="7ce55-107">\<claimType></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ce55-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7ce55-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7ce55-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="7ce55-109">Attributes and Elements</span></span>  
 <span data-ttu-id="7ce55-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7ce55-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7ce55-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="7ce55-111">Attributes</span></span>  
  
|<span data-ttu-id="7ce55-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="7ce55-112">Attribute</span></span>|<span data-ttu-id="7ce55-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7ce55-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7ce55-114">türü</span><span class="sxs-lookup"><span data-stu-id="7ce55-114">type</span></span>|<span data-ttu-id="7ce55-115">Talep türü.</span><span class="sxs-lookup"><span data-stu-id="7ce55-115">The claim type.</span></span> <span data-ttu-id="7ce55-116">Tipik olarak bir URI.</span><span class="sxs-lookup"><span data-stu-id="7ce55-116">Typically a URI.</span></span> <span data-ttu-id="7ce55-117">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="7ce55-117">Required.</span></span>|  
|<span data-ttu-id="7ce55-118">isteğe bağlı</span><span class="sxs-lookup"><span data-stu-id="7ce55-118">optional</span></span>|<span data-ttu-id="7ce55-119">Talep türü isteğe bağlı olup olmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="7ce55-119">A boolean value that specifies whether the claim type is optional.</span></span> <span data-ttu-id="7ce55-120">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="7ce55-120">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7ce55-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="7ce55-121">Child Elements</span></span>  
 <span data-ttu-id="7ce55-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="7ce55-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7ce55-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="7ce55-123">Parent Elements</span></span>  
  
|<span data-ttu-id="7ce55-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="7ce55-124">Element</span></span>|<span data-ttu-id="7ce55-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7ce55-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7ce55-126">\<claimTypeRequired ></span><span class="sxs-lookup"><span data-stu-id="7ce55-126">\<claimTypeRequired></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimtyperequired.md)|<span data-ttu-id="7ce55-127">Gelen güvenlik belirteçlerinin için gerekli talep kümesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="7ce55-127">Specifies the set of required claims for incoming security tokens.</span></span>|
