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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "74088437"
---
# <a name="defaultftpcachepolicy-element-network-settings"></a><span data-ttu-id="43573-102">\<defaultFtpCachePolicy> Öğesi (Ağ Ayarları)</span><span class="sxs-lookup"><span data-stu-id="43573-102">\<defaultFtpCachePolicy> Element (Network Settings)</span></span>
<span data-ttu-id="43573-103">FTP önbelleğe almanın etkin olup olmadığını ve varsayılan önbelleğe alma ilkesini açıklar.</span><span class="sxs-lookup"><span data-stu-id="43573-103">Describes whether FTP caching is active and describes the default caching policy.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<requestCaching>**](requestcaching-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<defaultFtpCachePolicy>**

## <a name="syntax"></a><span data-ttu-id="43573-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="43573-104">Syntax</span></span>  
  
```xml  
<defaultFtpCachePolicy  
  policyLevel="BypassCache|Default|CacheOnly|CacheIfAvailable|Revalidate|Reload|NoCacheNoStore|Revalidate"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="43573-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="43573-105">Attributes and Elements</span></span>  
 <span data-ttu-id="43573-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="43573-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="43573-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="43573-107">Attributes</span></span>  
  
|<span data-ttu-id="43573-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="43573-108">Attribute</span></span>|<span data-ttu-id="43573-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="43573-109">Description</span></span>|  
|---------------|-----------------|  
|`policyLevel`|<span data-ttu-id="43573-110">FTP önbelleğe alma ilkesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="43573-110">Specifies the FTP caching policy.</span></span> <span data-ttu-id="43573-111">Varsayılan değer: `Default`.</span><span class="sxs-lookup"><span data-stu-id="43573-111">The default value is `Default`.</span></span>|  
  
## <a name="policylevel-attribute"></a><span data-ttu-id="43573-112">policyLevel özniteliği</span><span class="sxs-lookup"><span data-stu-id="43573-112">policyLevel Attribute</span></span>  
  
|<span data-ttu-id="43573-113">Değer</span><span class="sxs-lookup"><span data-stu-id="43573-113">Value</span></span>|<span data-ttu-id="43573-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="43573-114">Description</span></span>|  
|-----------|-----------------|  
|`Default`|<span data-ttu-id="43573-115">Kaynak yeni ise, içerik uzunluğu doğru, süre sonu, değişiklik ve içerik uzunluğu öznitelikleri varsa önbelleğe alınmış kaynağı döndürür.</span><span class="sxs-lookup"><span data-stu-id="43573-115">Returns the cached resource if the resource is fresh, the content length is accurate, and the expiration, modification, and content length attributes are present.</span></span>|  
|`BypassCache`|<span data-ttu-id="43573-116">Sunucudan kaynağı döndürür.</span><span class="sxs-lookup"><span data-stu-id="43573-116">Returns the resource from the server.</span></span>|  
|`CacheOnly`|<span data-ttu-id="43573-117">İçerik uzunluğu varsa ve giriş boyutuyla eşleşiyorsa, önbelleğe alınmış kaynağı döndürür.</span><span class="sxs-lookup"><span data-stu-id="43573-117">Returns the cached resource if the content length is present and matches the entry size.</span></span>|  
|`CacheIfAvailable`|<span data-ttu-id="43573-118">İçerik uzunluğu sağlanmışsa ve giriş boyutuyla eşleşiyorsa, önbelleğe alınmış kaynağı döndürür; Aksi takdirde, kaynak sunucudan indirilir ve çağırana döndürülür.</span><span class="sxs-lookup"><span data-stu-id="43573-118">Returns the cached resource if the content length is provided and matches the entry size; otherwise, the resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="43573-119">Önbelleğe alınan kaynağın zaman damgası sunucudaki kaynağın zaman damgasıyla aynıysa, önbelleğe alınmış kaynağı döndürür; Aksi takdirde, kaynak sunucudan indirilir, önbellekte depolanır ve çağırana döndürülür.</span><span class="sxs-lookup"><span data-stu-id="43573-119">Returns the cached resource if the timestamp of the cached resource is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, stored in the cache, and returned to the caller.</span></span>|  
|`Reload`|<span data-ttu-id="43573-120">Kaynağı sunucudan indirir, önbellekte depolar ve kaynak arayana döndürür.</span><span class="sxs-lookup"><span data-stu-id="43573-120">Downloads the resource from the server, stores it in the cache, and returns the resource to the caller.</span></span>|  
|`NoCacheNoStore`|<span data-ttu-id="43573-121">Önbelleğe alınmış bir kaynak varsa, silinir.</span><span class="sxs-lookup"><span data-stu-id="43573-121">If a cached resource exists, it is deleted.</span></span> <span data-ttu-id="43573-122">Kaynak sunucudan indirilir ve çağırana döndürülür.</span><span class="sxs-lookup"><span data-stu-id="43573-122">The resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="43573-123">Zaman damgası sunucudaki kaynağın zaman damgasıyla aynıysa, kaynağın önbelleğe alınmış kopyasını kullanarak bir isteği karşılar; Aksi takdirde, kaynak, çağırana sunulan ve önbellekte depolanan sunucudan indirilir.</span><span class="sxs-lookup"><span data-stu-id="43573-123">Satisfies a request by using the cached copy of the resource if the timestamp is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, presented to the caller, and stored in the cache.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="43573-124">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="43573-124">Child Elements</span></span>  
 <span data-ttu-id="43573-125">Yok.</span><span class="sxs-lookup"><span data-stu-id="43573-125">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="43573-126">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="43573-126">Parent Elements</span></span>  
  
|<span data-ttu-id="43573-127">Öğe</span><span class="sxs-lookup"><span data-stu-id="43573-127">Element</span></span>|<span data-ttu-id="43573-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="43573-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="43573-129">requestCaching</span><span class="sxs-lookup"><span data-stu-id="43573-129">requestCaching</span></span>](requestcaching-element-network-settings.md)|<span data-ttu-id="43573-130">Ağ istekleri için önbelleğe alma mekanizmasını denetler.</span><span class="sxs-lookup"><span data-stu-id="43573-130">Controls the caching mechanism for network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="43573-131">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="43573-131">Remarks</span></span>  
  
## <a name="example"></a><span data-ttu-id="43573-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="43573-132">Example</span></span>  
 <span data-ttu-id="43573-133">Aşağıdaki örnek, ' nin bir FTP önbelleğe alma ilkesinin nasıl ekleneceğini gösterir `NoCacheNoStore` .</span><span class="sxs-lookup"><span data-stu-id="43573-133">The following example shows how to specify an FTP caching policy of `NoCacheNoStore`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="43573-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="43573-134">See also</span></span>

- <xref:System.Net.Cache>
- <xref:System.Net.WebRequest>
- <xref:System.Net.Cache.RequestCacheLevel>
- [<span data-ttu-id="43573-135">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="43573-135">Network Settings Schema</span></span>](index.md)
