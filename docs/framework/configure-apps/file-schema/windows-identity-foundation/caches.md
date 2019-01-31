---
title: <caches>
ms.date: 03/30/2017
ms.assetid: 4651091b-3a20-40d8-b293-4408c0710143
author: BrucePerlerMS
ms.openlocfilehash: b1d04280ef993297102d446ba5a7db54e8404dd8
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55285668"
---
# <a name="caches"></a><span data-ttu-id="b3655-101">\<önbelleğe alan ></span><span class="sxs-lookup"><span data-stu-id="b3655-101">\<caches></span></span>
<span data-ttu-id="b3655-102">Oturum belirteçleri ve belirteç yeniden yürütme algılaması için kullanılan önbellekleri kaydeder.</span><span class="sxs-lookup"><span data-stu-id="b3655-102">Registers the caches used for session tokens and token replay detection.</span></span>  
  
 <span data-ttu-id="b3655-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="b3655-103">\<system.identityModel></span></span>  
<span data-ttu-id="b3655-104">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="b3655-104">\<identityConfiguration></span></span>  
<span data-ttu-id="b3655-105">\<önbelleğe alan ></span><span class="sxs-lookup"><span data-stu-id="b3655-105">\<caches></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3655-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b3655-106">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <caches>  
    </caches>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b3655-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="b3655-107">Attributes and Elements</span></span>  
 <span data-ttu-id="b3655-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b3655-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b3655-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b3655-109">Attributes</span></span>  
 <span data-ttu-id="b3655-110">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="b3655-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b3655-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="b3655-111">Child Elements</span></span>  
  
|<span data-ttu-id="b3655-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="b3655-112">Element</span></span>|<span data-ttu-id="b3655-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b3655-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b3655-114">\<sessionSecurityTokenCache></span><span class="sxs-lookup"><span data-stu-id="b3655-114">\<sessionSecurityTokenCache></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessionsecuritytokencache.md)|<span data-ttu-id="b3655-115">Bir hizmet ya da bir güvenlik belirteci işleyicisi koleksiyon oturumu belirteçleri için bir önbelleği kaydeder.</span><span class="sxs-lookup"><span data-stu-id="b3655-115">Registers a cache for session tokens with a service or a security token handler collection.</span></span>|  
|[<span data-ttu-id="b3655-116">\<tokenReplayCache></span><span class="sxs-lookup"><span data-stu-id="b3655-116">\<tokenReplayCache></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md)|<span data-ttu-id="b3655-117">Bir hizmet veya bir güvenlik belirteci işleyicisi koleksiyon ile bir belirteç yeniden yürütme önbelleğe kaydeder.</span><span class="sxs-lookup"><span data-stu-id="b3655-117">Registers a token replay cache with a service or a security token handler collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b3655-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="b3655-118">Parent Elements</span></span>  
  
|<span data-ttu-id="b3655-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="b3655-119">Element</span></span>|<span data-ttu-id="b3655-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b3655-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b3655-121">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="b3655-121">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="b3655-122">Hizmet düzeyi kimlik ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="b3655-122">Specifies service-level identity settings.</span></span>|  
|[<span data-ttu-id="b3655-123">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="b3655-123">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="b3655-124">Güvenlik topluluğu için yapılandırma, belirteç işleyicileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="b3655-124">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b3655-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b3655-125">Remarks</span></span>  
 <span data-ttu-id="b3655-126">A `<caches>` öğesi altında hizmet düzeyinde belirtilebilir `<identityConfiguration>` öğesi veya güvenlik belirteci işleyicisi koleksiyon düzeyi altında `<securityTokenHandlerConfiguration>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="b3655-126">A `<caches>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="b3655-127">Bir belirteci işleyicisi koleksiyon ayarlarını hizmette belirtilen geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="b3655-127">Settings on a token handler collection override those specified on the service.</span></span>  
  
 <span data-ttu-id="b3655-128">`<caches>` Öğesi tarafından temsil edilen <xref:System.IdentityModel.Configuration.IdentityModelCachesElement> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="b3655-128">The `<caches>` element is represented by the <xref:System.IdentityModel.Configuration.IdentityModelCachesElement> class.</span></span> <span data-ttu-id="b3655-129">Yapılandırılmış önbellekleri tarafından temsil edilen <xref:System.IdentityModel.Configuration.IdentityModelCaches> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="b3655-129">The configured caches are represented by the <xref:System.IdentityModel.Configuration.IdentityModelCaches> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b3655-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="b3655-130">Example</span></span>  
 <span data-ttu-id="b3655-131">Aşağıdaki XML oturumu güvenlik belirteçleri tutmak için özel bir önbellek yapılandırmasını gösterir (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span><span class="sxs-lookup"><span data-stu-id="b3655-131">The following XML shows the configuration of a custom cache for holding session security tokens (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span></span> <span data-ttu-id="b3655-132">Yapılandırma alınır `ClaimsAwareWebFarm` örnek.</span><span class="sxs-lookup"><span data-stu-id="b3655-132">The configuration is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```
