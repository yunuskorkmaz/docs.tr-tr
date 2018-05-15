---
title: '&lt;tokenReplayCache&gt;'
ms.date: 03/30/2017
ms.assetid: 1572ab23-6933-41b5-bfb4-0c4548145500
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 79022319944c4042c6f62a7521784b826b90d4ce
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="lttokenreplaycachegt"></a><span data-ttu-id="7b3df-102">&lt;tokenReplayCache&gt;</span><span class="sxs-lookup"><span data-stu-id="7b3df-102">&lt;tokenReplayCache&gt;</span></span>
<span data-ttu-id="7b3df-103">Bir hizmeti veya bir güvenlik belirteci işleyicisi koleksiyonu ile bir simge tekrar yürütme önbelleğine kaydeder.</span><span class="sxs-lookup"><span data-stu-id="7b3df-103">Registers a token replay cache with a service or a security token handler collection.</span></span>  
  
 <span data-ttu-id="7b3df-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="7b3df-104">\<system.identityModel></span></span>  
<span data-ttu-id="7b3df-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="7b3df-105">\<identityConfiguration></span></span>  
<span data-ttu-id="7b3df-106">\<önbelleğe alan ></span><span class="sxs-lookup"><span data-stu-id="7b3df-106">\<caches></span></span>  
<span data-ttu-id="7b3df-107">\<tokenReplayCache ></span><span class="sxs-lookup"><span data-stu-id="7b3df-107">\<tokenReplayCache></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b3df-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7b3df-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7b3df-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="7b3df-109">Attributes and Elements</span></span>  
 <span data-ttu-id="7b3df-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7b3df-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7b3df-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="7b3df-111">Attributes</span></span>  
  
|<span data-ttu-id="7b3df-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="7b3df-112">Attribute</span></span>|<span data-ttu-id="7b3df-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7b3df-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7b3df-114">türü</span><span class="sxs-lookup"><span data-stu-id="7b3df-114">type</span></span>|<span data-ttu-id="7b3df-115">Türetilen bir tür <xref:System.IdentityModel.Tokens.TokenReplayCache> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="7b3df-115">A type that derives from the <xref:System.IdentityModel.Tokens.TokenReplayCache> class.</span></span> <span data-ttu-id="7b3df-116">Özel bir belirtme hakkında daha fazla bilgi için `type`, [özel tür başvuruları] bakın.</span><span class="sxs-lookup"><span data-stu-id="7b3df-116">For more information about how to specify a custom `type`, see [Custom Type References].</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="7b3df-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="7b3df-117">Child Elements</span></span>  
 <span data-ttu-id="7b3df-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="7b3df-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7b3df-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="7b3df-119">Parent Elements</span></span>  
  
|<span data-ttu-id="7b3df-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="7b3df-120">Element</span></span>|<span data-ttu-id="7b3df-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7b3df-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7b3df-122">\<önbelleğe alan ></span><span class="sxs-lookup"><span data-stu-id="7b3df-122">\<caches></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|<span data-ttu-id="7b3df-123">Bir hizmeti veya bir güvenlik belirteci işleyicisi koleksiyon tarafından kullanılan önbellekleri kaydeder.</span><span class="sxs-lookup"><span data-stu-id="7b3df-123">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7b3df-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7b3df-124">Remarks</span></span>  
 <span data-ttu-id="7b3df-125">Simge tekrar yürütme önbelleğine yeniden yürütülmüş belirteçleri algılamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7b3df-125">The token replay cache is used to detect replayed tokens.</span></span> <span data-ttu-id="7b3df-126">Belirteç yeniden yürütme algılaması etkindir [ \<tokenReplayDetection >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md) ayrıca belirteçleri için en fazla süre sonu zamanı belirtir öğesi.</span><span class="sxs-lookup"><span data-stu-id="7b3df-126">Token replay detection is enabled by the [\<tokenReplayDetection>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md) element, which also specifies the maximum expiration time for tokens.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7b3df-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="7b3df-127">Example</span></span>  
 <span data-ttu-id="7b3df-128">Aşağıdaki XML yeniden yürütülmüş belirteçleri algılamak için özel bir önbellek yapılandırmasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="7b3df-128">The following XML shows the configuration of a custom cache for detecting replayed tokens.</span></span>  
  
```xml  
<caches>  
  <tokenReplayCache type="MyCacheLibrary.MyTokenReplayCache, MyCacheLibrary">  
  </tokenReplayCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7b3df-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7b3df-129">See Also</span></span>  
 <xref:System.IdentityModel.Tokens.TokenReplayCache>  
 [<span data-ttu-id="7b3df-130">\<tokenReplayDetection ></span><span class="sxs-lookup"><span data-stu-id="7b3df-130">\<tokenReplayDetection></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md)
