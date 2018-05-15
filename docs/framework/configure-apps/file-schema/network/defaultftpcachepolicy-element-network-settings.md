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
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: e4ea16c925114d4ad4054af5f340c764ed6fe4fd
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltdefaultftpcachepolicygt-element-network-settings"></a><span data-ttu-id="0e702-102">&lt;defaultFtpCachePolicy&gt; öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="0e702-102">&lt;defaultFtpCachePolicy&gt; Element (Network Settings)</span></span>
<span data-ttu-id="0e702-103">FTP önbelleğe alma etkindir ve ilke önbelleğe almayı varsayılan açıklar olup olmadığını açıklar.</span><span class="sxs-lookup"><span data-stu-id="0e702-103">Describes whether FTP caching is active and describes the default caching policy.</span></span>  
  
 <span data-ttu-id="0e702-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="0e702-104">\<configuration></span></span>  
<span data-ttu-id="0e702-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="0e702-105">\<system.net></span></span>  
<span data-ttu-id="0e702-106">\<requestCaching ></span><span class="sxs-lookup"><span data-stu-id="0e702-106">\<requestCaching></span></span>  
<span data-ttu-id="0e702-107">\<defaultFtpCachePolicy ></span><span class="sxs-lookup"><span data-stu-id="0e702-107">\<defaultFtpCachePolicy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e702-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0e702-108">Syntax</span></span>  
  
```xml  
<defaultFtpCachePolicy  
  policyLevel="BypassCache|Default|CacheOnly|CacheIfAvailable|Revalidate|Reload|NoCacheNoStore|Revalidate"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0e702-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="0e702-109">Attributes and Elements</span></span>  
 <span data-ttu-id="0e702-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0e702-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0e702-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0e702-111">Attributes</span></span>  
  
|<span data-ttu-id="0e702-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="0e702-112">Attribute</span></span>|<span data-ttu-id="0e702-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0e702-113">Description</span></span>|  
|---------------|-----------------|  
|`policyLevel`|<span data-ttu-id="0e702-114">İlke önbelleği FTP belirtir.</span><span class="sxs-lookup"><span data-stu-id="0e702-114">Specifies the FTP caching policy.</span></span> <span data-ttu-id="0e702-115">Varsayılan değer `Default` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="0e702-115">The default value is `Default`.</span></span>|  
  
## <a name="policylevel-attribute"></a><span data-ttu-id="0e702-116">policyLevel özniteliği</span><span class="sxs-lookup"><span data-stu-id="0e702-116">policyLevel Attribute</span></span>  
  
|<span data-ttu-id="0e702-117">Değer</span><span class="sxs-lookup"><span data-stu-id="0e702-117">Value</span></span>|<span data-ttu-id="0e702-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0e702-118">Description</span></span>|  
|-----------|-----------------|  
|`Default`|<span data-ttu-id="0e702-119">Önbelleğe alınan kaynak yeni bir kaynaktır, içerik uzunluğu doğru olduğundan ve süre sonu, değiştirilmesi ve içerik uzunluğu öznitelikleri mevcut döndürür.</span><span class="sxs-lookup"><span data-stu-id="0e702-119">Returns the cached resource if the resource is fresh, the content length is accurate, and the expiration, modification, and content length attributes are present.</span></span>|  
|`BypassCache`|<span data-ttu-id="0e702-120">Kaynak sunucudan döndürür.</span><span class="sxs-lookup"><span data-stu-id="0e702-120">Returns the resource from the server.</span></span>|  
|`CacheOnly`|<span data-ttu-id="0e702-121">İçerik uzunluğu varsa ve giriş boyutu eşleşen önbelleğe alınan kaynak döndürür.</span><span class="sxs-lookup"><span data-stu-id="0e702-121">Returns the cached resource if the content length is present and matches the entry size.</span></span>|  
|`CacheIfAvailable`|<span data-ttu-id="0e702-122">İçerik uzunluğu sağlanır ve giriş boyutu eşleşiyorsa önbelleğe alınan kaynak döndürür; Aksi halde, kaynak sunucudan indirilir ve çağırana döndürülür.</span><span class="sxs-lookup"><span data-stu-id="0e702-122">Returns the cached resource if the content length is provided and matches the entry size; otherwise, the resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="0e702-123">Önbelleğe alınan kaynak damgası kaynak sunucuda damgası ile aynı olduğunda önbelleğe alınan kaynak döndürür; Aksi halde, kaynak sunucudan, önbellekte depolanır ve yapana.</span><span class="sxs-lookup"><span data-stu-id="0e702-123">Returns the cached resource if the timestamp of the cached resource is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, stored in the cache, and returned to the caller.</span></span>|  
|`Reload`|<span data-ttu-id="0e702-124">Kaynak sunucudan indirir, önbellekte depolar ve kaynak çağırana döndürür.</span><span class="sxs-lookup"><span data-stu-id="0e702-124">Downloads the resource from the server, stores it in the cache, and returns the resource to the caller.</span></span>|  
|`NoCacheNoStore`|<span data-ttu-id="0e702-125">Önbelleğe alınan bir kaynak zaten varsa, bu silinir.</span><span class="sxs-lookup"><span data-stu-id="0e702-125">If a cached resource exists, it is deleted.</span></span> <span data-ttu-id="0e702-126">Kaynak sunucudan indirilir ve çağırana döndürülür.</span><span class="sxs-lookup"><span data-stu-id="0e702-126">The resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="0e702-127">Bir istek zaman damgası kaynak sunucuda damgası ile aynı olduğunda, kaynak önbelleğe alınmış bir kopyasını kullanarak karşılayan; Aksi halde, kaynak sunucudan, çağırana sunulan ve önbellekte depolanır.</span><span class="sxs-lookup"><span data-stu-id="0e702-127">Satisfies a request by using the cached copy of the resource if the timestamp is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, presented to the caller, and stored in the cache.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0e702-128">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="0e702-128">Child Elements</span></span>  
 <span data-ttu-id="0e702-129">Yok.</span><span class="sxs-lookup"><span data-stu-id="0e702-129">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0e702-130">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="0e702-130">Parent Elements</span></span>  
  
|<span data-ttu-id="0e702-131">Öğe</span><span class="sxs-lookup"><span data-stu-id="0e702-131">Element</span></span>|<span data-ttu-id="0e702-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0e702-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0e702-133">requestCaching</span><span class="sxs-lookup"><span data-stu-id="0e702-133">requestCaching</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)|<span data-ttu-id="0e702-134">Ağ isteği önbelleğe alma mekanizması denetler.</span><span class="sxs-lookup"><span data-stu-id="0e702-134">Controls the caching mechanism for network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0e702-135">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0e702-135">Remarks</span></span>  
  
## <a name="example"></a><span data-ttu-id="0e702-136">Örnek</span><span class="sxs-lookup"><span data-stu-id="0e702-136">Example</span></span>  
 <span data-ttu-id="0e702-137">Aşağıdaki örnekte, önbelleğe alma İlkesi, bir FTP belirtmek gösterilmiştir `NoCacheNoStore`.</span><span class="sxs-lookup"><span data-stu-id="0e702-137">The following example shows how to specify an FTP caching policy of `NoCacheNoStore`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0e702-138">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0e702-138">See Also</span></span>  
 <xref:System.Net.Cache>  
 <xref:System.Net.WebRequest>  
 <xref:System.Net.Cache.RequestCacheLevel>  
 [<span data-ttu-id="0e702-139">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="0e702-139">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
