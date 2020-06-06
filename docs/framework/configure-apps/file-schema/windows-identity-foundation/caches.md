---
title: <caches>
ms.date: 03/30/2017
ms.assetid: 4651091b-3a20-40d8-b293-4408c0710143
author: BrucePerlerMS
ms.openlocfilehash: 80f435b52fd7657c5cd44538028d6080beffe0b5
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70252157"
---
# \<caches>
<span data-ttu-id="f69d2-101">Oturum belirteçleri ve belirteci yeniden yürütme algılaması için kullanılan önbellekleri kaydeder.</span><span class="sxs-lookup"><span data-stu-id="f69d2-101">Registers the caches used for session tokens and token replay detection.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<caches>**  
  
## <a name="syntax"></a><span data-ttu-id="f69d2-102">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f69d2-102">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <caches>  
    </caches>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f69d2-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f69d2-103">Attributes and Elements</span></span>  
 <span data-ttu-id="f69d2-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f69d2-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f69d2-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f69d2-105">Attributes</span></span>  
 <span data-ttu-id="f69d2-106">Yok</span><span class="sxs-lookup"><span data-stu-id="f69d2-106">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f69d2-107">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f69d2-107">Child Elements</span></span>  
  
|<span data-ttu-id="f69d2-108">Öğe</span><span class="sxs-lookup"><span data-stu-id="f69d2-108">Element</span></span>|<span data-ttu-id="f69d2-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f69d2-109">Description</span></span>|  
|-------------|-----------------|  
|[\<sessionSecurityTokenCache>](sessionsecuritytokencache.md)|<span data-ttu-id="f69d2-110">Bir hizmet veya güvenlik belirteci işleyici koleksiyonuyla oturum belirteçleri için bir önbellek kaydeder.</span><span class="sxs-lookup"><span data-stu-id="f69d2-110">Registers a cache for session tokens with a service or a security token handler collection.</span></span>|  
|[\<tokenReplayCache>](tokenreplaycache.md)|<span data-ttu-id="f69d2-111">Belirteç yeniden yürütme önbelleğini bir hizmet veya güvenlik belirteci işleyici koleksiyonuyla kaydeder.</span><span class="sxs-lookup"><span data-stu-id="f69d2-111">Registers a token replay cache with a service or a security token handler collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f69d2-112">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f69d2-112">Parent Elements</span></span>  
  
|<span data-ttu-id="f69d2-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="f69d2-113">Element</span></span>|<span data-ttu-id="f69d2-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f69d2-114">Description</span></span>|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|<span data-ttu-id="f69d2-115">Hizmet düzeyi kimlik ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="f69d2-115">Specifies service-level identity settings.</span></span>|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="f69d2-116">Bir güvenlik belirteci işleyicileri koleksiyonu için yapılandırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="f69d2-116">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f69d2-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f69d2-117">Remarks</span></span>  
 <span data-ttu-id="f69d2-118">Öğesi `<caches>` , öğesinin altındaki hizmet düzeyinde `<identityConfiguration>` veya öğesinin altındaki güvenlik belirteci işleyicisi koleksiyonu düzeyinde belirtilebilir `<securityTokenHandlerConfiguration>` .</span><span class="sxs-lookup"><span data-stu-id="f69d2-118">A `<caches>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="f69d2-119">Belirteç işleyici koleksiyonundaki ayarlar, hizmette belirtilen ayarları geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="f69d2-119">Settings on a token handler collection override those specified on the service.</span></span>  
  
 <span data-ttu-id="f69d2-120">`<caches>`Öğesi sınıfı tarafından temsil edilir <xref:System.IdentityModel.Configuration.IdentityModelCachesElement> .</span><span class="sxs-lookup"><span data-stu-id="f69d2-120">The `<caches>` element is represented by the <xref:System.IdentityModel.Configuration.IdentityModelCachesElement> class.</span></span> <span data-ttu-id="f69d2-121">Yapılandırılan önbellekler sınıfı tarafından temsil edilir <xref:System.IdentityModel.Configuration.IdentityModelCaches> .</span><span class="sxs-lookup"><span data-stu-id="f69d2-121">The configured caches are represented by the <xref:System.IdentityModel.Configuration.IdentityModelCaches> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f69d2-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="f69d2-122">Example</span></span>  
 <span data-ttu-id="f69d2-123">Aşağıdaki XML, oturum güvenlik belirteçlerini () tutmak için özel bir önbelleğin yapılandırmasını gösterir <xref:System.IdentityModel.Tokens.SessionSecurityToken> .</span><span class="sxs-lookup"><span data-stu-id="f69d2-123">The following XML shows the configuration of a custom cache for holding session security tokens (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span></span> <span data-ttu-id="f69d2-124">Yapılandırma `ClaimsAwareWebFarm` örnekten alınır.</span><span class="sxs-lookup"><span data-stu-id="f69d2-124">The configuration is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```
