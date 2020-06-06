---
title: <sessionSecurityTokenCache>
ms.date: 03/30/2017
ms.assetid: d43e676c-0153-485c-ab31-0257a2db7507
author: BrucePerlerMS
ms.openlocfilehash: a0db10ceb75a470dbf799d717b2059355dd104bb
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "81646075"
---
# \<sessionSecurityTokenCache>
<span data-ttu-id="fff54-101">Bir hizmet veya güvenlik belirteci işleyici koleksiyonuyla oturum belirteçleri için bir önbellek kaydeder.</span><span class="sxs-lookup"><span data-stu-id="fff54-101">Registers a cache for session tokens with a service or a security token handler collection.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<caches>**](caches.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sessionSecurityTokenCache>**  
  
## <a name="syntax"></a><span data-ttu-id="fff54-102">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fff54-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fff54-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="fff54-103">Attributes and Elements</span></span>  
 <span data-ttu-id="fff54-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fff54-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fff54-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="fff54-105">Attributes</span></span>  
  
|<span data-ttu-id="fff54-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="fff54-106">Attribute</span></span>|<span data-ttu-id="fff54-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fff54-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fff54-108">tür</span><span class="sxs-lookup"><span data-stu-id="fff54-108">type</span></span>|<span data-ttu-id="fff54-109">Sınıfından türeten bir tür <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> .</span><span class="sxs-lookup"><span data-stu-id="fff54-109">A type that derives from the <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fff54-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="fff54-110">Child Elements</span></span>  
 <span data-ttu-id="fff54-111">Yok</span><span class="sxs-lookup"><span data-stu-id="fff54-111">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fff54-112">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="fff54-112">Parent Elements</span></span>  
  
|<span data-ttu-id="fff54-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="fff54-113">Element</span></span>|<span data-ttu-id="fff54-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fff54-114">Description</span></span>|  
|-------------|-----------------|  
|[\<caches>](caches.md)|<span data-ttu-id="fff54-115">Bir hizmet veya güvenlik belirteci işleyici koleksiyonu tarafından kullanılan önbellekleri kaydeder.</span><span class="sxs-lookup"><span data-stu-id="fff54-115">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="fff54-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="fff54-116">Example</span></span>  
 <span data-ttu-id="fff54-117">Aşağıdaki XML, oturum güvenlik belirteçlerini () tutmak için özel bir önbelleğin yapılandırmasını gösterir <xref:System.IdentityModel.Tokens.SessionSecurityToken> .</span><span class="sxs-lookup"><span data-stu-id="fff54-117">The following XML shows the configuration of a custom cache for holding session security tokens (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span></span> <span data-ttu-id="fff54-118">Yapılandırma `ClaimsAwareWebFarm` örnekten alınır.</span><span class="sxs-lookup"><span data-stu-id="fff54-118">The configuration is taken from the `ClaimsAwareWebFarm` sample.</span></span> <span data-ttu-id="fff54-119">Bu örnek hakkında daha fazla bilgi için bkz. [WIF kodu örnek dizini](https://docs.microsoft.com/previous-versions/dotnet/framework/security/wif-code-sample-index).</span><span class="sxs-lookup"><span data-stu-id="fff54-119">For more information about this sample, see [WIF Code Sample Index](https://docs.microsoft.com/previous-versions/dotnet/framework/security/wif-code-sample-index).</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="fff54-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fff54-120">See also</span></span>

- <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>
