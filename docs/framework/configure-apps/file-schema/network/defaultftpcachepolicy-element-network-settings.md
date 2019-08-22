---
title: <defaultFtpCachePolicy> Öğesi (Ağ Ayarları)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultFtpCachePolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching/defaultFtpCachePolicy
helpviewer_keywords:
- <defaultFtpCachePolicy> element
- defaultFtpCachePolicy element
ms.assetid: 0eb0c5cb-dd97-484d-8614-785e88877abb
ms.openlocfilehash: 7ff44f0251936d51b4e396c37c53322efa110227
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659416"
---
# <a name="defaultftpcachepolicy-element-network-settings"></a><span data-ttu-id="9a17f-102">\<defaultFtpCachePolicy > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="9a17f-102">\<defaultFtpCachePolicy> Element (Network Settings)</span></span>
<span data-ttu-id="9a17f-103">FTP önbelleğe almanın etkin olup olmadığını ve varsayılan önbelleğe alma ilkesini açıklar.</span><span class="sxs-lookup"><span data-stu-id="9a17f-103">Describes whether FTP caching is active and describes the default caching policy.</span></span>  
  
 <span data-ttu-id="9a17f-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="9a17f-104">\<configuration></span></span>  
<span data-ttu-id="9a17f-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="9a17f-105">\<system.net></span></span>  
<span data-ttu-id="9a17f-106">\<requestCaching ></span><span class="sxs-lookup"><span data-stu-id="9a17f-106">\<requestCaching></span></span>  
<span data-ttu-id="9a17f-107">\<defaultFtpCachePolicy ></span><span class="sxs-lookup"><span data-stu-id="9a17f-107">\<defaultFtpCachePolicy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a17f-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9a17f-108">Syntax</span></span>  
  
