---
title: <claimType>
ms.date: 03/30/2017
ms.assetid: d17b5831-9a2c-45c4-b0d1-68f48e72e861
author: BrucePerlerMS
ms.openlocfilehash: 6bc185572528d4229ee53f1421eaa5bf27b053e6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61667229"
---
# <a name="claimtype"></a><span data-ttu-id="9b28c-101">\<claimType ></span><span class="sxs-lookup"><span data-stu-id="9b28c-101">\<claimType></span></span>
<span data-ttu-id="9b28c-102">Gelen güvenlik belirteçleri için tek bir isteğe bağlı veya gerekli talep belirtir.</span><span class="sxs-lookup"><span data-stu-id="9b28c-102">Specifies a single optional or required claim for incoming security tokens.</span></span>  
  
 <span data-ttu-id="9b28c-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="9b28c-103">\<system.identityModel></span></span>  
<span data-ttu-id="9b28c-104">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="9b28c-104">\<identityConfiguration></span></span>  
<span data-ttu-id="9b28c-105">\<claimTypeRequired ></span><span class="sxs-lookup"><span data-stu-id="9b28c-105">\<claimTypeRequired></span></span>  
<span data-ttu-id="9b28c-106">\<claimType ></span><span class="sxs-lookup"><span data-stu-id="9b28c-106">\<claimType></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b28c-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9b28c-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9b28c-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="9b28c-108">Attributes and Elements</span></span>  
 <span data-ttu-id="9b28c-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9b28c-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9b28c-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="9b28c-110">Attributes</span></span>  
  
|<span data-ttu-id="9b28c-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="9b28c-111">Attribute</span></span>|<span data-ttu-id="9b28c-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9b28c-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9b28c-113">türü</span><span class="sxs-lookup"><span data-stu-id="9b28c-113">type</span></span>|<span data-ttu-id="9b28c-114">Talep türü.</span><span class="sxs-lookup"><span data-stu-id="9b28c-114">The claim type.</span></span> <span data-ttu-id="9b28c-115">Genellikle bir URI.</span><span class="sxs-lookup"><span data-stu-id="9b28c-115">Typically a URI.</span></span> <span data-ttu-id="9b28c-116">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="9b28c-116">Required.</span></span>|  
|<span data-ttu-id="9b28c-117">isteğe bağlı</span><span class="sxs-lookup"><span data-stu-id="9b28c-117">optional</span></span>|<span data-ttu-id="9b28c-118">Talep türü isteğe bağlı olup olmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="9b28c-118">A boolean value that specifies whether the claim type is optional.</span></span> <span data-ttu-id="9b28c-119">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="9b28c-119">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9b28c-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="9b28c-120">Child Elements</span></span>  
 <span data-ttu-id="9b28c-121">None</span><span class="sxs-lookup"><span data-stu-id="9b28c-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9b28c-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="9b28c-122">Parent Elements</span></span>  
  
|<span data-ttu-id="9b28c-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="9b28c-123">Element</span></span>|<span data-ttu-id="9b28c-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9b28c-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9b28c-125">\<claimTypeRequired ></span><span class="sxs-lookup"><span data-stu-id="9b28c-125">\<claimTypeRequired></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimtyperequired.md)|<span data-ttu-id="9b28c-126">Gelen güvenlik belirteçleri için gerekli talep kümesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="9b28c-126">Specifies the set of required claims for incoming security tokens.</span></span>|
