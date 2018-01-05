---
title: '&lt;claimTypeRequired&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c469d71f-6c77-4a24-97aa-53efa126ceef
caps.latest.revision: "5"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 491277e39b29d7c3e0a0d69ec8745b2c6718a91e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltclaimtyperequiredgt"></a><span data-ttu-id="79ce9-102">&lt;claimTypeRequired&gt;</span><span class="sxs-lookup"><span data-stu-id="79ce9-102">&lt;claimTypeRequired&gt;</span></span>
<span data-ttu-id="79ce9-103">Gelen güvenlik belirteçlerinin için gerekli talep kümesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="79ce9-103">Specifies the set of required claims for incoming security tokens.</span></span>  
  
 <span data-ttu-id="79ce9-104">\<System.IdentityModel ></span><span class="sxs-lookup"><span data-stu-id="79ce9-104">\<system.identityModel></span></span>  
<span data-ttu-id="79ce9-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="79ce9-105">\<identityConfiguration></span></span>  
<span data-ttu-id="79ce9-106">\<claimTypeRequired ></span><span class="sxs-lookup"><span data-stu-id="79ce9-106">\<claimTypeRequired></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79ce9-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="79ce9-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimTypeRequired>  
    </claimTypeRequired>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="79ce9-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="79ce9-108">Attributes and Elements</span></span>  
 <span data-ttu-id="79ce9-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="79ce9-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="79ce9-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="79ce9-110">Attributes</span></span>  
 <span data-ttu-id="79ce9-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="79ce9-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="79ce9-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="79ce9-112">Child Elements</span></span>  
  
|<span data-ttu-id="79ce9-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="79ce9-113">Element</span></span>|<span data-ttu-id="79ce9-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="79ce9-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="79ce9-115">\<claimType ></span><span class="sxs-lookup"><span data-stu-id="79ce9-115">\<claimType></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimtype.md)|<span data-ttu-id="79ce9-116">Gelen güvenlik belirteçlerinin için tek bir isteğe bağlı veya gerekli talep belirtir.</span><span class="sxs-lookup"><span data-stu-id="79ce9-116">Specifies a single optional or required claim for incoming security tokens.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="79ce9-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="79ce9-117">Parent Elements</span></span>  
  
|<span data-ttu-id="79ce9-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="79ce9-118">Element</span></span>|<span data-ttu-id="79ce9-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="79ce9-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="79ce9-120">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="79ce9-120">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="79ce9-121">Hizmet düzeyi kimlik ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="79ce9-121">Specifies service-level identity settings.</span></span>|
