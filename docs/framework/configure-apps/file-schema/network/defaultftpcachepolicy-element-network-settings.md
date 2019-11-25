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
ms.openlocfilehash: 9261a430642cb4d5ac4507835bd0fd3561bd8c02
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088437"
---
# <a name="defaultftpcachepolicy-element-network-settings"></a><span data-ttu-id="de018-102">\<defaultFtpCachePolicy > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="de018-102">\<defaultFtpCachePolicy> Element (Network Settings)</span></span>
<span data-ttu-id="de018-103">FTP önbelleğe almanın etkin olup olmadığını ve varsayılan önbelleğe alma ilkesini açıklar.</span><span class="sxs-lookup"><span data-stu-id="de018-103">Describes whether FTP caching is active and describes the default caching policy.</span></span>  

<span data-ttu-id="de018-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="de018-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="de018-105">[**System. net >\<** ](system-net-element-network-settings.md) &nbsp;&nbsp;</span><span class="sxs-lookup"><span data-stu-id="de018-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="de018-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<requestCaching >** ](requestcaching-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="de018-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<requestCaching>**](requestcaching-element-network-settings.md)</span></span>\
<span data-ttu-id="de018-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<defaultFtpCachePolicy >**</span><span class="sxs-lookup"><span data-stu-id="de018-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<defaultFtpCachePolicy>**</span></span>

## <a name="syntax"></a><span data-ttu-id="de018-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="de018-108">Syntax</span></span>  
  
```xml  
<defaultFtpCachePolicy  
  policyLevel="BypassCache|Default|CacheOnly|CacheIfAvailable|Revalidate|Reload|NoCacheNoStore|Revalidate"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="de018-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="de018-109">Attributes and Elements</span></span>  
 <span data-ttu-id="de018-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="de018-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="de018-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="de018-111">Attributes</span></span>  
  
|<span data-ttu-id="de018-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="de018-112">Attribute</span></span>|<span data-ttu-id="de018-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="de018-113">Description</span></span>|  
|---------------|-----------------|  
|`policyLevel`|<span data-ttu-id="de018-114">FTP önbelleğe alma ilkesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="de018-114">Specifies the FTP caching policy.</span></span> <span data-ttu-id="de018-115">Varsayılan değer `Default` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="de018-115">The default value is `Default`.</span></span>|  
  
## <a name="policylevel-attribute"></a><span data-ttu-id="de018-116">policyLevel özniteliği</span><span class="sxs-lookup"><span data-stu-id="de018-116">policyLevel Attribute</span></span>  
  
|<span data-ttu-id="de018-117">Değer</span><span class="sxs-lookup"><span data-stu-id="de018-117">Value</span></span>|<span data-ttu-id="de018-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="de018-118">Description</span></span>|  
|-----------|-----------------|  
|`Default`|<span data-ttu-id="de018-119">Kaynak yeni ise, içerik uzunluğu doğru, süre sonu, değişiklik ve içerik uzunluğu öznitelikleri varsa önbelleğe alınmış kaynağı döndürür.</span><span class="sxs-lookup"><span data-stu-id="de018-119">Returns the cached resource if the resource is fresh, the content length is accurate, and the expiration, modification, and content length attributes are present.</span></span>|  
|`BypassCache`|<span data-ttu-id="de018-120">Sunucudan kaynağı döndürür.</span><span class="sxs-lookup"><span data-stu-id="de018-120">Returns the resource from the server.</span></span>|  
|`CacheOnly`|<span data-ttu-id="de018-121">İçerik uzunluğu varsa ve giriş boyutuyla eşleşiyorsa, önbelleğe alınmış kaynağı döndürür.</span><span class="sxs-lookup"><span data-stu-id="de018-121">Returns the cached resource if the content length is present and matches the entry size.</span></span>|  
|`CacheIfAvailable`|<span data-ttu-id="de018-122">İçerik uzunluğu sağlanmışsa ve giriş boyutuyla eşleşiyorsa, önbelleğe alınmış kaynağı döndürür; Aksi takdirde, kaynak sunucudan indirilir ve çağırana döndürülür.</span><span class="sxs-lookup"><span data-stu-id="de018-122">Returns the cached resource if the content length is provided and matches the entry size; otherwise, the resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="de018-123">Önbelleğe alınan kaynağın zaman damgası sunucudaki kaynağın zaman damgasıyla aynıysa, önbelleğe alınmış kaynağı döndürür; Aksi takdirde, kaynak sunucudan indirilir, önbellekte depolanır ve çağırana döndürülür.</span><span class="sxs-lookup"><span data-stu-id="de018-123">Returns the cached resource if the timestamp of the cached resource is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, stored in the cache, and returned to the caller.</span></span>|  
|`Reload`|<span data-ttu-id="de018-124">Kaynağı sunucudan indirir, önbellekte depolar ve kaynak arayana döndürür.</span><span class="sxs-lookup"><span data-stu-id="de018-124">Downloads the resource from the server, stores it in the cache, and returns the resource to the caller.</span></span>|  
|`NoCacheNoStore`|<span data-ttu-id="de018-125">Önbelleğe alınmış bir kaynak varsa, silinir.</span><span class="sxs-lookup"><span data-stu-id="de018-125">If a cached resource exists, it is deleted.</span></span> <span data-ttu-id="de018-126">Kaynak sunucudan indirilir ve çağırana döndürülür.</span><span class="sxs-lookup"><span data-stu-id="de018-126">The resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="de018-127">Zaman damgası sunucudaki kaynağın zaman damgasıyla aynıysa, kaynağın önbelleğe alınmış kopyasını kullanarak bir isteği karşılar; Aksi takdirde, kaynak, çağırana sunulan ve önbellekte depolanan sunucudan indirilir.</span><span class="sxs-lookup"><span data-stu-id="de018-127">Satisfies a request by using the cached copy of the resource if the timestamp is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, presented to the caller, and stored in the cache.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="de018-128">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="de018-128">Child Elements</span></span>  
 <span data-ttu-id="de018-129">Yok.</span><span class="sxs-lookup"><span data-stu-id="de018-129">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="de018-130">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="de018-130">Parent Elements</span></span>  
  
|<span data-ttu-id="de018-131">Öğe</span><span class="sxs-lookup"><span data-stu-id="de018-131">Element</span></span>|<span data-ttu-id="de018-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="de018-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="de018-133">requestCaching</span><span class="sxs-lookup"><span data-stu-id="de018-133">requestCaching</span></span>](requestcaching-element-network-settings.md)|<span data-ttu-id="de018-134">Ağ istekleri için önbelleğe alma mekanizmasını denetler.</span><span class="sxs-lookup"><span data-stu-id="de018-134">Controls the caching mechanism for network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="de018-135">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="de018-135">Remarks</span></span>  
  
## <a name="example"></a><span data-ttu-id="de018-136">Örnek</span><span class="sxs-lookup"><span data-stu-id="de018-136">Example</span></span>  
 <span data-ttu-id="de018-137">Aşağıdaki örnek, `NoCacheNoStore`FTP önbelleğe alma ilkesinin nasıl yapılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="de018-137">The following example shows how to specify an FTP caching policy of `NoCacheNoStore`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="de018-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="de018-138">See also</span></span>

- <xref:System.Net.Cache>
- <xref:System.Net.WebRequest>
- <xref:System.Net.Cache.RequestCacheLevel>
- [<span data-ttu-id="de018-139">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="de018-139">Network Settings Schema</span></span>](index.md)
