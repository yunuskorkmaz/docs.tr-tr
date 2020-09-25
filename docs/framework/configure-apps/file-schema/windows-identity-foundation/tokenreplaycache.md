---
title: <tokenReplayCache>
ms.date: 03/30/2017
ms.assetid: 1572ab23-6933-41b5-bfb4-0c4548145500
author: BrucePerlerMS
ms.openlocfilehash: 5e695bb56b59da40ce9e83f9f4f77d0d22d0b40f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91202428"
---
# \<tokenReplayCache>

<span data-ttu-id="ef1f4-101">Belirteç yeniden yürütme önbelleğini bir hizmet veya güvenlik belirteci işleyici koleksiyonuyla kaydeder.</span><span class="sxs-lookup"><span data-stu-id="ef1f4-101">Registers a token replay cache with a service or a security token handler collection.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<caches>**](caches.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<tokenReplayCache>**  
  
## <a name="syntax"></a><span data-ttu-id="ef1f4-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="ef1f4-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ef1f4-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ef1f4-103">Attributes and Elements</span></span>  

 <span data-ttu-id="ef1f4-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ef1f4-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ef1f4-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ef1f4-105">Attributes</span></span>  
  
|<span data-ttu-id="ef1f4-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ef1f4-106">Attribute</span></span>|<span data-ttu-id="ef1f4-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ef1f4-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ef1f4-108">tür</span><span class="sxs-lookup"><span data-stu-id="ef1f4-108">type</span></span>|<span data-ttu-id="ef1f4-109">Sınıfından türeten bir tür <xref:System.IdentityModel.Tokens.TokenReplayCache> .</span><span class="sxs-lookup"><span data-stu-id="ef1f4-109">A type that derives from the <xref:System.IdentityModel.Tokens.TokenReplayCache> class.</span></span> <span data-ttu-id="ef1f4-110">Özel belirtme hakkında daha fazla bilgi için `type` bkz. [özel tür başvuruları].</span><span class="sxs-lookup"><span data-stu-id="ef1f4-110">For more information about how to specify a custom `type`, see [Custom Type References].</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="ef1f4-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ef1f4-111">Child Elements</span></span>  

 <span data-ttu-id="ef1f4-112">Yok</span><span class="sxs-lookup"><span data-stu-id="ef1f4-112">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ef1f4-113">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ef1f4-113">Parent Elements</span></span>  
  
|<span data-ttu-id="ef1f4-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="ef1f4-114">Element</span></span>|<span data-ttu-id="ef1f4-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ef1f4-115">Description</span></span>|  
|-------------|-----------------|  
|[\<caches>](caches.md)|<span data-ttu-id="ef1f4-116">Bir hizmet veya güvenlik belirteci işleyici koleksiyonu tarafından kullanılan önbellekleri kaydeder.</span><span class="sxs-lookup"><span data-stu-id="ef1f4-116">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ef1f4-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ef1f4-117">Remarks</span></span>  

 <span data-ttu-id="ef1f4-118">Belirteç yeniden yürütme önbelleği, yeniden yürütülmüş belirteçleri algılamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ef1f4-118">The token replay cache is used to detect replayed tokens.</span></span> <span data-ttu-id="ef1f4-119">Belirteç yeniden yürütme algılaması öğesi tarafından etkinleştirilir [\<tokenReplayDetection>](tokenreplaydetection.md) , bu da belirteçler için en uzun süre sonu süresini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ef1f4-119">Token replay detection is enabled by the [\<tokenReplayDetection>](tokenreplaydetection.md) element, which also specifies the maximum expiration time for tokens.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ef1f4-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="ef1f4-120">Example</span></span>  

 <span data-ttu-id="ef1f4-121">Aşağıdaki XML, yeniden yürütülmüş belirteçleri algılamak için özel bir önbelleğin yapılandırmasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ef1f4-121">The following XML shows the configuration of a custom cache for detecting replayed tokens.</span></span>  
  
```xml  
<caches>  
  <tokenReplayCache type="MyCacheLibrary.MyTokenReplayCache, MyCacheLibrary">  
  </tokenReplayCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ef1f4-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ef1f4-122">See also</span></span>

- <xref:System.IdentityModel.Tokens.TokenReplayCache>
- [\<tokenReplayDetection>](tokenreplaydetection.md)
