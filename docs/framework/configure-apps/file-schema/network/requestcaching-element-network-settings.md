---
title: <requestCaching> Öğesi (Ağ Ayarları)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#requestCaching
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching
helpviewer_keywords:
- requestCaching element
- <requestCaching> element
ms.assetid: 9962a2fe-cbda-41a6-9377-571811eaea84
ms.openlocfilehash: afee69eb894518b1c88483e34a1d64d452019244
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802134"
---
# <a name="requestcaching-element-network-settings"></a><span data-ttu-id="dd42e-102">\<requestCaching > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="dd42e-102">\<requestCaching> Element (Network Settings)</span></span>
<span data-ttu-id="dd42e-103">Ağ istekleri için önbelleğe alma mekanizmasını denetler.</span><span class="sxs-lookup"><span data-stu-id="dd42e-103">Controls the caching mechanism for network requests.</span></span>  
  
[<span data-ttu-id="dd42e-104"> **\<Yapılandırma >** </span><span class="sxs-lookup"><span data-stu-id="dd42e-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="dd42e-105">[ **System. net >\<** &nbsp;&nbsp;](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="dd42e-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="dd42e-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<requestCaching >**</span><span class="sxs-lookup"><span data-stu-id="dd42e-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<requestCaching>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd42e-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dd42e-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dd42e-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="dd42e-108">Attributes and Elements</span></span>  
 <span data-ttu-id="dd42e-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="dd42e-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dd42e-110">{1&gt;{2&gt;Öznitelikler&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="dd42e-110">Attributes</span></span>  
  
|<span data-ttu-id="dd42e-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="dd42e-111">Attribute</span></span>|<span data-ttu-id="dd42e-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dd42e-112">Description</span></span>|  
|---------------|-----------------|  
|`isPrivateCache`|<span data-ttu-id="dd42e-113">Önbelleğin, farklı kullanıcıların bilgileri arasında yalıtım verip içermediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="dd42e-113">Specifies whether the cache provides isolation between the information of different users.</span></span> <span data-ttu-id="dd42e-114">Varsayılan değer `true` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="dd42e-114">The default value is `true`.</span></span> <span data-ttu-id="dd42e-115">Bu değer, orta katman uygulamalar için `false` olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="dd42e-115">This value should be `false` for middle tier applications.</span></span>|  
|`disableAllCaching`|<span data-ttu-id="dd42e-116">Tüm Web yanıtları için önbelleğe almanın devre dışı bırakıldığını belirtir ve program aracılığıyla geçersiz kılınamaz.</span><span class="sxs-lookup"><span data-stu-id="dd42e-116">Specifies that caching is disabled for all Web responses, and cannot be overridden programmatically.</span></span>|  
|`defaultPolicyLevel`|<span data-ttu-id="dd42e-117"><xref:System.Net.Cache.RequestCacheLevel> Numaralandırmadaki değerlerden biri.</span><span class="sxs-lookup"><span data-stu-id="dd42e-117">One of the values in the <xref:System.Net.Cache.RequestCacheLevel> enumeration.</span></span> <span data-ttu-id="dd42e-118">Varsayılan değer `BypassCache` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="dd42e-118">The default value is `BypassCache`.</span></span>|  
|`unspecifiedMaximumAge`|<span data-ttu-id="dd42e-119">İçeriğin süresi dolduğunda, varsayılan süreyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="dd42e-119">Specifies the default time after which content is marked as expired.</span></span>|  
  
## <a name="policylevel-attribute"></a><span data-ttu-id="dd42e-120">policyLevel özniteliği</span><span class="sxs-lookup"><span data-stu-id="dd42e-120">policyLevel Attribute</span></span>  
  
|<span data-ttu-id="dd42e-121">Değer</span><span class="sxs-lookup"><span data-stu-id="dd42e-121">Value</span></span>|<span data-ttu-id="dd42e-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dd42e-122">Description</span></span>|  
|-----------|-----------------|  
|`Default`|<span data-ttu-id="dd42e-123">Kaynak yeni ise, içerik uzunluğu doğru, süre sonu, değişiklik ve içerik uzunluğu öznitelikleri varsa önbelleğe alınmış kaynağı döndürür.</span><span class="sxs-lookup"><span data-stu-id="dd42e-123">Returns the cached resource if the resource is fresh, the content length is accurate, and the expiration, modification, and content length attributes are present.</span></span>|  
|`BypassCache`|<span data-ttu-id="dd42e-124">Sunucudan kaynağı döndürür.</span><span class="sxs-lookup"><span data-stu-id="dd42e-124">Returns the resource from the server.</span></span>|  
|`CacheOnly`|<span data-ttu-id="dd42e-125">İçerik uzunluğu varsa ve giriş boyutuyla eşleşiyorsa, önbelleğe alınmış kaynağı döndürür.</span><span class="sxs-lookup"><span data-stu-id="dd42e-125">Returns the cached resource if the content length is present and matches the entry size.</span></span>|  
|`CacheIfAvailable`|<span data-ttu-id="dd42e-126">İçerik uzunluğu sağlanmışsa ve giriş boyutuyla eşleşiyorsa, önbelleğe alınmış kaynağı döndürür; Aksi takdirde, kaynak sunucudan indirilir ve çağırana döndürülür.</span><span class="sxs-lookup"><span data-stu-id="dd42e-126">Returns the cached resource if the content length is provided and matches the entry size; otherwise, the resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="dd42e-127">Önbelleğe alınan kaynağın zaman damgası sunucudaki kaynağın zaman damgasıyla aynıysa, önbelleğe alınmış kaynağı döndürür; Aksi takdirde, kaynak sunucudan yüklenir, önbellekte depolanır ve çağırana döndürülür.</span><span class="sxs-lookup"><span data-stu-id="dd42e-127">Returns the cached resource if the timestamp of the cached resource is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, stored in the cache, and is returned to the caller.</span></span>|  
|`Reload`|<span data-ttu-id="dd42e-128">Kaynağı sunucudan indirir, önbellekte depolar ve kaynak arayana döndürür.</span><span class="sxs-lookup"><span data-stu-id="dd42e-128">Downloads the resource from the server, stores it in the cache, and returns the resource to the caller.</span></span>|  
|`NoCacheNoStore`|<span data-ttu-id="dd42e-129">Önbelleğe alınmış bir kaynak varsa, silinir.</span><span class="sxs-lookup"><span data-stu-id="dd42e-129">If a cached resource exists, it is deleted.</span></span> <span data-ttu-id="dd42e-130">Kaynak sunucudan indirilir ve çağırana döndürülür.</span><span class="sxs-lookup"><span data-stu-id="dd42e-130">The resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="dd42e-131">Zaman damgası sunucudaki kaynağın zaman damgasıyla aynıysa, kaynağın önbelleğe alınmış kopyasını kullanarak bir isteği karşılar; Aksi takdirde, kaynak, çağırana sunulan sunucudan indirilir ve önbellekte depolanır.</span><span class="sxs-lookup"><span data-stu-id="dd42e-131">Satisfies a request by using the cached copy of the resource if the timestamp is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, presented to the caller, and is stored in the cache,</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dd42e-132">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="dd42e-132">Child Elements</span></span>  
  
|<span data-ttu-id="dd42e-133">Öğe</span><span class="sxs-lookup"><span data-stu-id="dd42e-133">Element</span></span>|<span data-ttu-id="dd42e-134">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dd42e-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dd42e-135">defaultHttpCachePolicy</span><span class="sxs-lookup"><span data-stu-id="dd42e-135">defaultHttpCachePolicy</span></span>](defaulthttpcachepolicy-element-network-settings.md)|<span data-ttu-id="dd42e-136">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="dd42e-136">Optional element.</span></span><br /><br /> <span data-ttu-id="dd42e-137">HTTP önbelleğe almanın etkin olup olmadığını ve varsayılan önbelleğe alma ilkesini açıklar.</span><span class="sxs-lookup"><span data-stu-id="dd42e-137">Describes whether HTTP caching is active and describes the default caching policy.</span></span>|  
|[<span data-ttu-id="dd42e-138">\<defaultFtpCachePolicy > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="dd42e-138">\<defaultFtpCachePolicy> Element (Network Settings)</span></span>](defaultftpcachepolicy-element-network-settings.md)|<span data-ttu-id="dd42e-139">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="dd42e-139">Optional element.</span></span><br /><br /> <span data-ttu-id="dd42e-140">FTP önbelleğe almanın etkin olup olmadığını ve varsayılan önbelleğe alma ilkesini açıklar.</span><span class="sxs-lookup"><span data-stu-id="dd42e-140">Describes whether FTP caching is active and describes the default caching policy.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="dd42e-141">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="dd42e-141">Parent Elements</span></span>  
  
|<span data-ttu-id="dd42e-142">Öğe</span><span class="sxs-lookup"><span data-stu-id="dd42e-142">Element</span></span>|<span data-ttu-id="dd42e-143">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dd42e-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dd42e-144">system.net</span><span class="sxs-lookup"><span data-stu-id="dd42e-144">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="dd42e-145">.NET Framework ağa nasıl bağlanacağını belirten ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="dd42e-145">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="dd42e-146">Örnek</span><span class="sxs-lookup"><span data-stu-id="dd42e-146">Example</span></span>  
 <span data-ttu-id="dd42e-147">Aşağıdaki örnek, tüm önbelleğe almanın nasıl devre dışı bırakılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="dd42e-147">The following example shows how to disable all caching.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <requestCaching  
      disableAllCaching="true"  
    />  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="dd42e-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dd42e-148">See also</span></span>

- <xref:System.Net.Cache?displayProperty=nameWithType>
- [<span data-ttu-id="dd42e-149">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="dd42e-149">Network Settings Schema</span></span>](index.md)
