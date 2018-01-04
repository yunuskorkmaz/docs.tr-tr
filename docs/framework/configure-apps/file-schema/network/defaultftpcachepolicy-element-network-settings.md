---
title: "&lt;defaultFtpCachePolicy&gt; öğesi (ağ ayarları)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultFtpCachePolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching/defaultFtpCachePolicy
helpviewer_keywords:
- <defaultFtpCachePolicy> element
- defaultFtpCachePolicy element
ms.assetid: 0eb0c5cb-dd97-484d-8614-785e88877abb
caps.latest.revision: "13"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 0c62be73db6d9d0b6ce67dd87021c589502d5fec
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltdefaultftpcachepolicygt-element-network-settings"></a><span data-ttu-id="70de3-102">&lt;defaultFtpCachePolicy&gt; öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="70de3-102">&lt;defaultFtpCachePolicy&gt; Element (Network Settings)</span></span>
<span data-ttu-id="70de3-103">FTP önbelleğe alma etkindir ve ilke önbelleğe almayı varsayılan açıklar olup olmadığını açıklar.</span><span class="sxs-lookup"><span data-stu-id="70de3-103">Describes whether FTP caching is active and describes the default caching policy.</span></span>  
  
 <span data-ttu-id="70de3-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="70de3-104">\<configuration></span></span>  
<span data-ttu-id="70de3-105">\<System.NET ></span><span class="sxs-lookup"><span data-stu-id="70de3-105">\<system.net></span></span>  
<span data-ttu-id="70de3-106">\<requestCaching ></span><span class="sxs-lookup"><span data-stu-id="70de3-106">\<requestCaching></span></span>  
<span data-ttu-id="70de3-107">\<defaultFtpCachePolicy ></span><span class="sxs-lookup"><span data-stu-id="70de3-107">\<defaultFtpCachePolicy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70de3-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="70de3-108">Syntax</span></span>  
  
