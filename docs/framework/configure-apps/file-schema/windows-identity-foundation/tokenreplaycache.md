---
title: <tokenReplayCache>
ms.date: 03/30/2017
ms.assetid: 1572ab23-6933-41b5-bfb4-0c4548145500
author: BrucePerlerMS
ms.openlocfilehash: 1567c669b5e682a7a771d7bedc95a8effa474e36
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61790513"
---
# <a name="tokenreplaycache"></a><span data-ttu-id="4bdee-101">\<tokenReplayCache></span><span class="sxs-lookup"><span data-stu-id="4bdee-101">\<tokenReplayCache></span></span>
<span data-ttu-id="4bdee-102">Bir hizmet veya bir güvenlik belirteci işleyicisi koleksiyon ile bir belirteç yeniden yürütme önbelleğe kaydeder.</span><span class="sxs-lookup"><span data-stu-id="4bdee-102">Registers a token replay cache with a service or a security token handler collection.</span></span>  
  
 <span data-ttu-id="4bdee-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="4bdee-103">\<system.identityModel></span></span>  
<span data-ttu-id="4bdee-104">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="4bdee-104">\<identityConfiguration></span></span>  
<span data-ttu-id="4bdee-105">\<önbelleğe alan ></span><span class="sxs-lookup"><span data-stu-id="4bdee-105">\<caches></span></span>  
<span data-ttu-id="4bdee-106">\<tokenReplayCache></span><span class="sxs-lookup"><span data-stu-id="4bdee-106">\<tokenReplayCache></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4bdee-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4bdee-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4bdee-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="4bdee-108">Attributes and Elements</span></span>  
 <span data-ttu-id="4bdee-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4bdee-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4bdee-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="4bdee-110">Attributes</span></span>  
  
|<span data-ttu-id="4bdee-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="4bdee-111">Attribute</span></span>|<span data-ttu-id="4bdee-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4bdee-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4bdee-113">türü</span><span class="sxs-lookup"><span data-stu-id="4bdee-113">type</span></span>|<span data-ttu-id="4bdee-114">Türetilen bir tür <xref:System.IdentityModel.Tokens.TokenReplayCache> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="4bdee-114">A type that derives from the <xref:System.IdentityModel.Tokens.TokenReplayCache> class.</span></span> <span data-ttu-id="4bdee-115">Özel bir belirtme hakkında daha fazla bilgi için `type`, [özel tür başvurularını] bakın.</span><span class="sxs-lookup"><span data-stu-id="4bdee-115">For more information about how to specify a custom `type`, see [Custom Type References].</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="4bdee-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="4bdee-116">Child Elements</span></span>  
 <span data-ttu-id="4bdee-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="4bdee-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4bdee-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="4bdee-118">Parent Elements</span></span>  
  
|<span data-ttu-id="4bdee-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="4bdee-119">Element</span></span>|<span data-ttu-id="4bdee-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4bdee-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4bdee-121">\<önbelleğe alan ></span><span class="sxs-lookup"><span data-stu-id="4bdee-121">\<caches></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|<span data-ttu-id="4bdee-122">Bir hizmet veya bir güvenlik belirteci işleyicisi koleksiyon tarafından kullanılan önbellekleri kaydeder.</span><span class="sxs-lookup"><span data-stu-id="4bdee-122">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4bdee-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4bdee-123">Remarks</span></span>  
 <span data-ttu-id="4bdee-124">Belirteç yeniden yürütme önbelleğini yeniden yürütülmüş belirteçleri algılamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4bdee-124">The token replay cache is used to detect replayed tokens.</span></span> <span data-ttu-id="4bdee-125">Belirteç yeniden yürütme algılaması etkindir [ \<tokenReplayDetection >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md) öğesi, ayrıca belirteçleri maksimum sona erme süresini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4bdee-125">Token replay detection is enabled by the [\<tokenReplayDetection>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md) element, which also specifies the maximum expiration time for tokens.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4bdee-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="4bdee-126">Example</span></span>  
 <span data-ttu-id="4bdee-127">Aşağıdaki XML yeniden yürütülmüş belirteçleri algılamak için özel bir önbellek yapılandırmasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="4bdee-127">The following XML shows the configuration of a custom cache for detecting replayed tokens.</span></span>  
  
```xml  
<caches>  
  <tokenReplayCache type="MyCacheLibrary.MyTokenReplayCache, MyCacheLibrary">  
  </tokenReplayCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4bdee-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4bdee-128">See also</span></span>

- <xref:System.IdentityModel.Tokens.TokenReplayCache>
- [<span data-ttu-id="4bdee-129">\<tokenReplayDetection ></span><span class="sxs-lookup"><span data-stu-id="4bdee-129">\<tokenReplayDetection></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md)
