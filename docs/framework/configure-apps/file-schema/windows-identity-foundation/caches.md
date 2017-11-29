---
title: "&lt;önbellekler&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4651091b-3a20-40d8-b293-4408c0710143
caps.latest.revision: "7"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: f0c46532cb7716f4dc066f0e96c14534d7fa0b42
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="ltcachesgt"></a><span data-ttu-id="a3925-102">&lt;önbellekler&gt;</span><span class="sxs-lookup"><span data-stu-id="a3925-102">&lt;caches&gt;</span></span>
<span data-ttu-id="a3925-103">Oturum belirteçleri ve belirteç yeniden yürütme algılaması için kullanılan önbellekleri kaydeder.</span><span class="sxs-lookup"><span data-stu-id="a3925-103">Registers the caches used for session tokens and token replay detection.</span></span>  
  
 <span data-ttu-id="a3925-104">\<System.IdentityModel ></span><span class="sxs-lookup"><span data-stu-id="a3925-104">\<system.identityModel></span></span>  
<span data-ttu-id="a3925-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="a3925-105">\<identityConfiguration></span></span>  
<span data-ttu-id="a3925-106">\<önbelleğe alan ></span><span class="sxs-lookup"><span data-stu-id="a3925-106">\<caches></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3925-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a3925-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <caches>  
    </caches>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a3925-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a3925-108">Attributes and Elements</span></span>  
 <span data-ttu-id="a3925-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a3925-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a3925-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a3925-110">Attributes</span></span>  
 <span data-ttu-id="a3925-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="a3925-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a3925-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a3925-112">Child Elements</span></span>  
  
|<span data-ttu-id="a3925-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="a3925-113">Element</span></span>|<span data-ttu-id="a3925-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a3925-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a3925-115">\<sessionSecurityTokenCache ></span><span class="sxs-lookup"><span data-stu-id="a3925-115">\<sessionSecurityTokenCache></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessionsecuritytokencache.md)|<span data-ttu-id="a3925-116">Bir önbellek oturum belirteçleri için bir hizmet veya bir güvenlik belirteci işleyicisi koleksiyonu ile kaydeder.</span><span class="sxs-lookup"><span data-stu-id="a3925-116">Registers a cache for session tokens with a service or a security token handler collection.</span></span>|  
|[<span data-ttu-id="a3925-117">\<tokenReplayCache ></span><span class="sxs-lookup"><span data-stu-id="a3925-117">\<tokenReplayCache></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md)|<span data-ttu-id="a3925-118">Bir hizmeti veya bir güvenlik belirteci işleyicisi koleksiyonu ile bir simge tekrar yürütme önbelleğine kaydeder.</span><span class="sxs-lookup"><span data-stu-id="a3925-118">Registers a token replay cache with a service or a security token handler collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a3925-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a3925-119">Parent Elements</span></span>  
  
|<span data-ttu-id="a3925-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="a3925-120">Element</span></span>|<span data-ttu-id="a3925-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a3925-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a3925-122">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="a3925-122">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="a3925-123">Hizmet düzeyi kimlik ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a3925-123">Specifies service-level identity settings.</span></span>|  
|[<span data-ttu-id="a3925-124">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="a3925-124">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="a3925-125">Güvenlik bir koleksiyon için yapılandırma belirteci işleyicileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="a3925-125">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a3925-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a3925-126">Remarks</span></span>  
 <span data-ttu-id="a3925-127">A `<caches>` öğesi altında hizmet düzeyinde belirtilebilir `<identityConfiguration>` öğesi veya güvenlik belirteci işleyicisi koleksiyon düzeyinde altında `<securityTokenHandlerConfiguration>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="a3925-127">A `<caches>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="a3925-128">Bir belirteci işleyicisi koleksiyon ayarlarını hizmette belirtilen geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="a3925-128">Settings on a token handler collection override those specified on the service.</span></span>  
  
 <span data-ttu-id="a3925-129">`<caches>` Öğesi ile temsil edilir <xref:System.IdentityModel.Configuration.IdentityModelCachesElement> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="a3925-129">The `<caches>` element is represented by the <xref:System.IdentityModel.Configuration.IdentityModelCachesElement> class.</span></span> <span data-ttu-id="a3925-130">Yapılandırılmış önbellekleri tarafından temsil edilen <xref:System.IdentityModel.Configuration.IdentityModelCaches> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="a3925-130">The configured caches are represented by the <xref:System.IdentityModel.Configuration.IdentityModelCaches> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a3925-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="a3925-131">Example</span></span>  
 <span data-ttu-id="a3925-132">Aşağıdaki XML güvenlik belirteçleri oturum tutmak için özel bir önbellek yapılandırma gösterir (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span><span class="sxs-lookup"><span data-stu-id="a3925-132">The following XML shows the configuration of a custom cache for holding session security tokens (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span></span> <span data-ttu-id="a3925-133">Yapılandırma alınırlar `ClaimsAwareWebFarm` örnek.</span><span class="sxs-lookup"><span data-stu-id="a3925-133">The configuration is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```
