---
title: '&lt;defaultFtpCachePolicy&gt; öğesi (ağ ayarları)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultFtpCachePolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching/defaultFtpCachePolicy
helpviewer_keywords:
- <defaultFtpCachePolicy> element
- defaultFtpCachePolicy element
ms.assetid: 0eb0c5cb-dd97-484d-8614-785e88877abb
ms.openlocfilehash: f237831befab627ec603a9000a7cef6184e0ae65
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54546115"
---
# <a name="ltdefaultftpcachepolicygt-element-network-settings"></a><span data-ttu-id="8525c-102">&lt;defaultFtpCachePolicy&gt; öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="8525c-102">&lt;defaultFtpCachePolicy&gt; Element (Network Settings)</span></span>
<span data-ttu-id="8525c-103">FTP önbelleğe alma etkindir ve önbelleğe alma ilkesi varsayılan tanımlar olup olmadığını açıklar.</span><span class="sxs-lookup"><span data-stu-id="8525c-103">Describes whether FTP caching is active and describes the default caching policy.</span></span>  
  
 <span data-ttu-id="8525c-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="8525c-104">\<configuration></span></span>  
<span data-ttu-id="8525c-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="8525c-105">\<system.net></span></span>  
<span data-ttu-id="8525c-106">\<requestCaching ></span><span class="sxs-lookup"><span data-stu-id="8525c-106">\<requestCaching></span></span>  
<span data-ttu-id="8525c-107">\<defaultFtpCachePolicy ></span><span class="sxs-lookup"><span data-stu-id="8525c-107">\<defaultFtpCachePolicy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8525c-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8525c-108">Syntax</span></span>  
  
