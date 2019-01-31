---
title: <tokenReplayCache>
ms.date: 03/30/2017
ms.assetid: 1572ab23-6933-41b5-bfb4-0c4548145500
author: BrucePerlerMS
ms.openlocfilehash: dfa6c0d84582d55595f00f149adfdcaa9d554d6b
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55271960"
---
# <a name="tokenreplaycache"></a><span data-ttu-id="9d394-101">\<tokenReplayCache></span><span class="sxs-lookup"><span data-stu-id="9d394-101">\<tokenReplayCache></span></span>
<span data-ttu-id="9d394-102">Bir hizmet veya bir güvenlik belirteci işleyicisi koleksiyon ile bir belirteç yeniden yürütme önbelleğe kaydeder.</span><span class="sxs-lookup"><span data-stu-id="9d394-102">Registers a token replay cache with a service or a security token handler collection.</span></span>  
  
 <span data-ttu-id="9d394-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="9d394-103">\<system.identityModel></span></span>  
<span data-ttu-id="9d394-104">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="9d394-104">\<identityConfiguration></span></span>  
<span data-ttu-id="9d394-105">\<önbelleğe alan ></span><span class="sxs-lookup"><span data-stu-id="9d394-105">\<caches></span></span>  
<span data-ttu-id="9d394-106">\<tokenReplayCache></span><span class="sxs-lookup"><span data-stu-id="9d394-106">\<tokenReplayCache></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d394-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9d394-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9d394-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="9d394-108">Attributes and Elements</span></span>  
 <span data-ttu-id="9d394-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9d394-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9d394-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="9d394-110">Attributes</span></span>  
  
|<span data-ttu-id="9d394-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="9d394-111">Attribute</span></span>|<span data-ttu-id="9d394-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9d394-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9d394-113">türü</span><span class="sxs-lookup"><span data-stu-id="9d394-113">type</span></span>|<span data-ttu-id="9d394-114">Türetilen bir tür <xref:System.IdentityModel.Tokens.TokenReplayCache> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="9d394-114">A type that derives from the <xref:System.IdentityModel.Tokens.TokenReplayCache> class.</span></span> <span data-ttu-id="9d394-115">Özel bir belirtme hakkında daha fazla bilgi için `type`, [özel tür başvurularını] bakın.</span><span class="sxs-lookup"><span data-stu-id="9d394-115">For more information about how to specify a custom `type`, see [Custom Type References].</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="9d394-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="9d394-116">Child Elements</span></span>  
 <span data-ttu-id="9d394-117">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="9d394-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9d394-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="9d394-118">Parent Elements</span></span>  
  
|<span data-ttu-id="9d394-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="9d394-119">Element</span></span>|<span data-ttu-id="9d394-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9d394-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9d394-121">\<önbelleğe alan ></span><span class="sxs-lookup"><span data-stu-id="9d394-121">\<caches></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|<span data-ttu-id="9d394-122">Bir hizmet veya bir güvenlik belirteci işleyicisi koleksiyon tarafından kullanılan önbellekleri kaydeder.</span><span class="sxs-lookup"><span data-stu-id="9d394-122">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9d394-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9d394-123">Remarks</span></span>  
 <span data-ttu-id="9d394-124">Belirteç yeniden yürütme önbelleğini yeniden yürütülmüş belirteçleri algılamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9d394-124">The token replay cache is used to detect replayed tokens.</span></span> <span data-ttu-id="9d394-125">Belirteç yeniden yürütme algılaması etkindir [ \<tokenReplayDetection >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md) öğesi, ayrıca belirteçleri maksimum sona erme süresini belirtir.</span><span class="sxs-lookup"><span data-stu-id="9d394-125">Token replay detection is enabled by the [\<tokenReplayDetection>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md) element, which also specifies the maximum expiration time for tokens.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9d394-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="9d394-126">Example</span></span>  
 <span data-ttu-id="9d394-127">Aşağıdaki XML yeniden yürütülmüş belirteçleri algılamak için özel bir önbellek yapılandırmasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="9d394-127">The following XML shows the configuration of a custom cache for detecting replayed tokens.</span></span>  
  
```xml  
<caches>  
  <tokenReplayCache type="MyCacheLibrary.MyTokenReplayCache, MyCacheLibrary">  
  </tokenReplayCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9d394-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9d394-128">See also</span></span>
- <xref:System.IdentityModel.Tokens.TokenReplayCache>
- [<span data-ttu-id="9d394-129">\<tokenReplayDetection ></span><span class="sxs-lookup"><span data-stu-id="9d394-129">\<tokenReplayDetection></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md)
