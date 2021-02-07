---
description: 'Hakkında daha fazla bilgi edinin: <tokenReplayCache>'
title: <tokenReplayCache>
ms.date: 03/30/2017
ms.assetid: 1572ab23-6933-41b5-bfb4-0c4548145500
author: BrucePerlerMS
ms.openlocfilehash: 793b1f88a9eeb0ebce4cd440e248e81377f17e9b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99749005"
---
# \<tokenReplayCache>

<span data-ttu-id="57cd3-102">Belirteç yeniden yürütme önbelleğini bir hizmet veya güvenlik belirteci işleyici koleksiyonuyla kaydeder.</span><span class="sxs-lookup"><span data-stu-id="57cd3-102">Registers a token replay cache with a service or a security token handler collection.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<caches>**](caches.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<tokenReplayCache>**  
  
## <a name="syntax"></a><span data-ttu-id="57cd3-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="57cd3-103">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <caches>  
      <tokenReplayCache type=xs:string>  
      </tokenReplayCache>  
    </caches>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="57cd3-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="57cd3-104">Attributes and Elements</span></span>  

 <span data-ttu-id="57cd3-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="57cd3-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="57cd3-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="57cd3-106">Attributes</span></span>  
  
|<span data-ttu-id="57cd3-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="57cd3-107">Attribute</span></span>|<span data-ttu-id="57cd3-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="57cd3-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="57cd3-109">tür</span><span class="sxs-lookup"><span data-stu-id="57cd3-109">type</span></span>|<span data-ttu-id="57cd3-110">Sınıfından türeten bir tür <xref:System.IdentityModel.Tokens.TokenReplayCache> .</span><span class="sxs-lookup"><span data-stu-id="57cd3-110">A type that derives from the <xref:System.IdentityModel.Tokens.TokenReplayCache> class.</span></span> <span data-ttu-id="57cd3-111">Özel belirtme hakkında daha fazla bilgi için `type` bkz. [özel tür başvuruları].</span><span class="sxs-lookup"><span data-stu-id="57cd3-111">For more information about how to specify a custom `type`, see [Custom Type References].</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="57cd3-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="57cd3-112">Child Elements</span></span>  

 <span data-ttu-id="57cd3-113">Yok</span><span class="sxs-lookup"><span data-stu-id="57cd3-113">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="57cd3-114">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="57cd3-114">Parent Elements</span></span>  
  
|<span data-ttu-id="57cd3-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="57cd3-115">Element</span></span>|<span data-ttu-id="57cd3-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="57cd3-116">Description</span></span>|  
|-------------|-----------------|  
|[\<caches>](caches.md)|<span data-ttu-id="57cd3-117">Bir hizmet veya güvenlik belirteci işleyici koleksiyonu tarafından kullanılan önbellekleri kaydeder.</span><span class="sxs-lookup"><span data-stu-id="57cd3-117">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="57cd3-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="57cd3-118">Remarks</span></span>  

 <span data-ttu-id="57cd3-119">Belirteç yeniden yürütme önbelleği, yeniden yürütülmüş belirteçleri algılamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="57cd3-119">The token replay cache is used to detect replayed tokens.</span></span> <span data-ttu-id="57cd3-120">Belirteç yeniden yürütme algılaması öğesi tarafından etkinleştirilir [\<tokenReplayDetection>](tokenreplaydetection.md) , bu da belirteçler için en uzun süre sonu süresini belirtir.</span><span class="sxs-lookup"><span data-stu-id="57cd3-120">Token replay detection is enabled by the [\<tokenReplayDetection>](tokenreplaydetection.md) element, which also specifies the maximum expiration time for tokens.</span></span>  
  
## <a name="example"></a><span data-ttu-id="57cd3-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="57cd3-121">Example</span></span>  

 <span data-ttu-id="57cd3-122">Aşağıdaki XML, yeniden yürütülmüş belirteçleri algılamak için özel bir önbelleğin yapılandırmasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="57cd3-122">The following XML shows the configuration of a custom cache for detecting replayed tokens.</span></span>  
  
```xml  
<caches>  
  <tokenReplayCache type="MyCacheLibrary.MyTokenReplayCache, MyCacheLibrary">  
  </tokenReplayCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="57cd3-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="57cd3-123">See also</span></span>

- <xref:System.IdentityModel.Tokens.TokenReplayCache>
- [\<tokenReplayDetection>](tokenreplaydetection.md)
