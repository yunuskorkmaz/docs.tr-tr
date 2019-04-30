---
title: <caches>
ms.date: 03/30/2017
ms.assetid: 4651091b-3a20-40d8-b293-4408c0710143
author: BrucePerlerMS
ms.openlocfilehash: b1d04280ef993297102d446ba5a7db54e8404dd8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61750793"
---
# <a name="caches"></a><span data-ttu-id="4ef4b-101">\<önbelleğe alan ></span><span class="sxs-lookup"><span data-stu-id="4ef4b-101">\<caches></span></span>
<span data-ttu-id="4ef4b-102">Oturum belirteçleri ve belirteç yeniden yürütme algılaması için kullanılan önbellekleri kaydeder.</span><span class="sxs-lookup"><span data-stu-id="4ef4b-102">Registers the caches used for session tokens and token replay detection.</span></span>  
  
 <span data-ttu-id="4ef4b-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="4ef4b-103">\<system.identityModel></span></span>  
<span data-ttu-id="4ef4b-104">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="4ef4b-104">\<identityConfiguration></span></span>  
<span data-ttu-id="4ef4b-105">\<önbelleğe alan ></span><span class="sxs-lookup"><span data-stu-id="4ef4b-105">\<caches></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ef4b-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4ef4b-106">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <caches>  
    </caches>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4ef4b-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="4ef4b-107">Attributes and Elements</span></span>  
 <span data-ttu-id="4ef4b-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4ef4b-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4ef4b-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="4ef4b-109">Attributes</span></span>  
 <span data-ttu-id="4ef4b-110">None</span><span class="sxs-lookup"><span data-stu-id="4ef4b-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4ef4b-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="4ef4b-111">Child Elements</span></span>  
  
|<span data-ttu-id="4ef4b-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="4ef4b-112">Element</span></span>|<span data-ttu-id="4ef4b-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4ef4b-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4ef4b-114">\<sessionSecurityTokenCache></span><span class="sxs-lookup"><span data-stu-id="4ef4b-114">\<sessionSecurityTokenCache></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessionsecuritytokencache.md)|<span data-ttu-id="4ef4b-115">Bir hizmet ya da bir güvenlik belirteci işleyicisi koleksiyon oturumu belirteçleri için bir önbelleği kaydeder.</span><span class="sxs-lookup"><span data-stu-id="4ef4b-115">Registers a cache for session tokens with a service or a security token handler collection.</span></span>|  
|[<span data-ttu-id="4ef4b-116">\<tokenReplayCache></span><span class="sxs-lookup"><span data-stu-id="4ef4b-116">\<tokenReplayCache></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md)|<span data-ttu-id="4ef4b-117">Bir hizmet veya bir güvenlik belirteci işleyicisi koleksiyon ile bir belirteç yeniden yürütme önbelleğe kaydeder.</span><span class="sxs-lookup"><span data-stu-id="4ef4b-117">Registers a token replay cache with a service or a security token handler collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4ef4b-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="4ef4b-118">Parent Elements</span></span>  
  
|<span data-ttu-id="4ef4b-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="4ef4b-119">Element</span></span>|<span data-ttu-id="4ef4b-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4ef4b-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4ef4b-121">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="4ef4b-121">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="4ef4b-122">Hizmet düzeyi kimlik ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="4ef4b-122">Specifies service-level identity settings.</span></span>|  
|[<span data-ttu-id="4ef4b-123">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="4ef4b-123">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="4ef4b-124">Güvenlik topluluğu için yapılandırma, belirteç işleyicileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="4ef4b-124">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4ef4b-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4ef4b-125">Remarks</span></span>  
 <span data-ttu-id="4ef4b-126">A `<caches>` öğesi altında hizmet düzeyinde belirtilebilir `<identityConfiguration>` öğesi veya güvenlik belirteci işleyicisi koleksiyon düzeyi altında `<securityTokenHandlerConfiguration>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="4ef4b-126">A `<caches>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="4ef4b-127">Bir belirteci işleyicisi koleksiyon ayarlarını hizmette belirtilen geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="4ef4b-127">Settings on a token handler collection override those specified on the service.</span></span>  
  
 <span data-ttu-id="4ef4b-128">`<caches>` Öğesi tarafından temsil edilen <xref:System.IdentityModel.Configuration.IdentityModelCachesElement> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="4ef4b-128">The `<caches>` element is represented by the <xref:System.IdentityModel.Configuration.IdentityModelCachesElement> class.</span></span> <span data-ttu-id="4ef4b-129">Yapılandırılmış önbellekleri tarafından temsil edilen <xref:System.IdentityModel.Configuration.IdentityModelCaches> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="4ef4b-129">The configured caches are represented by the <xref:System.IdentityModel.Configuration.IdentityModelCaches> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4ef4b-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="4ef4b-130">Example</span></span>  
 <span data-ttu-id="4ef4b-131">Aşağıdaki XML oturumu güvenlik belirteçleri tutmak için özel bir önbellek yapılandırmasını gösterir (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span><span class="sxs-lookup"><span data-stu-id="4ef4b-131">The following XML shows the configuration of a custom cache for holding session security tokens (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span></span> <span data-ttu-id="4ef4b-132">Yapılandırma alınır `ClaimsAwareWebFarm` örnek.</span><span class="sxs-lookup"><span data-stu-id="4ef4b-132">The configuration is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```
