---
title: '&lt;sessionSecurityTokenCache&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d43e676c-0153-485c-ab31-0257a2db7507
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: a1d1af398073e15ce7f73b3359366df9e5629ac6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="ltsessionsecuritytokencachegt"></a><span data-ttu-id="ee597-102">&lt;sessionSecurityTokenCache&gt;</span><span class="sxs-lookup"><span data-stu-id="ee597-102">&lt;sessionSecurityTokenCache&gt;</span></span>
<span data-ttu-id="ee597-103">Bir önbellek oturum belirteçleri için bir hizmet veya bir güvenlik belirteci işleyicisi koleksiyonu ile kaydeder.</span><span class="sxs-lookup"><span data-stu-id="ee597-103">Registers a cache for session tokens with a service or a security token handler collection.</span></span>  
  
 <span data-ttu-id="ee597-104">\<System.IdentityModel ></span><span class="sxs-lookup"><span data-stu-id="ee597-104">\<system.identityModel></span></span>  
<span data-ttu-id="ee597-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="ee597-105">\<identityConfiguration></span></span>  
<span data-ttu-id="ee597-106">\<önbelleğe alan ></span><span class="sxs-lookup"><span data-stu-id="ee597-106">\<caches></span></span>  
<span data-ttu-id="ee597-107">\<sessionSecurityTokenCache ></span><span class="sxs-lookup"><span data-stu-id="ee597-107">\<sessionSecurityTokenCache></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee597-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ee597-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ee597-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ee597-109">Attributes and Elements</span></span>  
 <span data-ttu-id="ee597-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ee597-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ee597-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ee597-111">Attributes</span></span>  
  
|<span data-ttu-id="ee597-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ee597-112">Attribute</span></span>|<span data-ttu-id="ee597-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ee597-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ee597-114">türü</span><span class="sxs-lookup"><span data-stu-id="ee597-114">type</span></span>|<span data-ttu-id="ee597-115">Türetilen bir tür <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="ee597-115">A type that derives from the <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ee597-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ee597-116">Child Elements</span></span>  
 <span data-ttu-id="ee597-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="ee597-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ee597-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ee597-118">Parent Elements</span></span>  
  
|<span data-ttu-id="ee597-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="ee597-119">Element</span></span>|<span data-ttu-id="ee597-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ee597-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ee597-121">\<önbelleğe alan ></span><span class="sxs-lookup"><span data-stu-id="ee597-121">\<caches></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|<span data-ttu-id="ee597-122">Bir hizmeti veya bir güvenlik belirteci işleyicisi koleksiyon tarafından kullanılan önbellekleri kaydeder.</span><span class="sxs-lookup"><span data-stu-id="ee597-122">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ee597-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="ee597-123">Example</span></span>  
 <span data-ttu-id="ee597-124">Aşağıdaki XML güvenlik belirteçleri oturum tutmak için özel bir önbellek yapılandırma gösterir (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span><span class="sxs-lookup"><span data-stu-id="ee597-124">The following XML shows the configuration of a custom cache for holding session security tokens (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span></span> <span data-ttu-id="ee597-125">Yapılandırma alınırlar `ClaimsAwareWebFarm` örnek.</span><span class="sxs-lookup"><span data-stu-id="ee597-125">The configuration is taken from the `ClaimsAwareWebFarm` sample.</span></span> <span data-ttu-id="ee597-126">Bu örnek hakkında daha fazla bilgi için bkz: [WIF kod örnek dizin](../../../../../docs/framework/security/wif-code-sample-index.md).</span><span class="sxs-lookup"><span data-stu-id="ee597-126">For more information about this sample, see [WIF Code Sample Index](../../../../../docs/framework/security/wif-code-sample-index.md).</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ee597-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ee597-127">See Also</span></span>  
 <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>
