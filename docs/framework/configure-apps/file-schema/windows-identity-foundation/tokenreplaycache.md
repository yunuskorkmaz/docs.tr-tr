---
title: <tokenReplayCache>
ms.date: 03/30/2017
ms.assetid: 1572ab23-6933-41b5-bfb4-0c4548145500
author: BrucePerlerMS
ms.openlocfilehash: 5747a4cfa93118dd41292904b168bbef02fec415
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69944072"
---
# <a name="tokenreplaycache"></a><span data-ttu-id="59579-101">\<tokenReplayCache ></span><span class="sxs-lookup"><span data-stu-id="59579-101">\<tokenReplayCache></span></span>
<span data-ttu-id="59579-102">Belirteç yeniden yürütme önbelleğini bir hizmet veya güvenlik belirteci işleyici koleksiyonuyla kaydeder.</span><span class="sxs-lookup"><span data-stu-id="59579-102">Registers a token replay cache with a service or a security token handler collection.</span></span>  
  
 <span data-ttu-id="59579-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="59579-103">\<system.identityModel></span></span>  
<span data-ttu-id="59579-104">\<IdentityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="59579-104">\<identityConfiguration></span></span>  
<span data-ttu-id="59579-105">\<önbellekler ></span><span class="sxs-lookup"><span data-stu-id="59579-105">\<caches></span></span>  
<span data-ttu-id="59579-106">\<tokenReplayCache ></span><span class="sxs-lookup"><span data-stu-id="59579-106">\<tokenReplayCache></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59579-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="59579-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="59579-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="59579-108">Attributes and Elements</span></span>  
 <span data-ttu-id="59579-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="59579-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="59579-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="59579-110">Attributes</span></span>  
  
|<span data-ttu-id="59579-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="59579-111">Attribute</span></span>|<span data-ttu-id="59579-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="59579-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="59579-113">türü</span><span class="sxs-lookup"><span data-stu-id="59579-113">type</span></span>|<span data-ttu-id="59579-114"><xref:System.IdentityModel.Tokens.TokenReplayCache> Sınıfından türeten bir tür.</span><span class="sxs-lookup"><span data-stu-id="59579-114">A type that derives from the <xref:System.IdentityModel.Tokens.TokenReplayCache> class.</span></span> <span data-ttu-id="59579-115">Özel `type`belirtme hakkında daha fazla bilgi için bkz. [özel tür başvuruları].</span><span class="sxs-lookup"><span data-stu-id="59579-115">For more information about how to specify a custom `type`, see [Custom Type References].</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="59579-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="59579-116">Child Elements</span></span>  
 <span data-ttu-id="59579-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="59579-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="59579-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="59579-118">Parent Elements</span></span>  
  
|<span data-ttu-id="59579-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="59579-119">Element</span></span>|<span data-ttu-id="59579-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="59579-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="59579-121">\<önbellekler ></span><span class="sxs-lookup"><span data-stu-id="59579-121">\<caches></span></span>](caches.md)|<span data-ttu-id="59579-122">Bir hizmet veya güvenlik belirteci işleyici koleksiyonu tarafından kullanılan önbellekleri kaydeder.</span><span class="sxs-lookup"><span data-stu-id="59579-122">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="59579-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="59579-123">Remarks</span></span>  
 <span data-ttu-id="59579-124">Belirteç yeniden yürütme önbelleği, yeniden yürütülmüş belirteçleri algılamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="59579-124">The token replay cache is used to detect replayed tokens.</span></span> <span data-ttu-id="59579-125">Belirteç yeniden yürütme algılaması, belirteçlerin en uzun süre sonu süresini de belirten [ \<TokenReplayDetection >](tokenreplaydetection.md) öğesi tarafından etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="59579-125">Token replay detection is enabled by the [\<tokenReplayDetection>](tokenreplaydetection.md) element, which also specifies the maximum expiration time for tokens.</span></span>  
  
## <a name="example"></a><span data-ttu-id="59579-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="59579-126">Example</span></span>  
 <span data-ttu-id="59579-127">Aşağıdaki XML, yeniden yürütülmüş belirteçleri algılamak için özel bir önbelleğin yapılandırmasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="59579-127">The following XML shows the configuration of a custom cache for detecting replayed tokens.</span></span>  
  
```xml  
<caches>  
  <tokenReplayCache type="MyCacheLibrary.MyTokenReplayCache, MyCacheLibrary">  
  </tokenReplayCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="59579-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="59579-128">See also</span></span>

- <xref:System.IdentityModel.Tokens.TokenReplayCache>
- [<span data-ttu-id="59579-129">\<tokenReplayDetection ></span><span class="sxs-lookup"><span data-stu-id="59579-129">\<tokenReplayDetection></span></span>](tokenreplaydetection.md)
