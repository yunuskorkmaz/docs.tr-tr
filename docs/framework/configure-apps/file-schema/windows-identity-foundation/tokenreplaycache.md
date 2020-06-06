---
title: <tokenReplayCache>
ms.date: 03/30/2017
ms.assetid: 1572ab23-6933-41b5-bfb4-0c4548145500
author: BrucePerlerMS
ms.openlocfilehash: 9f3a95fd0a39f199eaf13c7509aff22caa0e3b66
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70251779"
---
# \<tokenReplayCache>
<span data-ttu-id="e799d-101">Belirteç yeniden yürütme önbelleğini bir hizmet veya güvenlik belirteci işleyici koleksiyonuyla kaydeder.</span><span class="sxs-lookup"><span data-stu-id="e799d-101">Registers a token replay cache with a service or a security token handler collection.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<caches>**](caches.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<tokenReplayCache>**  
  
## <a name="syntax"></a><span data-ttu-id="e799d-102">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e799d-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e799d-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e799d-103">Attributes and Elements</span></span>  
 <span data-ttu-id="e799d-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e799d-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e799d-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e799d-105">Attributes</span></span>  
  
|<span data-ttu-id="e799d-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e799d-106">Attribute</span></span>|<span data-ttu-id="e799d-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e799d-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e799d-108">tür</span><span class="sxs-lookup"><span data-stu-id="e799d-108">type</span></span>|<span data-ttu-id="e799d-109">Sınıfından türeten bir tür <xref:System.IdentityModel.Tokens.TokenReplayCache> .</span><span class="sxs-lookup"><span data-stu-id="e799d-109">A type that derives from the <xref:System.IdentityModel.Tokens.TokenReplayCache> class.</span></span> <span data-ttu-id="e799d-110">Özel belirtme hakkında daha fazla bilgi için `type` bkz. [özel tür başvuruları].</span><span class="sxs-lookup"><span data-stu-id="e799d-110">For more information about how to specify a custom `type`, see [Custom Type References].</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="e799d-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e799d-111">Child Elements</span></span>  
 <span data-ttu-id="e799d-112">Yok</span><span class="sxs-lookup"><span data-stu-id="e799d-112">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e799d-113">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e799d-113">Parent Elements</span></span>  
  
|<span data-ttu-id="e799d-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="e799d-114">Element</span></span>|<span data-ttu-id="e799d-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e799d-115">Description</span></span>|  
|-------------|-----------------|  
|[\<caches>](caches.md)|<span data-ttu-id="e799d-116">Bir hizmet veya güvenlik belirteci işleyici koleksiyonu tarafından kullanılan önbellekleri kaydeder.</span><span class="sxs-lookup"><span data-stu-id="e799d-116">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e799d-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e799d-117">Remarks</span></span>  
 <span data-ttu-id="e799d-118">Belirteç yeniden yürütme önbelleği, yeniden yürütülmüş belirteçleri algılamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e799d-118">The token replay cache is used to detect replayed tokens.</span></span> <span data-ttu-id="e799d-119">Belirteç yeniden yürütme algılaması öğesi tarafından etkinleştirilir [\<tokenReplayDetection>](tokenreplaydetection.md) , bu da belirteçler için en uzun süre sonu süresini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e799d-119">Token replay detection is enabled by the [\<tokenReplayDetection>](tokenreplaydetection.md) element, which also specifies the maximum expiration time for tokens.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e799d-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="e799d-120">Example</span></span>  
 <span data-ttu-id="e799d-121">Aşağıdaki XML, yeniden yürütülmüş belirteçleri algılamak için özel bir önbelleğin yapılandırmasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e799d-121">The following XML shows the configuration of a custom cache for detecting replayed tokens.</span></span>  
  
```xml  
<caches>  
  <tokenReplayCache type="MyCacheLibrary.MyTokenReplayCache, MyCacheLibrary">  
  </tokenReplayCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e799d-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e799d-122">See also</span></span>

- <xref:System.IdentityModel.Tokens.TokenReplayCache>
- [\<tokenReplayDetection>](tokenreplaydetection.md)
