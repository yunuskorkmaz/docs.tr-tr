---
title: '&lt;tokenReplayCache&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1572ab23-6933-41b5-bfb4-0c4548145500
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: e43e79416ddb8862cbc6e52d9d449a02b123af83
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="lttokenreplaycachegt"></a><span data-ttu-id="3135a-102">&lt;tokenReplayCache&gt;</span><span class="sxs-lookup"><span data-stu-id="3135a-102">&lt;tokenReplayCache&gt;</span></span>
<span data-ttu-id="3135a-103">Bir hizmeti veya bir güvenlik belirteci işleyicisi koleksiyonu ile bir simge tekrar yürütme önbelleğine kaydeder.</span><span class="sxs-lookup"><span data-stu-id="3135a-103">Registers a token replay cache with a service or a security token handler collection.</span></span>  
  
 <span data-ttu-id="3135a-104">\<System.IdentityModel ></span><span class="sxs-lookup"><span data-stu-id="3135a-104">\<system.identityModel></span></span>  
<span data-ttu-id="3135a-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="3135a-105">\<identityConfiguration></span></span>  
<span data-ttu-id="3135a-106">\<önbelleğe alan ></span><span class="sxs-lookup"><span data-stu-id="3135a-106">\<caches></span></span>  
<span data-ttu-id="3135a-107">\<tokenReplayCache ></span><span class="sxs-lookup"><span data-stu-id="3135a-107">\<tokenReplayCache></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3135a-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3135a-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3135a-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="3135a-109">Attributes and Elements</span></span>  
 <span data-ttu-id="3135a-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3135a-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3135a-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3135a-111">Attributes</span></span>  
  
|<span data-ttu-id="3135a-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="3135a-112">Attribute</span></span>|<span data-ttu-id="3135a-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3135a-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3135a-114">türü</span><span class="sxs-lookup"><span data-stu-id="3135a-114">type</span></span>|<span data-ttu-id="3135a-115">Türetilen bir tür <xref:System.IdentityModel.Tokens.TokenReplayCache> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="3135a-115">A type that derives from the <xref:System.IdentityModel.Tokens.TokenReplayCache> class.</span></span> <span data-ttu-id="3135a-116">Özel bir belirtme hakkında daha fazla bilgi için `type`, [özel tür başvuruları] bakın.</span><span class="sxs-lookup"><span data-stu-id="3135a-116">For more information about how to specify a custom `type`, see [Custom Type References].</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="3135a-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="3135a-117">Child Elements</span></span>  
 <span data-ttu-id="3135a-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="3135a-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3135a-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="3135a-119">Parent Elements</span></span>  
  
|<span data-ttu-id="3135a-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="3135a-120">Element</span></span>|<span data-ttu-id="3135a-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3135a-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3135a-122">\<önbelleğe alan ></span><span class="sxs-lookup"><span data-stu-id="3135a-122">\<caches></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|<span data-ttu-id="3135a-123">Bir hizmeti veya bir güvenlik belirteci işleyicisi koleksiyon tarafından kullanılan önbellekleri kaydeder.</span><span class="sxs-lookup"><span data-stu-id="3135a-123">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3135a-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3135a-124">Remarks</span></span>  
 <span data-ttu-id="3135a-125">Simge tekrar yürütme önbelleğine yeniden yürütülmüş belirteçleri algılamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3135a-125">The token replay cache is used to detect replayed tokens.</span></span> <span data-ttu-id="3135a-126">Belirteç yeniden yürütme algılaması etkindir [ \<tokenReplayDetection >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md) ayrıca belirteçleri için en fazla süre sonu zamanı belirtir öğesi.</span><span class="sxs-lookup"><span data-stu-id="3135a-126">Token replay detection is enabled by the [\<tokenReplayDetection>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md) element, which also specifies the maximum expiration time for tokens.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3135a-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="3135a-127">Example</span></span>  
 <span data-ttu-id="3135a-128">Aşağıdaki XML yeniden yürütülmüş belirteçleri algılamak için özel bir önbellek yapılandırmasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="3135a-128">The following XML shows the configuration of a custom cache for detecting replayed tokens.</span></span>  
  
```xml  
<caches>  
  <tokenReplayCache type="MyCacheLibrary.MyTokenReplayCache, MyCacheLibrary">  
  </tokenReplayCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3135a-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3135a-129">See Also</span></span>  
 <xref:System.IdentityModel.Tokens.TokenReplayCache>  
 [<span data-ttu-id="3135a-130">\<tokenReplayDetection ></span><span class="sxs-lookup"><span data-stu-id="3135a-130">\<tokenReplayDetection></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md)
