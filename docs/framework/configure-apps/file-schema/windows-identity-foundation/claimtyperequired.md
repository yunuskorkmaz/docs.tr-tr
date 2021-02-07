---
description: 'Hakkında daha fazla bilgi edinin: <claimTypeRequired>'
title: <claimTypeRequired>
ms.date: 03/30/2017
ms.assetid: c469d71f-6c77-4a24-97aa-53efa126ceef
author: BrucePerlerMS
ms.openlocfilehash: ba95c56af431a6dd81323751a42ce47160544cc3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99664177"
---
# \<claimTypeRequired>

<span data-ttu-id="7f088-102">Gelen güvenlik belirteçleri için gerekli talepler kümesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="7f088-102">Specifies the set of required claims for incoming security tokens.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<claimTypeRequired>**  
  
## <a name="syntax"></a><span data-ttu-id="7f088-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="7f088-103">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimTypeRequired>  
    </claimTypeRequired>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7f088-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="7f088-104">Attributes and Elements</span></span>  

 <span data-ttu-id="7f088-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7f088-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7f088-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="7f088-106">Attributes</span></span>  

 <span data-ttu-id="7f088-107">Yok</span><span class="sxs-lookup"><span data-stu-id="7f088-107">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="7f088-108">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="7f088-108">Child Elements</span></span>  
  
|<span data-ttu-id="7f088-109">Öğe</span><span class="sxs-lookup"><span data-stu-id="7f088-109">Element</span></span>|<span data-ttu-id="7f088-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7f088-110">Description</span></span>|  
|-------------|-----------------|  
|[\<claimType>](claimtype.md)|<span data-ttu-id="7f088-111">Gelen güvenlik belirteçleri için tek bir isteğe bağlı veya gerekli talebi belirtir.</span><span class="sxs-lookup"><span data-stu-id="7f088-111">Specifies a single optional or required claim for incoming security tokens.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7f088-112">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="7f088-112">Parent Elements</span></span>  
  
|<span data-ttu-id="7f088-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="7f088-113">Element</span></span>|<span data-ttu-id="7f088-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7f088-114">Description</span></span>|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|<span data-ttu-id="7f088-115">Hizmet düzeyi kimlik ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="7f088-115">Specifies service-level identity settings.</span></span>|
