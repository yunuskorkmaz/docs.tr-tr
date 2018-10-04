---
title: '&lt;claimTypeRequired&gt;'
ms.date: 03/30/2017
ms.assetid: c469d71f-6c77-4a24-97aa-53efa126ceef
author: BrucePerlerMS
ms.openlocfilehash: df4494de6b76943849db2bedef8f43ad894b6bd1
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48780667"
---
# <a name="ltclaimtyperequiredgt"></a><span data-ttu-id="85116-102">&lt;claimTypeRequired&gt;</span><span class="sxs-lookup"><span data-stu-id="85116-102">&lt;claimTypeRequired&gt;</span></span>
<span data-ttu-id="85116-103">Gelen güvenlik belirteçleri için gerekli talep kümesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="85116-103">Specifies the set of required claims for incoming security tokens.</span></span>  
  
 <span data-ttu-id="85116-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="85116-104">\<system.identityModel></span></span>  
<span data-ttu-id="85116-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="85116-105">\<identityConfiguration></span></span>  
<span data-ttu-id="85116-106">\<claimTypeRequired ></span><span class="sxs-lookup"><span data-stu-id="85116-106">\<claimTypeRequired></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85116-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="85116-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimTypeRequired>  
    </claimTypeRequired>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="85116-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="85116-108">Attributes and Elements</span></span>  
 <span data-ttu-id="85116-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="85116-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="85116-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="85116-110">Attributes</span></span>  
 <span data-ttu-id="85116-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="85116-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="85116-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="85116-112">Child Elements</span></span>  
  
|<span data-ttu-id="85116-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="85116-113">Element</span></span>|<span data-ttu-id="85116-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="85116-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="85116-115">\<claimType ></span><span class="sxs-lookup"><span data-stu-id="85116-115">\<claimType></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimtype.md)|<span data-ttu-id="85116-116">Gelen güvenlik belirteçleri için tek bir isteğe bağlı veya gerekli talep belirtir.</span><span class="sxs-lookup"><span data-stu-id="85116-116">Specifies a single optional or required claim for incoming security tokens.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="85116-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="85116-117">Parent Elements</span></span>  
  
|<span data-ttu-id="85116-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="85116-118">Element</span></span>|<span data-ttu-id="85116-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="85116-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="85116-120">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="85116-120">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="85116-121">Hizmet düzeyi kimlik ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="85116-121">Specifies service-level identity settings.</span></span>|