```xml  
<defaultFtpCachePolicy  
  policyLevel="BypassCache|Default|CacheOnly|CacheIfAvailable|Revalidate|Reload|NoCacheNoStore|Revalidate"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="70de3-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="70de3-109">Attributes and Elements</span></span>  
 <span data-ttu-id="70de3-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="70de3-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="70de3-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="70de3-111">Attributes</span></span>  
  
|<span data-ttu-id="70de3-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="70de3-112">Attribute</span></span>|<span data-ttu-id="70de3-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="70de3-113">Description</span></span>|  
|---------------|-----------------|  
|`policyLevel`|<span data-ttu-id="70de3-114">İlke önbelleği FTP belirtir.</span><span class="sxs-lookup"><span data-stu-id="70de3-114">Specifies the FTP caching policy.</span></span> <span data-ttu-id="70de3-115">Varsayılan değer `Default` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="70de3-115">The default value is `Default`.</span></span>|  
  
## <a name="policylevel-attribute"></a><span data-ttu-id="70de3-116">policyLevel özniteliği</span><span class="sxs-lookup"><span data-stu-id="70de3-116">policyLevel Attribute</span></span>  
  
|<span data-ttu-id="70de3-117">Değer</span><span class="sxs-lookup"><span data-stu-id="70de3-117">Value</span></span>|<span data-ttu-id="70de3-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="70de3-118">Description</span></span>|  
|-----------|-----------------|  
|`Default`|<span data-ttu-id="70de3-119">Önbelleğe alınan kaynak yeni bir kaynaktır, içerik uzunluğu doğru olduğundan ve süre sonu, değiştirilmesi ve içerik uzunluğu öznitelikleri mevcut döndürür.</span><span class="sxs-lookup"><span data-stu-id="70de3-119">Returns the cached resource if the resource is fresh, the content length is accurate, and the expiration, modification, and content length attributes are present.</span></span>|  
|`BypassCache`|<span data-ttu-id="70de3-120">Kaynak sunucudan döndürür.</span><span class="sxs-lookup"><span data-stu-id="70de3-120">Returns the resource from the server.</span></span>|  
|`CacheOnly`|<span data-ttu-id="70de3-121">İçerik uzunluğu varsa ve giriş boyutu eşleşen önbelleğe alınan kaynak döndürür.</span><span class="sxs-lookup"><span data-stu-id="70de3-121">Returns the cached resource if the content length is present and matches the entry size.</span></span>|  
|`CacheIfAvailable`|<span data-ttu-id="70de3-122">İçerik uzunluğu sağlanır ve giriş boyutu eşleşiyorsa önbelleğe alınan kaynak döndürür; Aksi halde, kaynak sunucudan indirilir ve çağırana döndürülür.</span><span class="sxs-lookup"><span data-stu-id="70de3-122">Returns the cached resource if the content length is provided and matches the entry size; otherwise, the resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="70de3-123">Önbelleğe alınan kaynak damgası kaynak sunucuda damgası ile aynı olduğunda önbelleğe alınan kaynak döndürür; Aksi halde, kaynak sunucudan, önbellekte depolanır ve yapana.</span><span class="sxs-lookup"><span data-stu-id="70de3-123">Returns the cached resource if the timestamp of the cached resource is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, stored in the cache, and returned to the caller.</span></span>|  
|`Reload`|<span data-ttu-id="70de3-124">Kaynak sunucudan indirir, önbellekte depolar ve kaynak çağırana döndürür.</span><span class="sxs-lookup"><span data-stu-id="70de3-124">Downloads the resource from the server, stores it in the cache, and returns the resource to the caller.</span></span>|  
|`NoCacheNoStore`|<span data-ttu-id="70de3-125">Önbelleğe alınan bir kaynak zaten varsa, bu silinir.</span><span class="sxs-lookup"><span data-stu-id="70de3-125">If a cached resource exists, it is deleted.</span></span> <span data-ttu-id="70de3-126">Kaynak sunucudan indirilir ve çağırana döndürülür.</span><span class="sxs-lookup"><span data-stu-id="70de3-126">The resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="70de3-127">Bir istek zaman damgası kaynak sunucuda damgası ile aynı olduğunda, kaynak önbelleğe alınmış bir kopyasını kullanarak karşılayan; Aksi halde, kaynak sunucudan, çağırana sunulan ve önbellekte depolanır.</span><span class="sxs-lookup"><span data-stu-id="70de3-127">Satisfies a request by using the cached copy of the resource if the timestamp is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, presented to the caller, and stored in the cache.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="70de3-128">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="70de3-128">Child Elements</span></span>  
 <span data-ttu-id="70de3-129">Yok.</span><span class="sxs-lookup"><span data-stu-id="70de3-129">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="70de3-130">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="70de3-130">Parent Elements</span></span>  
  
|<span data-ttu-id="70de3-131">Öğe</span><span class="sxs-lookup"><span data-stu-id="70de3-131">Element</span></span>|<span data-ttu-id="70de3-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="70de3-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="70de3-133">requestCaching</span><span class="sxs-lookup"><span data-stu-id="70de3-133">requestCaching</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)|<span data-ttu-id="70de3-134">Ağ isteği önbelleğe alma mekanizması denetler.</span><span class="sxs-lookup"><span data-stu-id="70de3-134">Controls the caching mechanism for network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="70de3-135">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="70de3-135">Remarks</span></span>  
  
## <a name="example"></a><span data-ttu-id="70de3-136">Örnek</span><span class="sxs-lookup"><span data-stu-id="70de3-136">Example</span></span>  
 <span data-ttu-id="70de3-137">Aşağıdaki örnekte, önbelleğe alma İlkesi, bir FTP belirtmek gösterilmiştir `NoCacheNoStore`.</span><span class="sxs-lookup"><span data-stu-id="70de3-137">The following example shows how to specify an FTP caching policy of `NoCacheNoStore`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="70de3-138">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="70de3-138">See Also</span></span>  
 <xref:System.Net.Cache>  
 <xref:System.Net.WebRequest>  
 <xref:System.Net.Cache.RequestCacheLevel>  
 [<span data-ttu-id="70de3-139">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="70de3-139">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
