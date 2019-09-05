---
title: <claimTypeRequired>
ms.date: 03/30/2017
ms.assetid: c469d71f-6c77-4a24-97aa-53efa126ceef
author: BrucePerlerMS
ms.openlocfilehash: 1c40c5e4b4a24a3c1bbd6e096f12b7b044331c88
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252059"
---
# <a name="claimtyperequired"></a><span data-ttu-id="13177-101">\<claimTypeRequired ></span><span class="sxs-lookup"><span data-stu-id="13177-101">\<claimTypeRequired></span></span>
<span data-ttu-id="13177-102">Gelen güvenlik belirteçleri için gerekli talepler kümesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="13177-102">Specifies the set of required claims for incoming security tokens.</span></span>  
  
<span data-ttu-id="13177-103">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="13177-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="13177-104">&nbsp;&nbsp;[ **\<System. IdentityModel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="13177-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="13177-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<IdentityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="13177-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="13177-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<claimTypeRequired >**</span><span class="sxs-lookup"><span data-stu-id="13177-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<claimTypeRequired>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13177-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="13177-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimTypeRequired>  
    </claimTypeRequired>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="13177-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="13177-108">Attributes and Elements</span></span>  
 <span data-ttu-id="13177-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="13177-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="13177-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="13177-110">Attributes</span></span>  
 <span data-ttu-id="13177-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="13177-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="13177-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="13177-112">Child Elements</span></span>  
  
|<span data-ttu-id="13177-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="13177-113">Element</span></span>|<span data-ttu-id="13177-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="13177-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="13177-115">\<claimType ></span><span class="sxs-lookup"><span data-stu-id="13177-115">\<claimType></span></span>](claimtype.md)|<span data-ttu-id="13177-116">Gelen güvenlik belirteçleri için tek bir isteğe bağlı veya gerekli talebi belirtir.</span><span class="sxs-lookup"><span data-stu-id="13177-116">Specifies a single optional or required claim for incoming security tokens.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="13177-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="13177-117">Parent Elements</span></span>  
  
|<span data-ttu-id="13177-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="13177-118">Element</span></span>|<span data-ttu-id="13177-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="13177-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="13177-120">\<IdentityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="13177-120">\<identityConfiguration></span></span>](identityconfiguration.md)|<span data-ttu-id="13177-121">Hizmet düzeyi kimlik ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="13177-121">Specifies service-level identity settings.</span></span>|
