---
description: 'Daha fazla bilgi edinin: <requestCaching> öğesi (ağ ayarları)'
title: <requestCaching> Öğesi (Ağ Ayarları)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#requestCaching
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching
helpviewer_keywords:
- requestCaching element
- <requestCaching> element
ms.assetid: 9962a2fe-cbda-41a6-9377-571811eaea84
ms.openlocfilehash: d09da8ad7a38ac363aaa740cca4de25e33fa8c56
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99698563"
---
# <a name="requestcaching-element-network-settings"></a><span data-ttu-id="70dce-103">\<requestCaching> Öğesi (Ağ Ayarları)</span><span class="sxs-lookup"><span data-stu-id="70dce-103">\<requestCaching> Element (Network Settings)</span></span>

<span data-ttu-id="70dce-104">Ağ istekleri için önbelleğe alma mekanizmasını denetler.</span><span class="sxs-lookup"><span data-stu-id="70dce-104">Controls the caching mechanism for network requests.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<requestCaching>**  
  
## <a name="syntax"></a><span data-ttu-id="70dce-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="70dce-105">Syntax</span></span>  
  
```xml  
<requestCaching  
  isPrivateCache ="true|false"  
  disableAllCaching="true|false"  
  defaultPolicyLevel="BypassCache|Default|CacheOnly|CacheIfAvailable|Revalidate|Reload|NoCacheNoStore|Revalidate"  
  unspecifiedMaximumAge= "d.hh:mm:ss">  
    <defaultHttpCachePolicy>...</defaultHttpCachePolicy>  
    <defaultFtpCachePolicy>...</defaultFtpCachePolicy>  
</requestCaching>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="70dce-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="70dce-106">Attributes and Elements</span></span>  

 <span data-ttu-id="70dce-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="70dce-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="70dce-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="70dce-108">Attributes</span></span>  
  
|<span data-ttu-id="70dce-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="70dce-109">Attribute</span></span>|<span data-ttu-id="70dce-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="70dce-110">Description</span></span>|  
|---------------|-----------------|  
|`isPrivateCache`|<span data-ttu-id="70dce-111">Önbelleğin, farklı kullanıcıların bilgileri arasında yalıtım verip içermediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="70dce-111">Specifies whether the cache provides isolation between the information of different users.</span></span> <span data-ttu-id="70dce-112">`true` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="70dce-112">The default value is `true`.</span></span> <span data-ttu-id="70dce-113">Bu değer, `false` Orta katman uygulamalar için olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="70dce-113">This value should be `false` for middle tier applications.</span></span>|  
|`disableAllCaching`|<span data-ttu-id="70dce-114">Tüm Web yanıtları için önbelleğe almanın devre dışı bırakıldığını belirtir ve program aracılığıyla geçersiz kılınamaz.</span><span class="sxs-lookup"><span data-stu-id="70dce-114">Specifies that caching is disabled for all Web responses, and cannot be overridden programmatically.</span></span>|  
|`defaultPolicyLevel`|<span data-ttu-id="70dce-115"><xref:System.Net.Cache.RequestCacheLevel>Numaralandırmadaki değerlerden biri.</span><span class="sxs-lookup"><span data-stu-id="70dce-115">One of the values in the <xref:System.Net.Cache.RequestCacheLevel> enumeration.</span></span> <span data-ttu-id="70dce-116">`BypassCache` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="70dce-116">The default value is `BypassCache`.</span></span>|  
|`unspecifiedMaximumAge`|<span data-ttu-id="70dce-117">İçeriğin süresi dolduğunda, varsayılan süreyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="70dce-117">Specifies the default time after which content is marked as expired.</span></span>|  
  
## <a name="policylevel-attribute"></a><span data-ttu-id="70dce-118">policyLevel özniteliği</span><span class="sxs-lookup"><span data-stu-id="70dce-118">policyLevel Attribute</span></span>  
  
|<span data-ttu-id="70dce-119">Değer</span><span class="sxs-lookup"><span data-stu-id="70dce-119">Value</span></span>|<span data-ttu-id="70dce-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="70dce-120">Description</span></span>|  
|-----------|-----------------|  
|`Default`|<span data-ttu-id="70dce-121">Kaynak yeni ise, içerik uzunluğu doğru, süre sonu, değişiklik ve içerik uzunluğu öznitelikleri varsa önbelleğe alınmış kaynağı döndürür.</span><span class="sxs-lookup"><span data-stu-id="70dce-121">Returns the cached resource if the resource is fresh, the content length is accurate, and the expiration, modification, and content length attributes are present.</span></span>|  
|`BypassCache`|<span data-ttu-id="70dce-122">Sunucudan kaynağı döndürür.</span><span class="sxs-lookup"><span data-stu-id="70dce-122">Returns the resource from the server.</span></span>|  
|`CacheOnly`|<span data-ttu-id="70dce-123">İçerik uzunluğu varsa ve giriş boyutuyla eşleşiyorsa, önbelleğe alınmış kaynağı döndürür.</span><span class="sxs-lookup"><span data-stu-id="70dce-123">Returns the cached resource if the content length is present and matches the entry size.</span></span>|  
|`CacheIfAvailable`|<span data-ttu-id="70dce-124">İçerik uzunluğu sağlanmışsa ve giriş boyutuyla eşleşiyorsa, önbelleğe alınmış kaynağı döndürür; Aksi takdirde, kaynak sunucudan indirilir ve çağırana döndürülür.</span><span class="sxs-lookup"><span data-stu-id="70dce-124">Returns the cached resource if the content length is provided and matches the entry size; otherwise, the resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="70dce-125">Önbelleğe alınan kaynağın zaman damgası sunucudaki kaynağın zaman damgasıyla aynıysa, önbelleğe alınmış kaynağı döndürür; Aksi takdirde, kaynak sunucudan yüklenir, önbellekte depolanır ve çağırana döndürülür.</span><span class="sxs-lookup"><span data-stu-id="70dce-125">Returns the cached resource if the timestamp of the cached resource is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, stored in the cache, and is returned to the caller.</span></span>|  
|`Reload`|<span data-ttu-id="70dce-126">Kaynağı sunucudan indirir, önbellekte depolar ve kaynak arayana döndürür.</span><span class="sxs-lookup"><span data-stu-id="70dce-126">Downloads the resource from the server, stores it in the cache, and returns the resource to the caller.</span></span>|  
|`NoCacheNoStore`|<span data-ttu-id="70dce-127">Önbelleğe alınmış bir kaynak varsa, silinir.</span><span class="sxs-lookup"><span data-stu-id="70dce-127">If a cached resource exists, it is deleted.</span></span> <span data-ttu-id="70dce-128">Kaynak sunucudan indirilir ve çağırana döndürülür.</span><span class="sxs-lookup"><span data-stu-id="70dce-128">The resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="70dce-129">Zaman damgası sunucudaki kaynağın zaman damgasıyla aynıysa, kaynağın önbelleğe alınmış kopyasını kullanarak bir isteği karşılar; Aksi takdirde, kaynak, çağırana sunulan sunucudan indirilir ve önbellekte depolanır.</span><span class="sxs-lookup"><span data-stu-id="70dce-129">Satisfies a request by using the cached copy of the resource if the timestamp is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, presented to the caller, and is stored in the cache,</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="70dce-130">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="70dce-130">Child Elements</span></span>  
  
|<span data-ttu-id="70dce-131">Öğe</span><span class="sxs-lookup"><span data-stu-id="70dce-131">Element</span></span>|<span data-ttu-id="70dce-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="70dce-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="70dce-133">defaultHttpCachePolicy</span><span class="sxs-lookup"><span data-stu-id="70dce-133">defaultHttpCachePolicy</span></span>](defaulthttpcachepolicy-element-network-settings.md)|<span data-ttu-id="70dce-134">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="70dce-134">Optional element.</span></span><br /><br /> <span data-ttu-id="70dce-135">HTTP önbelleğe almanın etkin olup olmadığını ve varsayılan önbelleğe alma ilkesini açıklar.</span><span class="sxs-lookup"><span data-stu-id="70dce-135">Describes whether HTTP caching is active and describes the default caching policy.</span></span>|  
|[<span data-ttu-id="70dce-136">\<defaultFtpCachePolicy> Öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="70dce-136">\<defaultFtpCachePolicy> Element (Network Settings)</span></span>](defaultftpcachepolicy-element-network-settings.md)|<span data-ttu-id="70dce-137">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="70dce-137">Optional element.</span></span><br /><br /> <span data-ttu-id="70dce-138">FTP önbelleğe almanın etkin olup olmadığını ve varsayılan önbelleğe alma ilkesini açıklar.</span><span class="sxs-lookup"><span data-stu-id="70dce-138">Describes whether FTP caching is active and describes the default caching policy.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="70dce-139">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="70dce-139">Parent Elements</span></span>  
  
|<span data-ttu-id="70dce-140">Öğe</span><span class="sxs-lookup"><span data-stu-id="70dce-140">Element</span></span>|<span data-ttu-id="70dce-141">Açıklama</span><span class="sxs-lookup"><span data-stu-id="70dce-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="70dce-142">system.net</span><span class="sxs-lookup"><span data-stu-id="70dce-142">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="70dce-143">.NET Framework ağa nasıl bağlanacağını belirten ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="70dce-143">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="70dce-144">Örnek</span><span class="sxs-lookup"><span data-stu-id="70dce-144">Example</span></span>  

 <span data-ttu-id="70dce-145">Aşağıdaki örnek, tüm önbelleğe almanın nasıl devre dışı bırakılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="70dce-145">The following example shows how to disable all caching.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <requestCaching  
      disableAllCaching="true"  
    />  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="70dce-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="70dce-146">See also</span></span>

- <xref:System.Net.Cache?displayProperty=nameWithType>
- [<span data-ttu-id="70dce-147">Ağ ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="70dce-147">Network Settings Schema</span></span>](index.md)
