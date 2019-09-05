---
title: <caches>
ms.date: 03/30/2017
ms.assetid: 4651091b-3a20-40d8-b293-4408c0710143
author: BrucePerlerMS
ms.openlocfilehash: 80f435b52fd7657c5cd44538028d6080beffe0b5
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252157"
---
# <a name="caches"></a><span data-ttu-id="9a1e2-101">\<önbellekler ></span><span class="sxs-lookup"><span data-stu-id="9a1e2-101">\<caches></span></span>
<span data-ttu-id="9a1e2-102">Oturum belirteçleri ve belirteci yeniden yürütme algılaması için kullanılan önbellekleri kaydeder.</span><span class="sxs-lookup"><span data-stu-id="9a1e2-102">Registers the caches used for session tokens and token replay detection.</span></span>  
  
<span data-ttu-id="9a1e2-103">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="9a1e2-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="9a1e2-104">&nbsp;&nbsp;[ **\<System. IdentityModel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="9a1e2-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="9a1e2-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<IdentityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="9a1e2-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="9a1e2-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<önbellekler >**</span><span class="sxs-lookup"><span data-stu-id="9a1e2-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<caches>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a1e2-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9a1e2-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <caches>  
    </caches>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9a1e2-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="9a1e2-108">Attributes and Elements</span></span>  
 <span data-ttu-id="9a1e2-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9a1e2-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9a1e2-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="9a1e2-110">Attributes</span></span>  
 <span data-ttu-id="9a1e2-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="9a1e2-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9a1e2-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="9a1e2-112">Child Elements</span></span>  
  
|<span data-ttu-id="9a1e2-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="9a1e2-113">Element</span></span>|<span data-ttu-id="9a1e2-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9a1e2-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9a1e2-115">\<sessionSecurityTokenCache ></span><span class="sxs-lookup"><span data-stu-id="9a1e2-115">\<sessionSecurityTokenCache></span></span>](sessionsecuritytokencache.md)|<span data-ttu-id="9a1e2-116">Bir hizmet veya güvenlik belirteci işleyici koleksiyonuyla oturum belirteçleri için bir önbellek kaydeder.</span><span class="sxs-lookup"><span data-stu-id="9a1e2-116">Registers a cache for session tokens with a service or a security token handler collection.</span></span>|  
|[<span data-ttu-id="9a1e2-117">\<tokenReplayCache ></span><span class="sxs-lookup"><span data-stu-id="9a1e2-117">\<tokenReplayCache></span></span>](tokenreplaycache.md)|<span data-ttu-id="9a1e2-118">Belirteç yeniden yürütme önbelleğini bir hizmet veya güvenlik belirteci işleyici koleksiyonuyla kaydeder.</span><span class="sxs-lookup"><span data-stu-id="9a1e2-118">Registers a token replay cache with a service or a security token handler collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9a1e2-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="9a1e2-119">Parent Elements</span></span>  
  
|<span data-ttu-id="9a1e2-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="9a1e2-120">Element</span></span>|<span data-ttu-id="9a1e2-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9a1e2-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9a1e2-122">\<IdentityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="9a1e2-122">\<identityConfiguration></span></span>](identityconfiguration.md)|<span data-ttu-id="9a1e2-123">Hizmet düzeyi kimlik ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="9a1e2-123">Specifies service-level identity settings.</span></span>|  
|[<span data-ttu-id="9a1e2-124">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="9a1e2-124">\<securityTokenHandlerConfiguration></span></span>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="9a1e2-125">Bir güvenlik belirteci işleyicileri koleksiyonu için yapılandırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="9a1e2-125">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9a1e2-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9a1e2-126">Remarks</span></span>  
 <span data-ttu-id="9a1e2-127">Öğesi, `<identityConfiguration>` öğesinin altındaki hizmet düzeyinde veya öğesinin altındaki `<securityTokenHandlerConfiguration>` güvenlik belirteci işleyicisi koleksiyonu düzeyinde belirtilebilir. `<caches>`</span><span class="sxs-lookup"><span data-stu-id="9a1e2-127">A `<caches>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="9a1e2-128">Belirteç işleyici koleksiyonundaki ayarlar, hizmette belirtilen ayarları geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="9a1e2-128">Settings on a token handler collection override those specified on the service.</span></span>  
  
 <span data-ttu-id="9a1e2-129">`<caches>` Öğesi sınıfı<xref:System.IdentityModel.Configuration.IdentityModelCachesElement> tarafından temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="9a1e2-129">The `<caches>` element is represented by the <xref:System.IdentityModel.Configuration.IdentityModelCachesElement> class.</span></span> <span data-ttu-id="9a1e2-130">Yapılandırılan önbellekler <xref:System.IdentityModel.Configuration.IdentityModelCaches> sınıfı tarafından temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="9a1e2-130">The configured caches are represented by the <xref:System.IdentityModel.Configuration.IdentityModelCaches> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9a1e2-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="9a1e2-131">Example</span></span>  
 <span data-ttu-id="9a1e2-132">Aşağıdaki XML, oturum güvenlik belirteçlerini (<xref:System.IdentityModel.Tokens.SessionSecurityToken>) tutmak için özel bir önbelleğin yapılandırmasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="9a1e2-132">The following XML shows the configuration of a custom cache for holding session security tokens (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span></span> <span data-ttu-id="9a1e2-133">Yapılandırma `ClaimsAwareWebFarm` örnekten alınır.</span><span class="sxs-lookup"><span data-stu-id="9a1e2-133">The configuration is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```
