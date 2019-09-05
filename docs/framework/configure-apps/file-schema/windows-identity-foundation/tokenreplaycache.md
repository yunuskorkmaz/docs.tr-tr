---
title: <tokenReplayCache>
ms.date: 03/30/2017
ms.assetid: 1572ab23-6933-41b5-bfb4-0c4548145500
author: BrucePerlerMS
ms.openlocfilehash: 9f3a95fd0a39f199eaf13c7509aff22caa0e3b66
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251779"
---
# <a name="tokenreplaycache"></a><span data-ttu-id="e078d-101">\<tokenReplayCache ></span><span class="sxs-lookup"><span data-stu-id="e078d-101">\<tokenReplayCache></span></span>
<span data-ttu-id="e078d-102">Belirteç yeniden yürütme önbelleğini bir hizmet veya güvenlik belirteci işleyici koleksiyonuyla kaydeder.</span><span class="sxs-lookup"><span data-stu-id="e078d-102">Registers a token replay cache with a service or a security token handler collection.</span></span>  
  
<span data-ttu-id="e078d-103">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e078d-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e078d-104">&nbsp;&nbsp;[ **\<System. IdentityModel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="e078d-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="e078d-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<IdentityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="e078d-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="e078d-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<önbellekler >** ](caches.md)</span><span class="sxs-lookup"><span data-stu-id="e078d-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<caches>**](caches.md)</span></span>\
<span data-ttu-id="e078d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<tokenReplayCache >**</span><span class="sxs-lookup"><span data-stu-id="e078d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<tokenReplayCache>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e078d-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e078d-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e078d-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e078d-109">Attributes and Elements</span></span>  
 <span data-ttu-id="e078d-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e078d-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e078d-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e078d-111">Attributes</span></span>  
  
|<span data-ttu-id="e078d-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e078d-112">Attribute</span></span>|<span data-ttu-id="e078d-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e078d-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e078d-114">türü</span><span class="sxs-lookup"><span data-stu-id="e078d-114">type</span></span>|<span data-ttu-id="e078d-115"><xref:System.IdentityModel.Tokens.TokenReplayCache> Sınıfından türeten bir tür.</span><span class="sxs-lookup"><span data-stu-id="e078d-115">A type that derives from the <xref:System.IdentityModel.Tokens.TokenReplayCache> class.</span></span> <span data-ttu-id="e078d-116">Özel `type`belirtme hakkında daha fazla bilgi için bkz. [özel tür başvuruları].</span><span class="sxs-lookup"><span data-stu-id="e078d-116">For more information about how to specify a custom `type`, see [Custom Type References].</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="e078d-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e078d-117">Child Elements</span></span>  
 <span data-ttu-id="e078d-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="e078d-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e078d-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e078d-119">Parent Elements</span></span>  
  
|<span data-ttu-id="e078d-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="e078d-120">Element</span></span>|<span data-ttu-id="e078d-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e078d-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e078d-122">\<önbellekler ></span><span class="sxs-lookup"><span data-stu-id="e078d-122">\<caches></span></span>](caches.md)|<span data-ttu-id="e078d-123">Bir hizmet veya güvenlik belirteci işleyici koleksiyonu tarafından kullanılan önbellekleri kaydeder.</span><span class="sxs-lookup"><span data-stu-id="e078d-123">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e078d-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e078d-124">Remarks</span></span>  
 <span data-ttu-id="e078d-125">Belirteç yeniden yürütme önbelleği, yeniden yürütülmüş belirteçleri algılamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e078d-125">The token replay cache is used to detect replayed tokens.</span></span> <span data-ttu-id="e078d-126">Belirteç yeniden yürütme algılaması, belirteçlerin en uzun süre sonu süresini de belirten [ \<TokenReplayDetection >](tokenreplaydetection.md) öğesi tarafından etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="e078d-126">Token replay detection is enabled by the [\<tokenReplayDetection>](tokenreplaydetection.md) element, which also specifies the maximum expiration time for tokens.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e078d-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="e078d-127">Example</span></span>  
 <span data-ttu-id="e078d-128">Aşağıdaki XML, yeniden yürütülmüş belirteçleri algılamak için özel bir önbelleğin yapılandırmasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e078d-128">The following XML shows the configuration of a custom cache for detecting replayed tokens.</span></span>  
  
```xml  
<caches>  
  <tokenReplayCache type="MyCacheLibrary.MyTokenReplayCache, MyCacheLibrary">  
  </tokenReplayCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e078d-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e078d-129">See also</span></span>

- <xref:System.IdentityModel.Tokens.TokenReplayCache>
- [<span data-ttu-id="e078d-130">\<tokenReplayDetection ></span><span class="sxs-lookup"><span data-stu-id="e078d-130">\<tokenReplayDetection></span></span>](tokenreplaydetection.md)
