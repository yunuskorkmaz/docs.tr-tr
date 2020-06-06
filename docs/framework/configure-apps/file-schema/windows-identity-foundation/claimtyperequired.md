---
title: <claimTypeRequired>
ms.date: 03/30/2017
ms.assetid: c469d71f-6c77-4a24-97aa-53efa126ceef
author: BrucePerlerMS
ms.openlocfilehash: 1c40c5e4b4a24a3c1bbd6e096f12b7b044331c88
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70252059"
---
# \<claimTypeRequired>
<span data-ttu-id="2ad7c-101">Gelen güvenlik belirteçleri için gerekli talepler kümesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="2ad7c-101">Specifies the set of required claims for incoming security tokens.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<claimTypeRequired>**  
  
## <a name="syntax"></a><span data-ttu-id="2ad7c-102">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2ad7c-102">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimTypeRequired>  
    </claimTypeRequired>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2ad7c-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="2ad7c-103">Attributes and Elements</span></span>  
 <span data-ttu-id="2ad7c-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2ad7c-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2ad7c-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="2ad7c-105">Attributes</span></span>  
 <span data-ttu-id="2ad7c-106">Yok</span><span class="sxs-lookup"><span data-stu-id="2ad7c-106">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="2ad7c-107">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="2ad7c-107">Child Elements</span></span>  
  
|<span data-ttu-id="2ad7c-108">Öğe</span><span class="sxs-lookup"><span data-stu-id="2ad7c-108">Element</span></span>|<span data-ttu-id="2ad7c-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2ad7c-109">Description</span></span>|  
|-------------|-----------------|  
|[\<claimType>](claimtype.md)|<span data-ttu-id="2ad7c-110">Gelen güvenlik belirteçleri için tek bir isteğe bağlı veya gerekli talebi belirtir.</span><span class="sxs-lookup"><span data-stu-id="2ad7c-110">Specifies a single optional or required claim for incoming security tokens.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2ad7c-111">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="2ad7c-111">Parent Elements</span></span>  
  
|<span data-ttu-id="2ad7c-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="2ad7c-112">Element</span></span>|<span data-ttu-id="2ad7c-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2ad7c-113">Description</span></span>|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|<span data-ttu-id="2ad7c-114">Hizmet düzeyi kimlik ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="2ad7c-114">Specifies service-level identity settings.</span></span>|
