---
title: <sessionSecurityTokenCache>
ms.date: 03/30/2017
ms.assetid: d43e676c-0153-485c-ab31-0257a2db7507
author: BrucePerlerMS
ms.openlocfilehash: a0db10ceb75a470dbf799d717b2059355dd104bb
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646075"
---
# <a name="sessionsecuritytokencache"></a><span data-ttu-id="1000e-101">\<oturumSecurityTokenCache></span><span class="sxs-lookup"><span data-stu-id="1000e-101">\<sessionSecurityTokenCache></span></span>
<span data-ttu-id="1000e-102">Bir hizmet veya güvenlik belirteç işleyicisi koleksiyonu ile oturum belirteçleri için bir önbellek kaydeder.</span><span class="sxs-lookup"><span data-stu-id="1000e-102">Registers a cache for session tokens with a service or a security token handler collection.</span></span>  
  
<span data-ttu-id="1000e-103">[**\<yapılandırma>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="1000e-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="1000e-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="1000e-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="1000e-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="1000e-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="1000e-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<önbellekleri>**](caches.md)</span><span class="sxs-lookup"><span data-stu-id="1000e-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<caches>**](caches.md)</span></span>\
<span data-ttu-id="1000e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<oturumSecurityTokenCache>**</span><span class="sxs-lookup"><span data-stu-id="1000e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sessionSecurityTokenCache>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1000e-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1000e-108">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <caches>  
      <sessionSecurityTokenCache type=xs:string>  
      </sessionSecurityTokenCache>  
    </caches>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1000e-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="1000e-109">Attributes and Elements</span></span>  
 <span data-ttu-id="1000e-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1000e-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1000e-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="1000e-111">Attributes</span></span>  
  
|<span data-ttu-id="1000e-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="1000e-112">Attribute</span></span>|<span data-ttu-id="1000e-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1000e-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1000e-114">type</span><span class="sxs-lookup"><span data-stu-id="1000e-114">type</span></span>|<span data-ttu-id="1000e-115"><xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> Sınıftan türemiş bir tür.</span><span class="sxs-lookup"><span data-stu-id="1000e-115">A type that derives from the <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1000e-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="1000e-116">Child Elements</span></span>  
 <span data-ttu-id="1000e-117">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="1000e-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1000e-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="1000e-118">Parent Elements</span></span>  
  
|<span data-ttu-id="1000e-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="1000e-119">Element</span></span>|<span data-ttu-id="1000e-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1000e-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1000e-121">\<önbellekleri></span><span class="sxs-lookup"><span data-stu-id="1000e-121">\<caches></span></span>](caches.md)|<span data-ttu-id="1000e-122">Bir hizmet veya güvenlik belirteci işleyicisi koleksiyonu tarafından kullanılan önbellekleri kaydeder.</span><span class="sxs-lookup"><span data-stu-id="1000e-122">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="1000e-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="1000e-123">Example</span></span>  
 <span data-ttu-id="1000e-124">Aşağıdaki XML, oturum güvenlik belirteçlerini tutmak için özel<xref:System.IdentityModel.Tokens.SessionSecurityToken>bir önbelleğin yapılandırmasını gösterir ( ).</span><span class="sxs-lookup"><span data-stu-id="1000e-124">The following XML shows the configuration of a custom cache for holding session security tokens (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span></span> <span data-ttu-id="1000e-125">Yapılandırma `ClaimsAwareWebFarm` örnekten alınır.</span><span class="sxs-lookup"><span data-stu-id="1000e-125">The configuration is taken from the `ClaimsAwareWebFarm` sample.</span></span> <span data-ttu-id="1000e-126">Bu örnek hakkında daha fazla bilgi için [WIF Kodu Örnek Endeksi'ne](https://docs.microsoft.com/previous-versions/dotnet/framework/security/wif-code-sample-index)bakın.</span><span class="sxs-lookup"><span data-stu-id="1000e-126">For more information about this sample, see [WIF Code Sample Index](https://docs.microsoft.com/previous-versions/dotnet/framework/security/wif-code-sample-index).</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1000e-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1000e-127">See also</span></span>

- <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>
