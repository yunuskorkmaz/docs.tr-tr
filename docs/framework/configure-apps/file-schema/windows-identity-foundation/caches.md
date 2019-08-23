---
title: <caches>
ms.date: 03/30/2017
ms.assetid: 4651091b-3a20-40d8-b293-4408c0710143
author: BrucePerlerMS
ms.openlocfilehash: 5ad75ae18772d6e7c724f2cbf40c1e3083d5c345
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941974"
---
# <a name="caches"></a><span data-ttu-id="d0af9-101">\<önbellekler ></span><span class="sxs-lookup"><span data-stu-id="d0af9-101">\<caches></span></span>
<span data-ttu-id="d0af9-102">Oturum belirteçleri ve belirteci yeniden yürütme algılaması için kullanılan önbellekleri kaydeder.</span><span class="sxs-lookup"><span data-stu-id="d0af9-102">Registers the caches used for session tokens and token replay detection.</span></span>  
  
 <span data-ttu-id="d0af9-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="d0af9-103">\<system.identityModel></span></span>  
<span data-ttu-id="d0af9-104">\<IdentityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="d0af9-104">\<identityConfiguration></span></span>  
<span data-ttu-id="d0af9-105">\<önbellekler ></span><span class="sxs-lookup"><span data-stu-id="d0af9-105">\<caches></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0af9-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d0af9-106">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <caches>  
    </caches>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d0af9-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d0af9-107">Attributes and Elements</span></span>  
 <span data-ttu-id="d0af9-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d0af9-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d0af9-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d0af9-109">Attributes</span></span>  
 <span data-ttu-id="d0af9-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="d0af9-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d0af9-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d0af9-111">Child Elements</span></span>  
  
|<span data-ttu-id="d0af9-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="d0af9-112">Element</span></span>|<span data-ttu-id="d0af9-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d0af9-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d0af9-114">\<sessionSecurityTokenCache ></span><span class="sxs-lookup"><span data-stu-id="d0af9-114">\<sessionSecurityTokenCache></span></span>](sessionsecuritytokencache.md)|<span data-ttu-id="d0af9-115">Bir hizmet veya güvenlik belirteci işleyici koleksiyonuyla oturum belirteçleri için bir önbellek kaydeder.</span><span class="sxs-lookup"><span data-stu-id="d0af9-115">Registers a cache for session tokens with a service or a security token handler collection.</span></span>|  
|[<span data-ttu-id="d0af9-116">\<tokenReplayCache ></span><span class="sxs-lookup"><span data-stu-id="d0af9-116">\<tokenReplayCache></span></span>](tokenreplaycache.md)|<span data-ttu-id="d0af9-117">Belirteç yeniden yürütme önbelleğini bir hizmet veya güvenlik belirteci işleyici koleksiyonuyla kaydeder.</span><span class="sxs-lookup"><span data-stu-id="d0af9-117">Registers a token replay cache with a service or a security token handler collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d0af9-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d0af9-118">Parent Elements</span></span>  
  
|<span data-ttu-id="d0af9-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="d0af9-119">Element</span></span>|<span data-ttu-id="d0af9-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d0af9-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d0af9-121">\<IdentityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="d0af9-121">\<identityConfiguration></span></span>](identityconfiguration.md)|<span data-ttu-id="d0af9-122">Hizmet düzeyi kimlik ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d0af9-122">Specifies service-level identity settings.</span></span>|  
|[<span data-ttu-id="d0af9-123">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="d0af9-123">\<securityTokenHandlerConfiguration></span></span>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="d0af9-124">Bir güvenlik belirteci işleyicileri koleksiyonu için yapılandırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="d0af9-124">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d0af9-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d0af9-125">Remarks</span></span>  
 <span data-ttu-id="d0af9-126">Öğesi, `<identityConfiguration>` öğesinin altındaki hizmet düzeyinde veya öğesinin altındaki `<securityTokenHandlerConfiguration>` güvenlik belirteci işleyicisi koleksiyonu düzeyinde belirtilebilir. `<caches>`</span><span class="sxs-lookup"><span data-stu-id="d0af9-126">A `<caches>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="d0af9-127">Belirteç işleyici koleksiyonundaki ayarlar, hizmette belirtilen ayarları geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="d0af9-127">Settings on a token handler collection override those specified on the service.</span></span>  
  
 <span data-ttu-id="d0af9-128">`<caches>` Öğesi sınıfı<xref:System.IdentityModel.Configuration.IdentityModelCachesElement> tarafından temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="d0af9-128">The `<caches>` element is represented by the <xref:System.IdentityModel.Configuration.IdentityModelCachesElement> class.</span></span> <span data-ttu-id="d0af9-129">Yapılandırılan önbellekler <xref:System.IdentityModel.Configuration.IdentityModelCaches> sınıfı tarafından temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="d0af9-129">The configured caches are represented by the <xref:System.IdentityModel.Configuration.IdentityModelCaches> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d0af9-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="d0af9-130">Example</span></span>  
 <span data-ttu-id="d0af9-131">Aşağıdaki XML, oturum güvenlik belirteçlerini (<xref:System.IdentityModel.Tokens.SessionSecurityToken>) tutmak için özel bir önbelleğin yapılandırmasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d0af9-131">The following XML shows the configuration of a custom cache for holding session security tokens (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span></span> <span data-ttu-id="d0af9-132">Yapılandırma `ClaimsAwareWebFarm` örnekten alınır.</span><span class="sxs-lookup"><span data-stu-id="d0af9-132">The configuration is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```