```xml  
<defaultFtpCachePolicy  
  policyLevel="BypassCache|Default|CacheOnly|CacheIfAvailable|Revalidate|Reload|NoCacheNoStore|Revalidate"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9a17f-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="9a17f-109">Attributes and Elements</span></span>  
 <span data-ttu-id="9a17f-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9a17f-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9a17f-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="9a17f-111">Attributes</span></span>  
  
|<span data-ttu-id="9a17f-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="9a17f-112">Attribute</span></span>|<span data-ttu-id="9a17f-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9a17f-113">Description</span></span>|  
|---------------|-----------------|  
|`policyLevel`|<span data-ttu-id="9a17f-114">FTP önbelleğe alma ilkesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="9a17f-114">Specifies the FTP caching policy.</span></span> <span data-ttu-id="9a17f-115">Varsayılan değer `Default` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="9a17f-115">The default value is `Default`.</span></span>|  
  
## <a name="policylevel-attribute"></a><span data-ttu-id="9a17f-116">policyLevel özniteliği</span><span class="sxs-lookup"><span data-stu-id="9a17f-116">policyLevel Attribute</span></span>  
  
|<span data-ttu-id="9a17f-117">Değer</span><span class="sxs-lookup"><span data-stu-id="9a17f-117">Value</span></span>|<span data-ttu-id="9a17f-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9a17f-118">Description</span></span>|  
|-----------|-----------------|  
|`Default`|<span data-ttu-id="9a17f-119">Kaynak yeni ise, içerik uzunluğu doğru, süre sonu, değişiklik ve içerik uzunluğu öznitelikleri varsa önbelleğe alınmış kaynağı döndürür.</span><span class="sxs-lookup"><span data-stu-id="9a17f-119">Returns the cached resource if the resource is fresh, the content length is accurate, and the expiration, modification, and content length attributes are present.</span></span>|  
|`BypassCache`|<span data-ttu-id="9a17f-120">Sunucudan kaynağı döndürür.</span><span class="sxs-lookup"><span data-stu-id="9a17f-120">Returns the resource from the server.</span></span>|  
|`CacheOnly`|<span data-ttu-id="9a17f-121">İçerik uzunluğu varsa ve giriş boyutuyla eşleşiyorsa, önbelleğe alınmış kaynağı döndürür.</span><span class="sxs-lookup"><span data-stu-id="9a17f-121">Returns the cached resource if the content length is present and matches the entry size.</span></span>|  
|`CacheIfAvailable`|<span data-ttu-id="9a17f-122">İçerik uzunluğu sağlanmışsa ve giriş boyutuyla eşleşiyorsa, önbelleğe alınmış kaynağı döndürür; Aksi takdirde, kaynak sunucudan indirilir ve çağırana döndürülür.</span><span class="sxs-lookup"><span data-stu-id="9a17f-122">Returns the cached resource if the content length is provided and matches the entry size; otherwise, the resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="9a17f-123">Önbelleğe alınan kaynağın zaman damgası sunucudaki kaynağın zaman damgasıyla aynıysa, önbelleğe alınmış kaynağı döndürür; Aksi takdirde, kaynak sunucudan indirilir, önbellekte depolanır ve çağırana döndürülür.</span><span class="sxs-lookup"><span data-stu-id="9a17f-123">Returns the cached resource if the timestamp of the cached resource is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, stored in the cache, and returned to the caller.</span></span>|  
|`Reload`|<span data-ttu-id="9a17f-124">Kaynağı sunucudan indirir, önbellekte depolar ve kaynak arayana döndürür.</span><span class="sxs-lookup"><span data-stu-id="9a17f-124">Downloads the resource from the server, stores it in the cache, and returns the resource to the caller.</span></span>|  
|`NoCacheNoStore`|<span data-ttu-id="9a17f-125">Önbelleğe alınmış bir kaynak varsa, silinir.</span><span class="sxs-lookup"><span data-stu-id="9a17f-125">If a cached resource exists, it is deleted.</span></span> <span data-ttu-id="9a17f-126">Kaynak sunucudan indirilir ve çağırana döndürülür.</span><span class="sxs-lookup"><span data-stu-id="9a17f-126">The resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="9a17f-127">Zaman damgası sunucudaki kaynağın zaman damgasıyla aynıysa, kaynağın önbelleğe alınmış kopyasını kullanarak bir isteği karşılar; Aksi takdirde, kaynak, çağırana sunulan ve önbellekte depolanan sunucudan indirilir.</span><span class="sxs-lookup"><span data-stu-id="9a17f-127">Satisfies a request by using the cached copy of the resource if the timestamp is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, presented to the caller, and stored in the cache.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9a17f-128">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="9a17f-128">Child Elements</span></span>  
 <span data-ttu-id="9a17f-129">Yok.</span><span class="sxs-lookup"><span data-stu-id="9a17f-129">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9a17f-130">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="9a17f-130">Parent Elements</span></span>  
  
|<span data-ttu-id="9a17f-131">Öğe</span><span class="sxs-lookup"><span data-stu-id="9a17f-131">Element</span></span>|<span data-ttu-id="9a17f-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9a17f-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9a17f-133">requestCaching</span><span class="sxs-lookup"><span data-stu-id="9a17f-133">requestCaching</span></span>](requestcaching-element-network-settings.md)|<span data-ttu-id="9a17f-134">Ağ istekleri için önbelleğe alma mekanizmasını denetler.</span><span class="sxs-lookup"><span data-stu-id="9a17f-134">Controls the caching mechanism for network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9a17f-135">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9a17f-135">Remarks</span></span>  
  
## <a name="example"></a><span data-ttu-id="9a17f-136">Örnek</span><span class="sxs-lookup"><span data-stu-id="9a17f-136">Example</span></span>  
 <span data-ttu-id="9a17f-137">Aşağıdaki örnek, ' nin `NoCacheNoStore`bir FTP önbelleğe alma ilkesinin nasıl ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="9a17f-137">The following example shows how to specify an FTP caching policy of `NoCacheNoStore`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9a17f-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9a17f-138">See also</span></span>

- <xref:System.Net.Cache>
- <xref:System.Net.WebRequest>
- <xref:System.Net.Cache.RequestCacheLevel>
- [<span data-ttu-id="9a17f-139">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="9a17f-139">Network Settings Schema</span></span>](index.md)
