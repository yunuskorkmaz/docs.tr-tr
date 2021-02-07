---
description: 'Hakkında daha fazla bilgi edinin: <sessionSecurityTokenCache>'
title: <sessionSecurityTokenCache>
ms.date: 03/30/2017
ms.assetid: d43e676c-0153-485c-ab31-0257a2db7507
author: BrucePerlerMS
ms.openlocfilehash: 6fc0bb518f546ffd80c68df95a9c0fab145423b8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99698290"
---
# \<sessionSecurityTokenCache>

<span data-ttu-id="fba4e-102">Bir hizmet veya güvenlik belirteci işleyici koleksiyonuyla oturum belirteçleri için bir önbellek kaydeder.</span><span class="sxs-lookup"><span data-stu-id="fba4e-102">Registers a cache for session tokens with a service or a security token handler collection.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<caches>**](caches.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sessionSecurityTokenCache>**  
  
## <a name="syntax"></a><span data-ttu-id="fba4e-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="fba4e-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fba4e-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="fba4e-104">Attributes and Elements</span></span>  

 <span data-ttu-id="fba4e-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fba4e-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fba4e-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="fba4e-106">Attributes</span></span>  
  
|<span data-ttu-id="fba4e-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="fba4e-107">Attribute</span></span>|<span data-ttu-id="fba4e-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fba4e-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fba4e-109">tür</span><span class="sxs-lookup"><span data-stu-id="fba4e-109">type</span></span>|<span data-ttu-id="fba4e-110">Sınıfından türeten bir tür <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> .</span><span class="sxs-lookup"><span data-stu-id="fba4e-110">A type that derives from the <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fba4e-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="fba4e-111">Child Elements</span></span>  

 <span data-ttu-id="fba4e-112">Yok</span><span class="sxs-lookup"><span data-stu-id="fba4e-112">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fba4e-113">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="fba4e-113">Parent Elements</span></span>  
  
|<span data-ttu-id="fba4e-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="fba4e-114">Element</span></span>|<span data-ttu-id="fba4e-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fba4e-115">Description</span></span>|  
|-------------|-----------------|  
|[\<caches>](caches.md)|<span data-ttu-id="fba4e-116">Bir hizmet veya güvenlik belirteci işleyici koleksiyonu tarafından kullanılan önbellekleri kaydeder.</span><span class="sxs-lookup"><span data-stu-id="fba4e-116">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="fba4e-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="fba4e-117">Example</span></span>  

 <span data-ttu-id="fba4e-118">Aşağıdaki XML, oturum güvenlik belirteçlerini () tutmak için özel bir önbelleğin yapılandırmasını gösterir <xref:System.IdentityModel.Tokens.SessionSecurityToken> .</span><span class="sxs-lookup"><span data-stu-id="fba4e-118">The following XML shows the configuration of a custom cache for holding session security tokens (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span></span> <span data-ttu-id="fba4e-119">Yapılandırma `ClaimsAwareWebFarm` örnekten alınır.</span><span class="sxs-lookup"><span data-stu-id="fba4e-119">The configuration is taken from the `ClaimsAwareWebFarm` sample.</span></span> <span data-ttu-id="fba4e-120">Bu örnek hakkında daha fazla bilgi için bkz. [WIF kodu örnek dizini](/previous-versions/dotnet/framework/security/wif-code-sample-index).</span><span class="sxs-lookup"><span data-stu-id="fba4e-120">For more information about this sample, see [WIF Code Sample Index](/previous-versions/dotnet/framework/security/wif-code-sample-index).</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="fba4e-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fba4e-121">See also</span></span>

- <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>
