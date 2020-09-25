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
ms.openlocfilehash: 3eb32b7ae643efdb19892410b669c1e7ff80e0ad
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91174166"
---
# <a name="requestcaching-element-network-settings"></a><span data-ttu-id="89bf7-102">\<requestCaching> Öğesi (Ağ Ayarları)</span><span class="sxs-lookup"><span data-stu-id="89bf7-102">\<requestCaching> Element (Network Settings)</span></span>

<span data-ttu-id="89bf7-103">Ağ istekleri için önbelleğe alma mekanizmasını denetler.</span><span class="sxs-lookup"><span data-stu-id="89bf7-103">Controls the caching mechanism for network requests.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<requestCaching>**  
  
## <a name="syntax"></a><span data-ttu-id="89bf7-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="89bf7-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="89bf7-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="89bf7-105">Attributes and Elements</span></span>  

 <span data-ttu-id="89bf7-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="89bf7-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="89bf7-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="89bf7-107">Attributes</span></span>  
  
|<span data-ttu-id="89bf7-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="89bf7-108">Attribute</span></span>|<span data-ttu-id="89bf7-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="89bf7-109">Description</span></span>|  
|---------------|-----------------|  
|`isPrivateCache`|<span data-ttu-id="89bf7-110">Önbelleğin, farklı kullanıcıların bilgileri arasında yalıtım verip içermediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="89bf7-110">Specifies whether the cache provides isolation between the information of different users.</span></span> <span data-ttu-id="89bf7-111">Varsayılan değer: `true`.</span><span class="sxs-lookup"><span data-stu-id="89bf7-111">The default value is `true`.</span></span> <span data-ttu-id="89bf7-112">Bu değer, `false` Orta katman uygulamalar için olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="89bf7-112">This value should be `false` for middle tier applications.</span></span>|  
|`disableAllCaching`|<span data-ttu-id="89bf7-113">Tüm Web yanıtları için önbelleğe almanın devre dışı bırakıldığını belirtir ve program aracılığıyla geçersiz kılınamaz.</span><span class="sxs-lookup"><span data-stu-id="89bf7-113">Specifies that caching is disabled for all Web responses, and cannot be overridden programmatically.</span></span>|  
|`defaultPolicyLevel`|<span data-ttu-id="89bf7-114"><xref:System.Net.Cache.RequestCacheLevel>Numaralandırmadaki değerlerden biri.</span><span class="sxs-lookup"><span data-stu-id="89bf7-114">One of the values in the <xref:System.Net.Cache.RequestCacheLevel> enumeration.</span></span> <span data-ttu-id="89bf7-115">Varsayılan değer: `BypassCache`.</span><span class="sxs-lookup"><span data-stu-id="89bf7-115">The default value is `BypassCache`.</span></span>|  
|`unspecifiedMaximumAge`|<span data-ttu-id="89bf7-116">İçeriğin süresi dolduğunda, varsayılan süreyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="89bf7-116">Specifies the default time after which content is marked as expired.</span></span>|  
  
## <a name="policylevel-attribute"></a><span data-ttu-id="89bf7-117">policyLevel özniteliği</span><span class="sxs-lookup"><span data-stu-id="89bf7-117">policyLevel Attribute</span></span>  
  
