---
title: '&lt;Önbellekler&gt;'
ms.date: 03/30/2017
ms.assetid: 4651091b-3a20-40d8-b293-4408c0710143
author: BrucePerlerMS
ms.openlocfilehash: a91a389e53354e4f5b26e1510fc2f025300d65cc
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47192686"
---
# <a name="ltcachesgt"></a><span data-ttu-id="31b8e-102">&lt;Önbellekler&gt;</span><span class="sxs-lookup"><span data-stu-id="31b8e-102">&lt;caches&gt;</span></span>
<span data-ttu-id="31b8e-103">Oturum belirteçleri ve belirteç yeniden yürütme algılaması için kullanılan önbellekleri kaydeder.</span><span class="sxs-lookup"><span data-stu-id="31b8e-103">Registers the caches used for session tokens and token replay detection.</span></span>  
  
 <span data-ttu-id="31b8e-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="31b8e-104">\<system.identityModel></span></span>  
<span data-ttu-id="31b8e-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="31b8e-105">\<identityConfiguration></span></span>  
<span data-ttu-id="31b8e-106">\<önbelleğe alan ></span><span class="sxs-lookup"><span data-stu-id="31b8e-106">\<caches></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31b8e-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="31b8e-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <caches>  
    </caches>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="31b8e-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="31b8e-108">Attributes and Elements</span></span>  
 <span data-ttu-id="31b8e-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="31b8e-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="31b8e-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="31b8e-110">Attributes</span></span>  
 <span data-ttu-id="31b8e-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="31b8e-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="31b8e-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="31b8e-112">Child Elements</span></span>  
  
|<span data-ttu-id="31b8e-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="31b8e-113">Element</span></span>|<span data-ttu-id="31b8e-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="31b8e-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="31b8e-115">\<sessionSecurityTokenCache ></span><span class="sxs-lookup"><span data-stu-id="31b8e-115">\<sessionSecurityTokenCache></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessionsecuritytokencache.md)|<span data-ttu-id="31b8e-116">Bir hizmet ya da bir güvenlik belirteci işleyicisi koleksiyon oturumu belirteçleri için bir önbelleği kaydeder.</span><span class="sxs-lookup"><span data-stu-id="31b8e-116">Registers a cache for session tokens with a service or a security token handler collection.</span></span>|  
|[<span data-ttu-id="31b8e-117">\<tokenReplayCache ></span><span class="sxs-lookup"><span data-stu-id="31b8e-117">\<tokenReplayCache></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md)|<span data-ttu-id="31b8e-118">Bir hizmet veya bir güvenlik belirteci işleyicisi koleksiyon ile bir belirteç yeniden yürütme önbelleğe kaydeder.</span><span class="sxs-lookup"><span data-stu-id="31b8e-118">Registers a token replay cache with a service or a security token handler collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="31b8e-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="31b8e-119">Parent Elements</span></span>  
  
|<span data-ttu-id="31b8e-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="31b8e-120">Element</span></span>|<span data-ttu-id="31b8e-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="31b8e-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="31b8e-122">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="31b8e-122">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="31b8e-123">Hizmet düzeyi kimlik ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="31b8e-123">Specifies service-level identity settings.</span></span>|  
|[<span data-ttu-id="31b8e-124">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="31b8e-124">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="31b8e-125">Güvenlik topluluğu için yapılandırma, belirteç işleyicileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="31b8e-125">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="31b8e-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="31b8e-126">Remarks</span></span>  
 <span data-ttu-id="31b8e-127">A `<caches>` öğesi altında hizmet düzeyinde belirtilebilir `<identityConfiguration>` öğesi veya güvenlik belirteci işleyicisi koleksiyon düzeyi altında `<securityTokenHandlerConfiguration>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="31b8e-127">A `<caches>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="31b8e-128">Bir belirteci işleyicisi koleksiyon ayarlarını hizmette belirtilen geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="31b8e-128">Settings on a token handler collection override those specified on the service.</span></span>  
  
 <span data-ttu-id="31b8e-129">`<caches>` Öğesi tarafından temsil edilen <xref:System.IdentityModel.Configuration.IdentityModelCachesElement> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="31b8e-129">The `<caches>` element is represented by the <xref:System.IdentityModel.Configuration.IdentityModelCachesElement> class.</span></span> <span data-ttu-id="31b8e-130">Yapılandırılmış önbellekleri tarafından temsil edilen <xref:System.IdentityModel.Configuration.IdentityModelCaches> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="31b8e-130">The configured caches are represented by the <xref:System.IdentityModel.Configuration.IdentityModelCaches> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="31b8e-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="31b8e-131">Example</span></span>  
 <span data-ttu-id="31b8e-132">Aşağıdaki XML oturumu güvenlik belirteçleri tutmak için özel bir önbellek yapılandırmasını gösterir (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span><span class="sxs-lookup"><span data-stu-id="31b8e-132">The following XML shows the configuration of a custom cache for holding session security tokens (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span></span> <span data-ttu-id="31b8e-133">Yapılandırma alınır `ClaimsAwareWebFarm` örnek.</span><span class="sxs-lookup"><span data-stu-id="31b8e-133">The configuration is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```