```xml  
<defaultFtpCachePolicy  
  policyLevel="BypassCache|Default|CacheOnly|CacheIfAvailable|Revalidate|Reload|NoCacheNoStore|Revalidate"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8525c-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="8525c-109">Attributes and Elements</span></span>  
 <span data-ttu-id="8525c-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8525c-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8525c-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="8525c-111">Attributes</span></span>  
  
|<span data-ttu-id="8525c-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="8525c-112">Attribute</span></span>|<span data-ttu-id="8525c-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8525c-113">Description</span></span>|  
|---------------|-----------------|  
|`policyLevel`|<span data-ttu-id="8525c-114">Önbelleğe alma İlkesi FTP belirtir.</span><span class="sxs-lookup"><span data-stu-id="8525c-114">Specifies the FTP caching policy.</span></span> <span data-ttu-id="8525c-115">Varsayılan değer `Default` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="8525c-115">The default value is `Default`.</span></span>|  
  
## <a name="policylevel-attribute"></a><span data-ttu-id="8525c-116">policyLevel özniteliği</span><span class="sxs-lookup"><span data-stu-id="8525c-116">policyLevel Attribute</span></span>  
  
|<span data-ttu-id="8525c-117">Değer</span><span class="sxs-lookup"><span data-stu-id="8525c-117">Value</span></span>|<span data-ttu-id="8525c-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8525c-118">Description</span></span>|  
|-----------|-----------------|  
|`Default`|<span data-ttu-id="8525c-119">Önbelleğe alınmış kaynak sona erme, değiştirilmesi ve içerik uzunluğu öznitelikleri mevcut olduğundan yeni bir kaynaktır ve içerik uzunluğu doğru döndürür.</span><span class="sxs-lookup"><span data-stu-id="8525c-119">Returns the cached resource if the resource is fresh, the content length is accurate, and the expiration, modification, and content length attributes are present.</span></span>|  
|`BypassCache`|<span data-ttu-id="8525c-120">Kaynak sunucudan döndürür.</span><span class="sxs-lookup"><span data-stu-id="8525c-120">Returns the resource from the server.</span></span>|  
|`CacheOnly`|<span data-ttu-id="8525c-121">İçerik uzunluğu varsa ve giriş boyutu eşleşen önbelleğe alınmış kaynak döndürür.</span><span class="sxs-lookup"><span data-stu-id="8525c-121">Returns the cached resource if the content length is present and matches the entry size.</span></span>|  
|`CacheIfAvailable`|<span data-ttu-id="8525c-122">İçerik uzunluğu sağlanır ve giriş boyutu eşleşiyorsa, önbelleğe alınmış kaynak döndürür; Aksi takdirde, kaynak sunucudan indirilir ve çağırana döndürülür.</span><span class="sxs-lookup"><span data-stu-id="8525c-122">Returns the cached resource if the content length is provided and matches the entry size; otherwise, the resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="8525c-123">Önbelleğe alınmış kaynak zaman damgası önbelleğe alınmış kaynak sunucusunda kaynak zaman damgası ile aynı olduğunda döndürür; Aksi takdirde, kaynak sunucudan, önbellekte depolanır ve arayana döndürülür.</span><span class="sxs-lookup"><span data-stu-id="8525c-123">Returns the cached resource if the timestamp of the cached resource is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, stored in the cache, and returned to the caller.</span></span>|  
|`Reload`|<span data-ttu-id="8525c-124">Kaynak sunucudan indirir, önbellekte depolar ve kaynak çağırana döner.</span><span class="sxs-lookup"><span data-stu-id="8525c-124">Downloads the resource from the server, stores it in the cache, and returns the resource to the caller.</span></span>|  
|`NoCacheNoStore`|<span data-ttu-id="8525c-125">Önbelleğe alınan bir kaynağın varolup olmadığını silinir.</span><span class="sxs-lookup"><span data-stu-id="8525c-125">If a cached resource exists, it is deleted.</span></span> <span data-ttu-id="8525c-126">Kaynak sunucudan indirilir ve çağırana döndürülür.</span><span class="sxs-lookup"><span data-stu-id="8525c-126">The resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="8525c-127">Bir istek, zaman damgası zaman damgasını kaynak sunucudaki aynı olduğunda, kaynağın önbelleğe alınmış kopyasını kullanarak karşılayan; Aksi takdirde, kaynak sunucudan indirilir, çağırana sunulan ve önbellekte depolanır.</span><span class="sxs-lookup"><span data-stu-id="8525c-127">Satisfies a request by using the cached copy of the resource if the timestamp is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, presented to the caller, and stored in the cache.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8525c-128">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="8525c-128">Child Elements</span></span>  
 <span data-ttu-id="8525c-129">Yok.</span><span class="sxs-lookup"><span data-stu-id="8525c-129">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8525c-130">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="8525c-130">Parent Elements</span></span>  
  
|<span data-ttu-id="8525c-131">Öğe</span><span class="sxs-lookup"><span data-stu-id="8525c-131">Element</span></span>|<span data-ttu-id="8525c-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8525c-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8525c-133">requestCaching</span><span class="sxs-lookup"><span data-stu-id="8525c-133">requestCaching</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)|<span data-ttu-id="8525c-134">Ağ istekleri için önbelleğe alma mekanizması denetler.</span><span class="sxs-lookup"><span data-stu-id="8525c-134">Controls the caching mechanism for network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8525c-135">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8525c-135">Remarks</span></span>  
  
## <a name="example"></a><span data-ttu-id="8525c-136">Örnek</span><span class="sxs-lookup"><span data-stu-id="8525c-136">Example</span></span>  
 <span data-ttu-id="8525c-137">Aşağıdaki örnekte, önbelleğe alma İlkesi, bir FTP belirtmek gösterilmektedir `NoCacheNoStore`.</span><span class="sxs-lookup"><span data-stu-id="8525c-137">The following example shows how to specify an FTP caching policy of `NoCacheNoStore`.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <requestCaching>  
      <defaultFtpCachePolicy  
        policyLevel="NoCacheNoStore">  
      </defaultFtpCachePolicy>  
    </requestCaching>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8525c-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8525c-138">See also</span></span>
- <xref:System.Net.Cache>
- <xref:System.Net.WebRequest>
- <xref:System.Net.Cache.RequestCacheLevel>
- [<span data-ttu-id="8525c-139">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="8525c-139">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