|<span data-ttu-id="89bf7-118">Değer</span><span class="sxs-lookup"><span data-stu-id="89bf7-118">Value</span></span>|<span data-ttu-id="89bf7-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="89bf7-119">Description</span></span>|  
|-----------|-----------------|  
|`Default`|<span data-ttu-id="89bf7-120">Kaynak yeni ise, içerik uzunluğu doğru, süre sonu, değişiklik ve içerik uzunluğu öznitelikleri varsa önbelleğe alınmış kaynağı döndürür.</span><span class="sxs-lookup"><span data-stu-id="89bf7-120">Returns the cached resource if the resource is fresh, the content length is accurate, and the expiration, modification, and content length attributes are present.</span></span>|  
|`BypassCache`|<span data-ttu-id="89bf7-121">Sunucudan kaynağı döndürür.</span><span class="sxs-lookup"><span data-stu-id="89bf7-121">Returns the resource from the server.</span></span>|  
|`CacheOnly`|<span data-ttu-id="89bf7-122">İçerik uzunluğu varsa ve giriş boyutuyla eşleşiyorsa, önbelleğe alınmış kaynağı döndürür.</span><span class="sxs-lookup"><span data-stu-id="89bf7-122">Returns the cached resource if the content length is present and matches the entry size.</span></span>|  
|`CacheIfAvailable`|<span data-ttu-id="89bf7-123">İçerik uzunluğu sağlanmışsa ve giriş boyutuyla eşleşiyorsa, önbelleğe alınmış kaynağı döndürür; Aksi takdirde, kaynak sunucudan indirilir ve çağırana döndürülür.</span><span class="sxs-lookup"><span data-stu-id="89bf7-123">Returns the cached resource if the content length is provided and matches the entry size; otherwise, the resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="89bf7-124">Önbelleğe alınan kaynağın zaman damgası sunucudaki kaynağın zaman damgasıyla aynıysa, önbelleğe alınmış kaynağı döndürür; Aksi takdirde, kaynak sunucudan yüklenir, önbellekte depolanır ve çağırana döndürülür.</span><span class="sxs-lookup"><span data-stu-id="89bf7-124">Returns the cached resource if the timestamp of the cached resource is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, stored in the cache, and is returned to the caller.</span></span>|  
|`Reload`|<span data-ttu-id="89bf7-125">Kaynağı sunucudan indirir, önbellekte depolar ve kaynak arayana döndürür.</span><span class="sxs-lookup"><span data-stu-id="89bf7-125">Downloads the resource from the server, stores it in the cache, and returns the resource to the caller.</span></span>|  
|`NoCacheNoStore`|<span data-ttu-id="89bf7-126">Önbelleğe alınmış bir kaynak varsa, silinir.</span><span class="sxs-lookup"><span data-stu-id="89bf7-126">If a cached resource exists, it is deleted.</span></span> <span data-ttu-id="89bf7-127">Kaynak sunucudan indirilir ve çağırana döndürülür.</span><span class="sxs-lookup"><span data-stu-id="89bf7-127">The resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="89bf7-128">Zaman damgası sunucudaki kaynağın zaman damgasıyla aynıysa, kaynağın önbelleğe alınmış kopyasını kullanarak bir isteği karşılar; Aksi takdirde, kaynak, çağırana sunulan sunucudan indirilir ve önbellekte depolanır.</span><span class="sxs-lookup"><span data-stu-id="89bf7-128">Satisfies a request by using the cached copy of the resource if the timestamp is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, presented to the caller, and is stored in the cache,</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="89bf7-129">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="89bf7-129">Child Elements</span></span>  
  
|<span data-ttu-id="89bf7-130">Öğe</span><span class="sxs-lookup"><span data-stu-id="89bf7-130">Element</span></span>|<span data-ttu-id="89bf7-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="89bf7-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="89bf7-132">defaultHttpCachePolicy</span><span class="sxs-lookup"><span data-stu-id="89bf7-132">defaultHttpCachePolicy</span></span>](defaulthttpcachepolicy-element-network-settings.md)|<span data-ttu-id="89bf7-133">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="89bf7-133">Optional element.</span></span><br /><br /> <span data-ttu-id="89bf7-134">HTTP önbelleğe almanın etkin olup olmadığını ve varsayılan önbelleğe alma ilkesini açıklar.</span><span class="sxs-lookup"><span data-stu-id="89bf7-134">Describes whether HTTP caching is active and describes the default caching policy.</span></span>|  
|[<span data-ttu-id="89bf7-135">\<defaultFtpCachePolicy> Öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="89bf7-135">\<defaultFtpCachePolicy> Element (Network Settings)</span></span>](defaultftpcachepolicy-element-network-settings.md)|<span data-ttu-id="89bf7-136">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="89bf7-136">Optional element.</span></span><br /><br /> <span data-ttu-id="89bf7-137">FTP önbelleğe almanın etkin olup olmadığını ve varsayılan önbelleğe alma ilkesini açıklar.</span><span class="sxs-lookup"><span data-stu-id="89bf7-137">Describes whether FTP caching is active and describes the default caching policy.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="89bf7-138">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="89bf7-138">Parent Elements</span></span>  
  
|<span data-ttu-id="89bf7-139">Öğe</span><span class="sxs-lookup"><span data-stu-id="89bf7-139">Element</span></span>|<span data-ttu-id="89bf7-140">Açıklama</span><span class="sxs-lookup"><span data-stu-id="89bf7-140">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="89bf7-141">system.net</span><span class="sxs-lookup"><span data-stu-id="89bf7-141">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="89bf7-142">.NET Framework ağa nasıl bağlanacağını belirten ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="89bf7-142">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="89bf7-143">Örnek</span><span class="sxs-lookup"><span data-stu-id="89bf7-143">Example</span></span>  

 <span data-ttu-id="89bf7-144">Aşağıdaki örnek, tüm önbelleğe almanın nasıl devre dışı bırakılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="89bf7-144">The following example shows how to disable all caching.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <requestCaching  
      disableAllCaching="true"  
    />  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="89bf7-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="89bf7-145">See also</span></span>

- <xref:System.Net.Cache?displayProperty=nameWithType>
- [<span data-ttu-id="89bf7-146">Ağ ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="89bf7-146">Network Settings Schema</span></span>](index.md)
