---
title: '&lt;Önbellekler&gt;'
ms.date: 03/30/2017
ms.assetid: 4651091b-3a20-40d8-b293-4408c0710143
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 2a9766b826eb7a708b4b4e99b6bd984f9fc76812
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltcachesgt"></a><span data-ttu-id="8147d-102">&lt;Önbellekler&gt;</span><span class="sxs-lookup"><span data-stu-id="8147d-102">&lt;caches&gt;</span></span>
<span data-ttu-id="8147d-103">Oturum belirteçleri ve belirteç yeniden yürütme algılaması için kullanılan önbellekleri kaydeder.</span><span class="sxs-lookup"><span data-stu-id="8147d-103">Registers the caches used for session tokens and token replay detection.</span></span>  
  
 <span data-ttu-id="8147d-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="8147d-104">\<system.identityModel></span></span>  
<span data-ttu-id="8147d-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="8147d-105">\<identityConfiguration></span></span>  
<span data-ttu-id="8147d-106">\<önbelleğe alan ></span><span class="sxs-lookup"><span data-stu-id="8147d-106">\<caches></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8147d-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8147d-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <caches>  
    </caches>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8147d-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="8147d-108">Attributes and Elements</span></span>  
 <span data-ttu-id="8147d-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8147d-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8147d-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="8147d-110">Attributes</span></span>  
 <span data-ttu-id="8147d-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="8147d-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="8147d-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="8147d-112">Child Elements</span></span>  
  
|<span data-ttu-id="8147d-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="8147d-113">Element</span></span>|<span data-ttu-id="8147d-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8147d-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8147d-115">\<sessionSecurityTokenCache ></span><span class="sxs-lookup"><span data-stu-id="8147d-115">\<sessionSecurityTokenCache></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessionsecuritytokencache.md)|<span data-ttu-id="8147d-116">Bir önbellek oturum belirteçleri için bir hizmet veya bir güvenlik belirteci işleyicisi koleksiyonu ile kaydeder.</span><span class="sxs-lookup"><span data-stu-id="8147d-116">Registers a cache for session tokens with a service or a security token handler collection.</span></span>|  
|[<span data-ttu-id="8147d-117">\<tokenReplayCache ></span><span class="sxs-lookup"><span data-stu-id="8147d-117">\<tokenReplayCache></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md)|<span data-ttu-id="8147d-118">Bir hizmeti veya bir güvenlik belirteci işleyicisi koleksiyonu ile bir simge tekrar yürütme önbelleğine kaydeder.</span><span class="sxs-lookup"><span data-stu-id="8147d-118">Registers a token replay cache with a service or a security token handler collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8147d-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="8147d-119">Parent Elements</span></span>  
  
|<span data-ttu-id="8147d-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="8147d-120">Element</span></span>|<span data-ttu-id="8147d-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8147d-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8147d-122">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="8147d-122">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="8147d-123">Hizmet düzeyi kimlik ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="8147d-123">Specifies service-level identity settings.</span></span>|  
|[<span data-ttu-id="8147d-124">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="8147d-124">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="8147d-125">Güvenlik bir koleksiyon için yapılandırma belirteci işleyicileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="8147d-125">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8147d-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8147d-126">Remarks</span></span>  
 <span data-ttu-id="8147d-127">A `<caches>` öğesi altında hizmet düzeyinde belirtilebilir `<identityConfiguration>` öğesi veya güvenlik belirteci işleyicisi koleksiyon düzeyinde altında `<securityTokenHandlerConfiguration>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="8147d-127">A `<caches>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="8147d-128">Bir belirteci işleyicisi koleksiyon ayarlarını hizmette belirtilen geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="8147d-128">Settings on a token handler collection override those specified on the service.</span></span>  
  
 <span data-ttu-id="8147d-129">`<caches>` Öğesi ile temsil edilir <xref:System.IdentityModel.Configuration.IdentityModelCachesElement> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="8147d-129">The `<caches>` element is represented by the <xref:System.IdentityModel.Configuration.IdentityModelCachesElement> class.</span></span> <span data-ttu-id="8147d-130">Yapılandırılmış önbellekleri tarafından temsil edilen <xref:System.IdentityModel.Configuration.IdentityModelCaches> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="8147d-130">The configured caches are represented by the <xref:System.IdentityModel.Configuration.IdentityModelCaches> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8147d-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="8147d-131">Example</span></span>  
 <span data-ttu-id="8147d-132">Aşağıdaki XML güvenlik belirteçleri oturum tutmak için özel bir önbellek yapılandırma gösterir (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span><span class="sxs-lookup"><span data-stu-id="8147d-132">The following XML shows the configuration of a custom cache for holding session security tokens (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span></span> <span data-ttu-id="8147d-133">Yapılandırma alınırlar `ClaimsAwareWebFarm` örnek.</span><span class="sxs-lookup"><span data-stu-id="8147d-133">The configuration is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```
