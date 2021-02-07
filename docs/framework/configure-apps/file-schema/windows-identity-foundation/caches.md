---
description: 'Hakkında daha fazla bilgi edinin: <caches>'
title: <caches>
ms.date: 03/30/2017
ms.assetid: 4651091b-3a20-40d8-b293-4408c0710143
author: BrucePerlerMS
ms.openlocfilehash: ebc2fa66ab8b657f7cc3741668c9f27fc60510b4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99681844"
---
# \<caches>

<span data-ttu-id="afbe6-102">Oturum belirteçleri ve belirteci yeniden yürütme algılaması için kullanılan önbellekleri kaydeder.</span><span class="sxs-lookup"><span data-stu-id="afbe6-102">Registers the caches used for session tokens and token replay detection.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<caches>**  
  
## <a name="syntax"></a><span data-ttu-id="afbe6-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="afbe6-103">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <caches>  
    </caches>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="afbe6-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="afbe6-104">Attributes and Elements</span></span>  

 <span data-ttu-id="afbe6-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="afbe6-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="afbe6-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="afbe6-106">Attributes</span></span>  

 <span data-ttu-id="afbe6-107">Yok</span><span class="sxs-lookup"><span data-stu-id="afbe6-107">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="afbe6-108">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="afbe6-108">Child Elements</span></span>  
  
|<span data-ttu-id="afbe6-109">Öğe</span><span class="sxs-lookup"><span data-stu-id="afbe6-109">Element</span></span>|<span data-ttu-id="afbe6-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="afbe6-110">Description</span></span>|  
|-------------|-----------------|  
|[\<sessionSecurityTokenCache>](sessionsecuritytokencache.md)|<span data-ttu-id="afbe6-111">Bir hizmet veya güvenlik belirteci işleyici koleksiyonuyla oturum belirteçleri için bir önbellek kaydeder.</span><span class="sxs-lookup"><span data-stu-id="afbe6-111">Registers a cache for session tokens with a service or a security token handler collection.</span></span>|  
|[\<tokenReplayCache>](tokenreplaycache.md)|<span data-ttu-id="afbe6-112">Belirteç yeniden yürütme önbelleğini bir hizmet veya güvenlik belirteci işleyici koleksiyonuyla kaydeder.</span><span class="sxs-lookup"><span data-stu-id="afbe6-112">Registers a token replay cache with a service or a security token handler collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="afbe6-113">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="afbe6-113">Parent Elements</span></span>  
  
|<span data-ttu-id="afbe6-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="afbe6-114">Element</span></span>|<span data-ttu-id="afbe6-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="afbe6-115">Description</span></span>|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|<span data-ttu-id="afbe6-116">Hizmet düzeyi kimlik ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="afbe6-116">Specifies service-level identity settings.</span></span>|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="afbe6-117">Bir güvenlik belirteci işleyicileri koleksiyonu için yapılandırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="afbe6-117">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="afbe6-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="afbe6-118">Remarks</span></span>  

 <span data-ttu-id="afbe6-119">Öğesi `<caches>` , öğesinin altındaki hizmet düzeyinde `<identityConfiguration>` veya öğesinin altındaki güvenlik belirteci işleyicisi koleksiyonu düzeyinde belirtilebilir `<securityTokenHandlerConfiguration>` .</span><span class="sxs-lookup"><span data-stu-id="afbe6-119">A `<caches>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="afbe6-120">Belirteç işleyici koleksiyonundaki ayarlar, hizmette belirtilen ayarları geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="afbe6-120">Settings on a token handler collection override those specified on the service.</span></span>  
  
 <span data-ttu-id="afbe6-121">`<caches>`Öğesi sınıfı tarafından temsil edilir <xref:System.IdentityModel.Configuration.IdentityModelCachesElement> .</span><span class="sxs-lookup"><span data-stu-id="afbe6-121">The `<caches>` element is represented by the <xref:System.IdentityModel.Configuration.IdentityModelCachesElement> class.</span></span> <span data-ttu-id="afbe6-122">Yapılandırılan önbellekler sınıfı tarafından temsil edilir <xref:System.IdentityModel.Configuration.IdentityModelCaches> .</span><span class="sxs-lookup"><span data-stu-id="afbe6-122">The configured caches are represented by the <xref:System.IdentityModel.Configuration.IdentityModelCaches> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="afbe6-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="afbe6-123">Example</span></span>  

 <span data-ttu-id="afbe6-124">Aşağıdaki XML, oturum güvenlik belirteçlerini () tutmak için özel bir önbelleğin yapılandırmasını gösterir <xref:System.IdentityModel.Tokens.SessionSecurityToken> .</span><span class="sxs-lookup"><span data-stu-id="afbe6-124">The following XML shows the configuration of a custom cache for holding session security tokens (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span></span> <span data-ttu-id="afbe6-125">Yapılandırma `ClaimsAwareWebFarm` örnekten alınır.</span><span class="sxs-lookup"><span data-stu-id="afbe6-125">The configuration is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```
