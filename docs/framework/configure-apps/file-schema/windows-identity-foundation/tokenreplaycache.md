---
title: '&lt;tokenReplayCache&gt;'
ms.date: 03/30/2017
ms.assetid: 1572ab23-6933-41b5-bfb4-0c4548145500
author: BrucePerlerMS
ms.openlocfilehash: 1e89afc5764dbdb86e87d2307425299dff57c686
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54525177"
---
# <a name="lttokenreplaycachegt"></a><span data-ttu-id="5af34-102">&lt;tokenReplayCache&gt;</span><span class="sxs-lookup"><span data-stu-id="5af34-102">&lt;tokenReplayCache&gt;</span></span>
<span data-ttu-id="5af34-103">Bir hizmet veya bir güvenlik belirteci işleyicisi koleksiyon ile bir belirteç yeniden yürütme önbelleğe kaydeder.</span><span class="sxs-lookup"><span data-stu-id="5af34-103">Registers a token replay cache with a service or a security token handler collection.</span></span>  
  
 <span data-ttu-id="5af34-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="5af34-104">\<system.identityModel></span></span>  
<span data-ttu-id="5af34-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="5af34-105">\<identityConfiguration></span></span>  
<span data-ttu-id="5af34-106">\<önbelleğe alan ></span><span class="sxs-lookup"><span data-stu-id="5af34-106">\<caches></span></span>  
<span data-ttu-id="5af34-107">\<tokenReplayCache></span><span class="sxs-lookup"><span data-stu-id="5af34-107">\<tokenReplayCache></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5af34-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5af34-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5af34-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5af34-109">Attributes and Elements</span></span>  
 <span data-ttu-id="5af34-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5af34-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5af34-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5af34-111">Attributes</span></span>  
  
|<span data-ttu-id="5af34-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="5af34-112">Attribute</span></span>|<span data-ttu-id="5af34-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5af34-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5af34-114">türü</span><span class="sxs-lookup"><span data-stu-id="5af34-114">type</span></span>|<span data-ttu-id="5af34-115">Türetilen bir tür <xref:System.IdentityModel.Tokens.TokenReplayCache> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="5af34-115">A type that derives from the <xref:System.IdentityModel.Tokens.TokenReplayCache> class.</span></span> <span data-ttu-id="5af34-116">Özel bir belirtme hakkında daha fazla bilgi için `type`, [özel tür başvurularını] bakın.</span><span class="sxs-lookup"><span data-stu-id="5af34-116">For more information about how to specify a custom `type`, see [Custom Type References].</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="5af34-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5af34-117">Child Elements</span></span>  
 <span data-ttu-id="5af34-118">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="5af34-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5af34-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5af34-119">Parent Elements</span></span>  
  
|<span data-ttu-id="5af34-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="5af34-120">Element</span></span>|<span data-ttu-id="5af34-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5af34-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5af34-122">\<önbelleğe alan ></span><span class="sxs-lookup"><span data-stu-id="5af34-122">\<caches></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|<span data-ttu-id="5af34-123">Bir hizmet veya bir güvenlik belirteci işleyicisi koleksiyon tarafından kullanılan önbellekleri kaydeder.</span><span class="sxs-lookup"><span data-stu-id="5af34-123">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5af34-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5af34-124">Remarks</span></span>  
 <span data-ttu-id="5af34-125">Belirteç yeniden yürütme önbelleğini yeniden yürütülmüş belirteçleri algılamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5af34-125">The token replay cache is used to detect replayed tokens.</span></span> <span data-ttu-id="5af34-126">Belirteç yeniden yürütme algılaması etkindir [ \<tokenReplayDetection >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md) öğesi, ayrıca belirteçleri maksimum sona erme süresini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5af34-126">Token replay detection is enabled by the [\<tokenReplayDetection>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md) element, which also specifies the maximum expiration time for tokens.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5af34-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="5af34-127">Example</span></span>  
 <span data-ttu-id="5af34-128">Aşağıdaki XML yeniden yürütülmüş belirteçleri algılamak için özel bir önbellek yapılandırmasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="5af34-128">The following XML shows the configuration of a custom cache for detecting replayed tokens.</span></span>  
  
```xml  
<caches>  
  <tokenReplayCache type="MyCacheLibrary.MyTokenReplayCache, MyCacheLibrary">  
  </tokenReplayCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5af34-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5af34-129">See also</span></span>
- <xref:System.IdentityModel.Tokens.TokenReplayCache>
- [<span data-ttu-id="5af34-130">\<tokenReplayDetection ></span><span class="sxs-lookup"><span data-stu-id="5af34-130">\<tokenReplayDetection></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md)
