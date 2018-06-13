---
title: '&lt;sessionSecurityTokenCache&gt;'
ms.date: 03/30/2017
ms.assetid: d43e676c-0153-485c-ab31-0257a2db7507
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 0b0d3c01a81f110f79f64d75aa2ab2ff2873fedd
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32755051"
---
# <a name="ltsessionsecuritytokencachegt"></a><span data-ttu-id="00c33-102">&lt;sessionSecurityTokenCache&gt;</span><span class="sxs-lookup"><span data-stu-id="00c33-102">&lt;sessionSecurityTokenCache&gt;</span></span>
<span data-ttu-id="00c33-103">Bir önbellek oturum belirteçleri için bir hizmet veya bir güvenlik belirteci işleyicisi koleksiyonu ile kaydeder.</span><span class="sxs-lookup"><span data-stu-id="00c33-103">Registers a cache for session tokens with a service or a security token handler collection.</span></span>  
  
 <span data-ttu-id="00c33-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="00c33-104">\<system.identityModel></span></span>  
<span data-ttu-id="00c33-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="00c33-105">\<identityConfiguration></span></span>  
<span data-ttu-id="00c33-106">\<önbelleğe alan ></span><span class="sxs-lookup"><span data-stu-id="00c33-106">\<caches></span></span>  
<span data-ttu-id="00c33-107">\<sessionSecurityTokenCache ></span><span class="sxs-lookup"><span data-stu-id="00c33-107">\<sessionSecurityTokenCache></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00c33-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="00c33-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="00c33-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="00c33-109">Attributes and Elements</span></span>  
 <span data-ttu-id="00c33-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="00c33-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="00c33-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="00c33-111">Attributes</span></span>  
  
|<span data-ttu-id="00c33-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="00c33-112">Attribute</span></span>|<span data-ttu-id="00c33-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="00c33-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="00c33-114">türü</span><span class="sxs-lookup"><span data-stu-id="00c33-114">type</span></span>|<span data-ttu-id="00c33-115">Türetilen bir tür <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="00c33-115">A type that derives from the <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="00c33-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="00c33-116">Child Elements</span></span>  
 <span data-ttu-id="00c33-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="00c33-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="00c33-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="00c33-118">Parent Elements</span></span>  
  
|<span data-ttu-id="00c33-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="00c33-119">Element</span></span>|<span data-ttu-id="00c33-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="00c33-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="00c33-121">\<önbelleğe alan ></span><span class="sxs-lookup"><span data-stu-id="00c33-121">\<caches></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|<span data-ttu-id="00c33-122">Bir hizmeti veya bir güvenlik belirteci işleyicisi koleksiyon tarafından kullanılan önbellekleri kaydeder.</span><span class="sxs-lookup"><span data-stu-id="00c33-122">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="00c33-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="00c33-123">Example</span></span>  
 <span data-ttu-id="00c33-124">Aşağıdaki XML güvenlik belirteçleri oturum tutmak için özel bir önbellek yapılandırma gösterir (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span><span class="sxs-lookup"><span data-stu-id="00c33-124">The following XML shows the configuration of a custom cache for holding session security tokens (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span></span> <span data-ttu-id="00c33-125">Yapılandırma alınırlar `ClaimsAwareWebFarm` örnek.</span><span class="sxs-lookup"><span data-stu-id="00c33-125">The configuration is taken from the `ClaimsAwareWebFarm` sample.</span></span> <span data-ttu-id="00c33-126">Bu örnek hakkında daha fazla bilgi için bkz: [WIF kod örnek dizin](../../../../../docs/framework/security/wif-code-sample-index.md).</span><span class="sxs-lookup"><span data-stu-id="00c33-126">For more information about this sample, see [WIF Code Sample Index](../../../../../docs/framework/security/wif-code-sample-index.md).</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="00c33-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="00c33-127">See Also</span></span>  
 <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>
