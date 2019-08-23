---
title: <sessionSecurityTokenCache>
ms.date: 03/30/2017
ms.assetid: d43e676c-0153-485c-ab31-0257a2db7507
author: BrucePerlerMS
ms.openlocfilehash: 9be3bf980c3756678d26d8652271113d4daaba43
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943706"
---
# <a name="sessionsecuritytokencache"></a><span data-ttu-id="e6017-101">\<sessionSecurityTokenCache ></span><span class="sxs-lookup"><span data-stu-id="e6017-101">\<sessionSecurityTokenCache></span></span>
<span data-ttu-id="e6017-102">Bir hizmet veya güvenlik belirteci işleyici koleksiyonuyla oturum belirteçleri için bir önbellek kaydeder.</span><span class="sxs-lookup"><span data-stu-id="e6017-102">Registers a cache for session tokens with a service or a security token handler collection.</span></span>  
  
 <span data-ttu-id="e6017-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="e6017-103">\<system.identityModel></span></span>  
<span data-ttu-id="e6017-104">\<IdentityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="e6017-104">\<identityConfiguration></span></span>  
<span data-ttu-id="e6017-105">\<önbellekler ></span><span class="sxs-lookup"><span data-stu-id="e6017-105">\<caches></span></span>  
<span data-ttu-id="e6017-106">\<sessionSecurityTokenCache ></span><span class="sxs-lookup"><span data-stu-id="e6017-106">\<sessionSecurityTokenCache></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6017-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e6017-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e6017-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e6017-108">Attributes and Elements</span></span>  
 <span data-ttu-id="e6017-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e6017-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e6017-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e6017-110">Attributes</span></span>  
  
|<span data-ttu-id="e6017-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e6017-111">Attribute</span></span>|<span data-ttu-id="e6017-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e6017-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e6017-113">türü</span><span class="sxs-lookup"><span data-stu-id="e6017-113">type</span></span>|<span data-ttu-id="e6017-114"><xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> Sınıfından türeten bir tür.</span><span class="sxs-lookup"><span data-stu-id="e6017-114">A type that derives from the <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e6017-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e6017-115">Child Elements</span></span>  
 <span data-ttu-id="e6017-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="e6017-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e6017-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e6017-117">Parent Elements</span></span>  
  
|<span data-ttu-id="e6017-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="e6017-118">Element</span></span>|<span data-ttu-id="e6017-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e6017-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e6017-120">\<önbellekler ></span><span class="sxs-lookup"><span data-stu-id="e6017-120">\<caches></span></span>](caches.md)|<span data-ttu-id="e6017-121">Bir hizmet veya güvenlik belirteci işleyici koleksiyonu tarafından kullanılan önbellekleri kaydeder.</span><span class="sxs-lookup"><span data-stu-id="e6017-121">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e6017-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="e6017-122">Example</span></span>  
 <span data-ttu-id="e6017-123">Aşağıdaki XML, oturum güvenlik belirteçlerini (<xref:System.IdentityModel.Tokens.SessionSecurityToken>) tutmak için özel bir önbelleğin yapılandırmasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e6017-123">The following XML shows the configuration of a custom cache for holding session security tokens (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span></span> <span data-ttu-id="e6017-124">Yapılandırma `ClaimsAwareWebFarm` örnekten alınır.</span><span class="sxs-lookup"><span data-stu-id="e6017-124">The configuration is taken from the `ClaimsAwareWebFarm` sample.</span></span> <span data-ttu-id="e6017-125">Bu örnek hakkında daha fazla bilgi için bkz. [WIF kodu örnek dizini](../../../security/wif-code-sample-index.md).</span><span class="sxs-lookup"><span data-stu-id="e6017-125">For more information about this sample, see [WIF Code Sample Index](../../../security/wif-code-sample-index.md).</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e6017-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e6017-126">See also</span></span>

- <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>
