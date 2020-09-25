---
title: <caches>
ms.date: 03/30/2017
ms.assetid: 4651091b-3a20-40d8-b293-4408c0710143
author: BrucePerlerMS
ms.openlocfilehash: 791c5be8aa48db2b17a42a216ad2bf5e7b5a4bc1
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91189883"
---
# \<caches>

<span data-ttu-id="71e03-101">Oturum belirteçleri ve belirteci yeniden yürütme algılaması için kullanılan önbellekleri kaydeder.</span><span class="sxs-lookup"><span data-stu-id="71e03-101">Registers the caches used for session tokens and token replay detection.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<caches>**  
  
## <a name="syntax"></a><span data-ttu-id="71e03-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="71e03-102">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <caches>  
    </caches>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="71e03-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="71e03-103">Attributes and Elements</span></span>  

 <span data-ttu-id="71e03-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="71e03-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="71e03-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="71e03-105">Attributes</span></span>  

 <span data-ttu-id="71e03-106">Yok</span><span class="sxs-lookup"><span data-stu-id="71e03-106">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="71e03-107">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="71e03-107">Child Elements</span></span>  
  
|<span data-ttu-id="71e03-108">Öğe</span><span class="sxs-lookup"><span data-stu-id="71e03-108">Element</span></span>|<span data-ttu-id="71e03-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="71e03-109">Description</span></span>|  
|-------------|-----------------|  
|[\<sessionSecurityTokenCache>](sessionsecuritytokencache.md)|<span data-ttu-id="71e03-110">Bir hizmet veya güvenlik belirteci işleyici koleksiyonuyla oturum belirteçleri için bir önbellek kaydeder.</span><span class="sxs-lookup"><span data-stu-id="71e03-110">Registers a cache for session tokens with a service or a security token handler collection.</span></span>|  
|[\<tokenReplayCache>](tokenreplaycache.md)|<span data-ttu-id="71e03-111">Belirteç yeniden yürütme önbelleğini bir hizmet veya güvenlik belirteci işleyici koleksiyonuyla kaydeder.</span><span class="sxs-lookup"><span data-stu-id="71e03-111">Registers a token replay cache with a service or a security token handler collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="71e03-112">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="71e03-112">Parent Elements</span></span>  
  
|<span data-ttu-id="71e03-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="71e03-113">Element</span></span>|<span data-ttu-id="71e03-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="71e03-114">Description</span></span>|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|<span data-ttu-id="71e03-115">Hizmet düzeyi kimlik ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="71e03-115">Specifies service-level identity settings.</span></span>|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="71e03-116">Bir güvenlik belirteci işleyicileri koleksiyonu için yapılandırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="71e03-116">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="71e03-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="71e03-117">Remarks</span></span>  

 <span data-ttu-id="71e03-118">Öğesi `<caches>` , öğesinin altındaki hizmet düzeyinde `<identityConfiguration>` veya öğesinin altındaki güvenlik belirteci işleyicisi koleksiyonu düzeyinde belirtilebilir `<securityTokenHandlerConfiguration>` .</span><span class="sxs-lookup"><span data-stu-id="71e03-118">A `<caches>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="71e03-119">Belirteç işleyici koleksiyonundaki ayarlar, hizmette belirtilen ayarları geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="71e03-119">Settings on a token handler collection override those specified on the service.</span></span>  
  
 <span data-ttu-id="71e03-120">`<caches>`Öğesi sınıfı tarafından temsil edilir <xref:System.IdentityModel.Configuration.IdentityModelCachesElement> .</span><span class="sxs-lookup"><span data-stu-id="71e03-120">The `<caches>` element is represented by the <xref:System.IdentityModel.Configuration.IdentityModelCachesElement> class.</span></span> <span data-ttu-id="71e03-121">Yapılandırılan önbellekler sınıfı tarafından temsil edilir <xref:System.IdentityModel.Configuration.IdentityModelCaches> .</span><span class="sxs-lookup"><span data-stu-id="71e03-121">The configured caches are represented by the <xref:System.IdentityModel.Configuration.IdentityModelCaches> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="71e03-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="71e03-122">Example</span></span>  

 <span data-ttu-id="71e03-123">Aşağıdaki XML, oturum güvenlik belirteçlerini () tutmak için özel bir önbelleğin yapılandırmasını gösterir <xref:System.IdentityModel.Tokens.SessionSecurityToken> .</span><span class="sxs-lookup"><span data-stu-id="71e03-123">The following XML shows the configuration of a custom cache for holding session security tokens (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span></span> <span data-ttu-id="71e03-124">Yapılandırma `ClaimsAwareWebFarm` örnekten alınır.</span><span class="sxs-lookup"><span data-stu-id="71e03-124">The configuration is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```
