---
title: <claimType>
ms.date: 03/30/2017
ms.assetid: d17b5831-9a2c-45c4-b0d1-68f48e72e861
author: BrucePerlerMS
ms.openlocfilehash: 4253aec961b812b6893ee201861d2ab38048032a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942875"
---
# <a name="claimtype"></a><span data-ttu-id="24ee1-101">\<claimType ></span><span class="sxs-lookup"><span data-stu-id="24ee1-101">\<claimType></span></span>
<span data-ttu-id="24ee1-102">Gelen güvenlik belirteçleri için tek bir isteğe bağlı veya gerekli talebi belirtir.</span><span class="sxs-lookup"><span data-stu-id="24ee1-102">Specifies a single optional or required claim for incoming security tokens.</span></span>  
  
 <span data-ttu-id="24ee1-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="24ee1-103">\<system.identityModel></span></span>  
<span data-ttu-id="24ee1-104">\<IdentityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="24ee1-104">\<identityConfiguration></span></span>  
<span data-ttu-id="24ee1-105">\<claimTypeRequired ></span><span class="sxs-lookup"><span data-stu-id="24ee1-105">\<claimTypeRequired></span></span>  
<span data-ttu-id="24ee1-106">\<claimType ></span><span class="sxs-lookup"><span data-stu-id="24ee1-106">\<claimType></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24ee1-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="24ee1-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="24ee1-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="24ee1-108">Attributes and Elements</span></span>  
 <span data-ttu-id="24ee1-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="24ee1-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="24ee1-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="24ee1-110">Attributes</span></span>  
  
|<span data-ttu-id="24ee1-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="24ee1-111">Attribute</span></span>|<span data-ttu-id="24ee1-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="24ee1-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="24ee1-113">türü</span><span class="sxs-lookup"><span data-stu-id="24ee1-113">type</span></span>|<span data-ttu-id="24ee1-114">Talep türü.</span><span class="sxs-lookup"><span data-stu-id="24ee1-114">The claim type.</span></span> <span data-ttu-id="24ee1-115">Genellikle bir URI.</span><span class="sxs-lookup"><span data-stu-id="24ee1-115">Typically a URI.</span></span> <span data-ttu-id="24ee1-116">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="24ee1-116">Required.</span></span>|  
|<span data-ttu-id="24ee1-117">isteğe bağlı</span><span class="sxs-lookup"><span data-stu-id="24ee1-117">optional</span></span>|<span data-ttu-id="24ee1-118">Talep türünün isteğe bağlı olup olmadığını belirten bir Boolean değer.</span><span class="sxs-lookup"><span data-stu-id="24ee1-118">A boolean value that specifies whether the claim type is optional.</span></span> <span data-ttu-id="24ee1-119">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="24ee1-119">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="24ee1-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="24ee1-120">Child Elements</span></span>  
 <span data-ttu-id="24ee1-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="24ee1-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="24ee1-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="24ee1-122">Parent Elements</span></span>  
  
|<span data-ttu-id="24ee1-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="24ee1-123">Element</span></span>|<span data-ttu-id="24ee1-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="24ee1-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="24ee1-125">\<claimTypeRequired ></span><span class="sxs-lookup"><span data-stu-id="24ee1-125">\<claimTypeRequired></span></span>](claimtyperequired.md)|<span data-ttu-id="24ee1-126">Gelen güvenlik belirteçleri için gerekli talepler kümesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="24ee1-126">Specifies the set of required claims for incoming security tokens.</span></span>|
