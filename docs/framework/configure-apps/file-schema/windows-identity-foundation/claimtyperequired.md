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
ms.openlocfilehash: 89d42cba78eb9758d8b3491fd1bd3b25ef168f9c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="ltclaimtyperequiredgt"></a><span data-ttu-id="dcbd6-102">&lt;claimTypeRequired&gt;</span><span class="sxs-lookup"><span data-stu-id="dcbd6-102">&lt;claimTypeRequired&gt;</span></span>
<span data-ttu-id="dcbd6-103">Gelen güvenlik belirteçlerinin için gerekli talep kümesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="dcbd6-103">Specifies the set of required claims for incoming security tokens.</span></span>  
  
 <span data-ttu-id="dcbd6-104">\<System.IdentityModel ></span><span class="sxs-lookup"><span data-stu-id="dcbd6-104">\<system.identityModel></span></span>  
<span data-ttu-id="dcbd6-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="dcbd6-105">\<identityConfiguration></span></span>  
<span data-ttu-id="dcbd6-106">\<claimTypeRequired ></span><span class="sxs-lookup"><span data-stu-id="dcbd6-106">\<claimTypeRequired></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dcbd6-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dcbd6-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimTypeRequired>  
    </claimTypeRequired>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dcbd6-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="dcbd6-108">Attributes and Elements</span></span>  
 <span data-ttu-id="dcbd6-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="dcbd6-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dcbd6-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="dcbd6-110">Attributes</span></span>  
 <span data-ttu-id="dcbd6-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="dcbd6-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="dcbd6-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="dcbd6-112">Child Elements</span></span>  
  
|<span data-ttu-id="dcbd6-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="dcbd6-113">Element</span></span>|<span data-ttu-id="dcbd6-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dcbd6-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dcbd6-115">\<claimType ></span><span class="sxs-lookup"><span data-stu-id="dcbd6-115">\<claimType></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimtype.md)|<span data-ttu-id="dcbd6-116">Gelen güvenlik belirteçlerinin için tek bir isteğe bağlı veya gerekli talep belirtir.</span><span class="sxs-lookup"><span data-stu-id="dcbd6-116">Specifies a single optional or required claim for incoming security tokens.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="dcbd6-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="dcbd6-117">Parent Elements</span></span>  
  
|<span data-ttu-id="dcbd6-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="dcbd6-118">Element</span></span>|<span data-ttu-id="dcbd6-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dcbd6-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dcbd6-120">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="dcbd6-120">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="dcbd6-121">Hizmet düzeyi kimlik ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="dcbd6-121">Specifies service-level identity settings.</span></span>|
