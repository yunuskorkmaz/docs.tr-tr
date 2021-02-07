---
description: 'Daha fazla bilgi edinin: <defaultFtpCachePolicy> öğesi (ağ ayarları)'
title: <defaultFtpCachePolicy> Öğesi (Ağ Ayarları)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultFtpCachePolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching/defaultFtpCachePolicy
helpviewer_keywords:
- <defaultFtpCachePolicy> element
- defaultFtpCachePolicy element
ms.assetid: 0eb0c5cb-dd97-484d-8614-785e88877abb
ms.openlocfilehash: 77150ce0980e96dd949df4b5ad7e4557ed1b991a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99740372"
---
# <a name="defaultftpcachepolicy-element-network-settings"></a><span data-ttu-id="6326f-103">\<defaultFtpCachePolicy> Öğesi (Ağ Ayarları)</span><span class="sxs-lookup"><span data-stu-id="6326f-103">\<defaultFtpCachePolicy> Element (Network Settings)</span></span>

<span data-ttu-id="6326f-104">FTP önbelleğe almanın etkin olup olmadığını ve varsayılan önbelleğe alma ilkesini açıklar.</span><span class="sxs-lookup"><span data-stu-id="6326f-104">Describes whether FTP caching is active and describes the default caching policy.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<requestCaching>**](requestcaching-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<defaultFtpCachePolicy>**

## <a name="syntax"></a><span data-ttu-id="6326f-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="6326f-105">Syntax</span></span>  
  
```xml  
<defaultFtpCachePolicy  
  policyLevel="BypassCache|Default|CacheOnly|CacheIfAvailable|Revalidate|Reload|NoCacheNoStore|Revalidate"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6326f-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="6326f-106">Attributes and Elements</span></span>  

 <span data-ttu-id="6326f-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6326f-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6326f-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6326f-108">Attributes</span></span>  
  
|<span data-ttu-id="6326f-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="6326f-109">Attribute</span></span>|<span data-ttu-id="6326f-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6326f-110">Description</span></span>|  
|---------------|-----------------|  
|`policyLevel`|<span data-ttu-id="6326f-111">FTP önbelleğe alma ilkesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="6326f-111">Specifies the FTP caching policy.</span></span> <span data-ttu-id="6326f-112">`Default` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="6326f-112">The default value is `Default`.</span></span>|  
  
## <a name="policylevel-attribute"></a><span data-ttu-id="6326f-113">policyLevel özniteliği</span><span class="sxs-lookup"><span data-stu-id="6326f-113">policyLevel Attribute</span></span>  
  
|<span data-ttu-id="6326f-114">Değer</span><span class="sxs-lookup"><span data-stu-id="6326f-114">Value</span></span>|<span data-ttu-id="6326f-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6326f-115">Description</span></span>|  
|-----------|-----------------|  
|`Default`|<span data-ttu-id="6326f-116">Kaynak yeni ise, içerik uzunluğu doğru, süre sonu, değişiklik ve içerik uzunluğu öznitelikleri varsa önbelleğe alınmış kaynağı döndürür.</span><span class="sxs-lookup"><span data-stu-id="6326f-116">Returns the cached resource if the resource is fresh, the content length is accurate, and the expiration, modification, and content length attributes are present.</span></span>|  
|`BypassCache`|<span data-ttu-id="6326f-117">Sunucudan kaynağı döndürür.</span><span class="sxs-lookup"><span data-stu-id="6326f-117">Returns the resource from the server.</span></span>|  
|`CacheOnly`|<span data-ttu-id="6326f-118">İçerik uzunluğu varsa ve giriş boyutuyla eşleşiyorsa, önbelleğe alınmış kaynağı döndürür.</span><span class="sxs-lookup"><span data-stu-id="6326f-118">Returns the cached resource if the content length is present and matches the entry size.</span></span>|  
|`CacheIfAvailable`|<span data-ttu-id="6326f-119">İçerik uzunluğu sağlanmışsa ve giriş boyutuyla eşleşiyorsa, önbelleğe alınmış kaynağı döndürür; Aksi takdirde, kaynak sunucudan indirilir ve çağırana döndürülür.</span><span class="sxs-lookup"><span data-stu-id="6326f-119">Returns the cached resource if the content length is provided and matches the entry size; otherwise, the resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="6326f-120">Önbelleğe alınan kaynağın zaman damgası sunucudaki kaynağın zaman damgasıyla aynıysa, önbelleğe alınmış kaynağı döndürür; Aksi takdirde, kaynak sunucudan indirilir, önbellekte depolanır ve çağırana döndürülür.</span><span class="sxs-lookup"><span data-stu-id="6326f-120">Returns the cached resource if the timestamp of the cached resource is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, stored in the cache, and returned to the caller.</span></span>|  
|`Reload`|<span data-ttu-id="6326f-121">Kaynağı sunucudan indirir, önbellekte depolar ve kaynak arayana döndürür.</span><span class="sxs-lookup"><span data-stu-id="6326f-121">Downloads the resource from the server, stores it in the cache, and returns the resource to the caller.</span></span>|  
|`NoCacheNoStore`|<span data-ttu-id="6326f-122">Önbelleğe alınmış bir kaynak varsa, silinir.</span><span class="sxs-lookup"><span data-stu-id="6326f-122">If a cached resource exists, it is deleted.</span></span> <span data-ttu-id="6326f-123">Kaynak sunucudan indirilir ve çağırana döndürülür.</span><span class="sxs-lookup"><span data-stu-id="6326f-123">The resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="6326f-124">Zaman damgası sunucudaki kaynağın zaman damgasıyla aynıysa, kaynağın önbelleğe alınmış kopyasını kullanarak bir isteği karşılar; Aksi takdirde, kaynak, çağırana sunulan ve önbellekte depolanan sunucudan indirilir.</span><span class="sxs-lookup"><span data-stu-id="6326f-124">Satisfies a request by using the cached copy of the resource if the timestamp is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, presented to the caller, and stored in the cache.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6326f-125">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="6326f-125">Child Elements</span></span>  

 <span data-ttu-id="6326f-126">Yok.</span><span class="sxs-lookup"><span data-stu-id="6326f-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6326f-127">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="6326f-127">Parent Elements</span></span>  
  
|<span data-ttu-id="6326f-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="6326f-128">Element</span></span>|<span data-ttu-id="6326f-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6326f-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6326f-130">requestCaching</span><span class="sxs-lookup"><span data-stu-id="6326f-130">requestCaching</span></span>](requestcaching-element-network-settings.md)|<span data-ttu-id="6326f-131">Ağ istekleri için önbelleğe alma mekanizmasını denetler.</span><span class="sxs-lookup"><span data-stu-id="6326f-131">Controls the caching mechanism for network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6326f-132">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6326f-132">Remarks</span></span>  
  
## <a name="example"></a><span data-ttu-id="6326f-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="6326f-133">Example</span></span>  

 <span data-ttu-id="6326f-134">Aşağıdaki örnek, ' nin bir FTP önbelleğe alma ilkesinin nasıl ekleneceğini gösterir `NoCacheNoStore` .</span><span class="sxs-lookup"><span data-stu-id="6326f-134">The following example shows how to specify an FTP caching policy of `NoCacheNoStore`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6326f-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6326f-135">See also</span></span>

- <xref:System.Net.Cache>
- <xref:System.Net.WebRequest>
- <xref:System.Net.Cache.RequestCacheLevel>
- [<span data-ttu-id="6326f-136">Ağ ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="6326f-136">Network Settings Schema</span></span>](index.md)
