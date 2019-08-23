---
title: <claimTypeRequired>
ms.date: 03/30/2017
ms.assetid: c469d71f-6c77-4a24-97aa-53efa126ceef
author: BrucePerlerMS
ms.openlocfilehash: 85f3954514fa8b532311b1fbfc34f32ebefa4099
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942826"
---
# <a name="claimtyperequired"></a><span data-ttu-id="3f3f5-101">\<claimTypeRequired ></span><span class="sxs-lookup"><span data-stu-id="3f3f5-101">\<claimTypeRequired></span></span>
<span data-ttu-id="3f3f5-102">Gelen güvenlik belirteçleri için gerekli talepler kümesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="3f3f5-102">Specifies the set of required claims for incoming security tokens.</span></span>  
  
 <span data-ttu-id="3f3f5-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="3f3f5-103">\<system.identityModel></span></span>  
<span data-ttu-id="3f3f5-104">\<IdentityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="3f3f5-104">\<identityConfiguration></span></span>  
<span data-ttu-id="3f3f5-105">\<claimTypeRequired ></span><span class="sxs-lookup"><span data-stu-id="3f3f5-105">\<claimTypeRequired></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f3f5-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3f3f5-106">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimTypeRequired>  
    </claimTypeRequired>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3f3f5-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="3f3f5-107">Attributes and Elements</span></span>  
 <span data-ttu-id="3f3f5-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3f3f5-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3f3f5-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3f3f5-109">Attributes</span></span>  
 <span data-ttu-id="3f3f5-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="3f3f5-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3f3f5-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="3f3f5-111">Child Elements</span></span>  
  
|<span data-ttu-id="3f3f5-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="3f3f5-112">Element</span></span>|<span data-ttu-id="3f3f5-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3f3f5-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3f3f5-114">\<claimType ></span><span class="sxs-lookup"><span data-stu-id="3f3f5-114">\<claimType></span></span>](claimtype.md)|<span data-ttu-id="3f3f5-115">Gelen güvenlik belirteçleri için tek bir isteğe bağlı veya gerekli talebi belirtir.</span><span class="sxs-lookup"><span data-stu-id="3f3f5-115">Specifies a single optional or required claim for incoming security tokens.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3f3f5-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="3f3f5-116">Parent Elements</span></span>  
  
|<span data-ttu-id="3f3f5-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="3f3f5-117">Element</span></span>|<span data-ttu-id="3f3f5-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3f3f5-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3f3f5-119">\<IdentityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="3f3f5-119">\<identityConfiguration></span></span>](identityconfiguration.md)|<span data-ttu-id="3f3f5-120">Hizmet düzeyi kimlik ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="3f3f5-120">Specifies service-level identity settings.</span></span>|
