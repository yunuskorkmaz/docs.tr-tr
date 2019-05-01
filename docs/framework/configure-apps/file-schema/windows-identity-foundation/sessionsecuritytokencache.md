---
title: <sessionSecurityTokenCache>
ms.date: 03/30/2017
ms.assetid: d43e676c-0153-485c-ab31-0257a2db7507
author: BrucePerlerMS
ms.openlocfilehash: 5c68fe618f965f364a3716c3bc65de5e165b12ec
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61793802"
---
# <a name="sessionsecuritytokencache"></a><span data-ttu-id="05176-101">\<sessionSecurityTokenCache></span><span class="sxs-lookup"><span data-stu-id="05176-101">\<sessionSecurityTokenCache></span></span>
<span data-ttu-id="05176-102">Bir hizmet ya da bir güvenlik belirteci işleyicisi koleksiyon oturumu belirteçleri için bir önbelleği kaydeder.</span><span class="sxs-lookup"><span data-stu-id="05176-102">Registers a cache for session tokens with a service or a security token handler collection.</span></span>  
  
 <span data-ttu-id="05176-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="05176-103">\<system.identityModel></span></span>  
<span data-ttu-id="05176-104">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="05176-104">\<identityConfiguration></span></span>  
<span data-ttu-id="05176-105">\<önbelleğe alan ></span><span class="sxs-lookup"><span data-stu-id="05176-105">\<caches></span></span>  
<span data-ttu-id="05176-106">\<sessionSecurityTokenCache></span><span class="sxs-lookup"><span data-stu-id="05176-106">\<sessionSecurityTokenCache></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05176-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="05176-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="05176-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="05176-108">Attributes and Elements</span></span>  
 <span data-ttu-id="05176-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="05176-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="05176-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="05176-110">Attributes</span></span>  
  
|<span data-ttu-id="05176-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="05176-111">Attribute</span></span>|<span data-ttu-id="05176-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="05176-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="05176-113">türü</span><span class="sxs-lookup"><span data-stu-id="05176-113">type</span></span>|<span data-ttu-id="05176-114">Türetilen bir tür <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="05176-114">A type that derives from the <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="05176-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="05176-115">Child Elements</span></span>  
 <span data-ttu-id="05176-116">None</span><span class="sxs-lookup"><span data-stu-id="05176-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="05176-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="05176-117">Parent Elements</span></span>  
  
|<span data-ttu-id="05176-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="05176-118">Element</span></span>|<span data-ttu-id="05176-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="05176-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="05176-120">\<önbelleğe alan ></span><span class="sxs-lookup"><span data-stu-id="05176-120">\<caches></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|<span data-ttu-id="05176-121">Bir hizmet veya bir güvenlik belirteci işleyicisi koleksiyon tarafından kullanılan önbellekleri kaydeder.</span><span class="sxs-lookup"><span data-stu-id="05176-121">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="05176-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="05176-122">Example</span></span>  
 <span data-ttu-id="05176-123">Aşağıdaki XML oturumu güvenlik belirteçleri tutmak için özel bir önbellek yapılandırmasını gösterir (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span><span class="sxs-lookup"><span data-stu-id="05176-123">The following XML shows the configuration of a custom cache for holding session security tokens (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span></span> <span data-ttu-id="05176-124">Yapılandırma alınır `ClaimsAwareWebFarm` örnek.</span><span class="sxs-lookup"><span data-stu-id="05176-124">The configuration is taken from the `ClaimsAwareWebFarm` sample.</span></span> <span data-ttu-id="05176-125">Bu örnek hakkında daha fazla bilgi için bkz: [WIF kod örneği dizini](../../../../../docs/framework/security/wif-code-sample-index.md).</span><span class="sxs-lookup"><span data-stu-id="05176-125">For more information about this sample, see [WIF Code Sample Index](../../../../../docs/framework/security/wif-code-sample-index.md).</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="05176-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="05176-126">See also</span></span>

- <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>
