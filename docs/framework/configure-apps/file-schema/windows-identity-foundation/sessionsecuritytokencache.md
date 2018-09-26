---
title: '&lt;sessionSecurityTokenCache&gt;'
ms.date: 03/30/2017
ms.assetid: d43e676c-0153-485c-ab31-0257a2db7507
author: BrucePerlerMS
ms.openlocfilehash: b812673ac1c015adde357d3c0707d85643aad3e9
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47084338"
---
# <a name="ltsessionsecuritytokencachegt"></a><span data-ttu-id="0e975-102">&lt;sessionSecurityTokenCache&gt;</span><span class="sxs-lookup"><span data-stu-id="0e975-102">&lt;sessionSecurityTokenCache&gt;</span></span>
<span data-ttu-id="0e975-103">Bir hizmet ya da bir güvenlik belirteci işleyicisi koleksiyon oturumu belirteçleri için bir önbelleği kaydeder.</span><span class="sxs-lookup"><span data-stu-id="0e975-103">Registers a cache for session tokens with a service or a security token handler collection.</span></span>  
  
 <span data-ttu-id="0e975-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="0e975-104">\<system.identityModel></span></span>  
<span data-ttu-id="0e975-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="0e975-105">\<identityConfiguration></span></span>  
<span data-ttu-id="0e975-106">\<önbelleğe alan ></span><span class="sxs-lookup"><span data-stu-id="0e975-106">\<caches></span></span>  
<span data-ttu-id="0e975-107">\<sessionSecurityTokenCache ></span><span class="sxs-lookup"><span data-stu-id="0e975-107">\<sessionSecurityTokenCache></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e975-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0e975-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0e975-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="0e975-109">Attributes and Elements</span></span>  
 <span data-ttu-id="0e975-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0e975-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0e975-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0e975-111">Attributes</span></span>  
  
|<span data-ttu-id="0e975-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="0e975-112">Attribute</span></span>|<span data-ttu-id="0e975-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0e975-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0e975-114">türü</span><span class="sxs-lookup"><span data-stu-id="0e975-114">type</span></span>|<span data-ttu-id="0e975-115">Türetilen bir tür <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="0e975-115">A type that derives from the <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0e975-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="0e975-116">Child Elements</span></span>  
 <span data-ttu-id="0e975-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="0e975-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0e975-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="0e975-118">Parent Elements</span></span>  
  
|<span data-ttu-id="0e975-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="0e975-119">Element</span></span>|<span data-ttu-id="0e975-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0e975-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0e975-121">\<önbelleğe alan ></span><span class="sxs-lookup"><span data-stu-id="0e975-121">\<caches></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|<span data-ttu-id="0e975-122">Bir hizmet veya bir güvenlik belirteci işleyicisi koleksiyon tarafından kullanılan önbellekleri kaydeder.</span><span class="sxs-lookup"><span data-stu-id="0e975-122">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="0e975-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="0e975-123">Example</span></span>  
 <span data-ttu-id="0e975-124">Aşağıdaki XML oturumu güvenlik belirteçleri tutmak için özel bir önbellek yapılandırmasını gösterir (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span><span class="sxs-lookup"><span data-stu-id="0e975-124">The following XML shows the configuration of a custom cache for holding session security tokens (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span></span> <span data-ttu-id="0e975-125">Yapılandırma alınır `ClaimsAwareWebFarm` örnek.</span><span class="sxs-lookup"><span data-stu-id="0e975-125">The configuration is taken from the `ClaimsAwareWebFarm` sample.</span></span> <span data-ttu-id="0e975-126">Bu örnek hakkında daha fazla bilgi için bkz: [WIF kod örneği dizini](../../../../../docs/framework/security/wif-code-sample-index.md).</span><span class="sxs-lookup"><span data-stu-id="0e975-126">For more information about this sample, see [WIF Code Sample Index](../../../../../docs/framework/security/wif-code-sample-index.md).</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0e975-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0e975-127">See Also</span></span>  
 <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>
