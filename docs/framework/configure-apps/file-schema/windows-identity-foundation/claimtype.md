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
ms.openlocfilehash: c4ee8833578b082f25c427b13d77072d1954197f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="ltclaimtypegt"></a><span data-ttu-id="1d164-102">&lt;claimType&gt;</span><span class="sxs-lookup"><span data-stu-id="1d164-102">&lt;claimType&gt;</span></span>
<span data-ttu-id="1d164-103">Gelen güvenlik belirteçlerinin için tek bir isteğe bağlı veya gerekli talep belirtir.</span><span class="sxs-lookup"><span data-stu-id="1d164-103">Specifies a single optional or required claim for incoming security tokens.</span></span>  
  
 <span data-ttu-id="1d164-104">\<System.IdentityModel ></span><span class="sxs-lookup"><span data-stu-id="1d164-104">\<system.identityModel></span></span>  
<span data-ttu-id="1d164-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="1d164-105">\<identityConfiguration></span></span>  
<span data-ttu-id="1d164-106">\<claimTypeRequired ></span><span class="sxs-lookup"><span data-stu-id="1d164-106">\<claimTypeRequired></span></span>  
<span data-ttu-id="1d164-107">\<claimType ></span><span class="sxs-lookup"><span data-stu-id="1d164-107">\<claimType></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d164-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1d164-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1d164-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="1d164-109">Attributes and Elements</span></span>  
 <span data-ttu-id="1d164-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1d164-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1d164-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="1d164-111">Attributes</span></span>  
  
|<span data-ttu-id="1d164-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="1d164-112">Attribute</span></span>|<span data-ttu-id="1d164-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1d164-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1d164-114">türü</span><span class="sxs-lookup"><span data-stu-id="1d164-114">type</span></span>|<span data-ttu-id="1d164-115">Talep türü.</span><span class="sxs-lookup"><span data-stu-id="1d164-115">The claim type.</span></span> <span data-ttu-id="1d164-116">Tipik olarak bir URI.</span><span class="sxs-lookup"><span data-stu-id="1d164-116">Typically a URI.</span></span> <span data-ttu-id="1d164-117">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="1d164-117">Required.</span></span>|  
|<span data-ttu-id="1d164-118">isteğe bağlı</span><span class="sxs-lookup"><span data-stu-id="1d164-118">optional</span></span>|<span data-ttu-id="1d164-119">Talep türü isteğe bağlı olup olmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="1d164-119">A boolean value that specifies whether the claim type is optional.</span></span> <span data-ttu-id="1d164-120">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="1d164-120">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1d164-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="1d164-121">Child Elements</span></span>  
 <span data-ttu-id="1d164-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="1d164-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1d164-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="1d164-123">Parent Elements</span></span>  
  
|<span data-ttu-id="1d164-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="1d164-124">Element</span></span>|<span data-ttu-id="1d164-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1d164-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1d164-126">\<claimTypeRequired ></span><span class="sxs-lookup"><span data-stu-id="1d164-126">\<claimTypeRequired></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimtyperequired.md)|<span data-ttu-id="1d164-127">Gelen güvenlik belirteçlerinin için gerekli talep kümesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="1d164-127">Specifies the set of required claims for incoming security tokens.</span></span>|
