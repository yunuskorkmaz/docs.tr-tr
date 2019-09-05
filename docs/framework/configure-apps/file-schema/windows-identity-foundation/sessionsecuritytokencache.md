---
title: <sessionSecurityTokenCache>
ms.date: 03/30/2017
ms.assetid: d43e676c-0153-485c-ab31-0257a2db7507
author: BrucePerlerMS
ms.openlocfilehash: e949b16f76f20191b84bbbbb6e8b019d913316f0
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251838"
---
# <a name="sessionsecuritytokencache"></a><span data-ttu-id="df5ce-101">\<sessionSecurityTokenCache ></span><span class="sxs-lookup"><span data-stu-id="df5ce-101">\<sessionSecurityTokenCache></span></span>
<span data-ttu-id="df5ce-102">Bir hizmet veya güvenlik belirteci işleyici koleksiyonuyla oturum belirteçleri için bir önbellek kaydeder.</span><span class="sxs-lookup"><span data-stu-id="df5ce-102">Registers a cache for session tokens with a service or a security token handler collection.</span></span>  
  
<span data-ttu-id="df5ce-103">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="df5ce-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="df5ce-104">&nbsp;&nbsp;[ **\<System. IdentityModel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="df5ce-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="df5ce-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<IdentityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="df5ce-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="df5ce-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<önbellekler >** ](caches.md)</span><span class="sxs-lookup"><span data-stu-id="df5ce-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<caches>**](caches.md)</span></span>\
<span data-ttu-id="df5ce-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<sessionSecurityTokenCache >**</span><span class="sxs-lookup"><span data-stu-id="df5ce-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sessionSecurityTokenCache>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df5ce-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="df5ce-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="df5ce-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="df5ce-109">Attributes and Elements</span></span>  
 <span data-ttu-id="df5ce-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="df5ce-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="df5ce-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="df5ce-111">Attributes</span></span>  
  
|<span data-ttu-id="df5ce-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="df5ce-112">Attribute</span></span>|<span data-ttu-id="df5ce-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="df5ce-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="df5ce-114">türü</span><span class="sxs-lookup"><span data-stu-id="df5ce-114">type</span></span>|<span data-ttu-id="df5ce-115"><xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> Sınıfından türeten bir tür.</span><span class="sxs-lookup"><span data-stu-id="df5ce-115">A type that derives from the <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="df5ce-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="df5ce-116">Child Elements</span></span>  
 <span data-ttu-id="df5ce-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="df5ce-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="df5ce-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="df5ce-118">Parent Elements</span></span>  
  
|<span data-ttu-id="df5ce-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="df5ce-119">Element</span></span>|<span data-ttu-id="df5ce-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="df5ce-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="df5ce-121">\<önbellekler ></span><span class="sxs-lookup"><span data-stu-id="df5ce-121">\<caches></span></span>](caches.md)|<span data-ttu-id="df5ce-122">Bir hizmet veya güvenlik belirteci işleyici koleksiyonu tarafından kullanılan önbellekleri kaydeder.</span><span class="sxs-lookup"><span data-stu-id="df5ce-122">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="df5ce-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="df5ce-123">Example</span></span>  
 <span data-ttu-id="df5ce-124">Aşağıdaki XML, oturum güvenlik belirteçlerini (<xref:System.IdentityModel.Tokens.SessionSecurityToken>) tutmak için özel bir önbelleğin yapılandırmasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="df5ce-124">The following XML shows the configuration of a custom cache for holding session security tokens (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span></span> <span data-ttu-id="df5ce-125">Yapılandırma `ClaimsAwareWebFarm` örnekten alınır.</span><span class="sxs-lookup"><span data-stu-id="df5ce-125">The configuration is taken from the `ClaimsAwareWebFarm` sample.</span></span> <span data-ttu-id="df5ce-126">Bu örnek hakkında daha fazla bilgi için bkz. [WIF kodu örnek dizini](../../../security/wif-code-sample-index.md).</span><span class="sxs-lookup"><span data-stu-id="df5ce-126">For more information about this sample, see [WIF Code Sample Index](../../../security/wif-code-sample-index.md).</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="df5ce-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="df5ce-127">See also</span></span>

- <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>
