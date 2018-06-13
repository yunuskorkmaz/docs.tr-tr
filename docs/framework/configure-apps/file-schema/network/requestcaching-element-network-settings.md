---
title: '&lt;requestCaching&gt; öğesi (ağ ayarları)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#requestCaching
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching
helpviewer_keywords:
- requestCaching element
- <requestCaching> element
ms.assetid: 9962a2fe-cbda-41a6-9377-571811eaea84
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 9c0c8d80182931f9ac14e687a337b7be55a5a9a5
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32743439"
---
# <a name="ltrequestcachinggt-element-network-settings"></a><span data-ttu-id="0adbd-102">&lt;requestCaching&gt; öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="0adbd-102">&lt;requestCaching&gt; Element (Network Settings)</span></span>
<span data-ttu-id="0adbd-103">Ağ isteği önbelleğe alma mekanizması denetler.</span><span class="sxs-lookup"><span data-stu-id="0adbd-103">Controls the caching mechanism for network requests.</span></span>  
  
 <span data-ttu-id="0adbd-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="0adbd-104">\<configuration></span></span>  
<span data-ttu-id="0adbd-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="0adbd-105">\<system.net></span></span>  
<span data-ttu-id="0adbd-106">\<requestCaching ></span><span class="sxs-lookup"><span data-stu-id="0adbd-106">\<requestCaching></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0adbd-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0adbd-107">Syntax</span></span>  
  
```xml  
      <requestCaching>  
        isPrivateCache ="true|false"  
        disableAllCaching="true|false"  
        defaultPolicyLevel="BypassCache|Default|CacheOnly|CacheIfAvailable|Revalidate|Reload|NoCacheNoStore|Revalidate"  
        unspecifiedMaximumAge= "d.hh.mm.ss">  
          <defaultHttpCachePolicy> … </defaultHttpCachePolicy>  
          <defaultFtpCachePolicy> … </defaultFtpCachePolicy>  
      </requestCaching>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0adbd-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="0adbd-108">Attributes and Elements</span></span>  
 <span data-ttu-id="0adbd-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0adbd-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0adbd-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0adbd-110">Attributes</span></span>  
  
|<span data-ttu-id="0adbd-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="0adbd-111">Attribute</span></span>|<span data-ttu-id="0adbd-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0adbd-112">Description</span></span>|  
|---------------|-----------------|  
|`isPrivateCache`|<span data-ttu-id="0adbd-113">Önbellek bilgilerin farklı kullanıcılar arasında yalıtım sağlayıp sağlamayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="0adbd-113">Specifies whether the cache provides isolation between the information of different users.</span></span> <span data-ttu-id="0adbd-114">Varsayılan değer `true` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="0adbd-114">The default value is `true`.</span></span> <span data-ttu-id="0adbd-115">Bu değer olmalıdır `false` orta katman uygulamalar için.</span><span class="sxs-lookup"><span data-stu-id="0adbd-115">This value should be `false` for middle tier applications.</span></span>|  
|`disableAllCaching`|<span data-ttu-id="0adbd-116">Önbelleğe alma için tüm Web yanıtlarını devre dışı ve program aracılığıyla geçersiz kılınamaz belirtir.</span><span class="sxs-lookup"><span data-stu-id="0adbd-116">Specifies that caching is disabled for all Web responses, and cannot be overridden programmatically.</span></span>|  
|`defaultPolicyLevel`|<span data-ttu-id="0adbd-117">Değerlerden biri <xref:System.Net.Cache.RequestCacheLevel> numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="0adbd-117">One of the values in the <xref:System.Net.Cache.RequestCacheLevel> enumeration.</span></span> <span data-ttu-id="0adbd-118">Varsayılan değer `BypassCache` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="0adbd-118">The default value is `BypassCache`.</span></span>|  
|`unspecifiedMaximumAge`|<span data-ttu-id="0adbd-119">Daha sonra içeriğin süresi dolmuş olarak işaretlenmiş varsayılan süreyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="0adbd-119">Specifies the default time after which content is marked as expired.</span></span>|  
  
## <a name="policylevel-attribute"></a><span data-ttu-id="0adbd-120">policyLevel özniteliği</span><span class="sxs-lookup"><span data-stu-id="0adbd-120">policyLevel Attribute</span></span>  
  
|<span data-ttu-id="0adbd-121">Değer</span><span class="sxs-lookup"><span data-stu-id="0adbd-121">Value</span></span>|<span data-ttu-id="0adbd-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0adbd-122">Description</span></span>|  
|-----------|-----------------|  
|`Default`|<span data-ttu-id="0adbd-123">Önbelleğe alınan kaynak yeni bir kaynaktır, içerik uzunluğu doğru olduğundan ve süre sonu, değiştirilmesi ve içerik uzunluğu öznitelikleri mevcut döndürür.</span><span class="sxs-lookup"><span data-stu-id="0adbd-123">Returns the cached resource if the resource is fresh, the content length is accurate, and the expiration, modification, and content length attributes are present.</span></span>|  
|`BypassCache`|<span data-ttu-id="0adbd-124">Kaynak sunucudan döndürür.</span><span class="sxs-lookup"><span data-stu-id="0adbd-124">Returns the resource from the server.</span></span>|  
|`CacheOnly`|<span data-ttu-id="0adbd-125">İçerik uzunluğu varsa ve giriş boyutu eşleşen önbelleğe alınan kaynak döndürür.</span><span class="sxs-lookup"><span data-stu-id="0adbd-125">Returns the cached resource if the content length is present and matches the entry size.</span></span>|  
|`CacheIfAvailable`|<span data-ttu-id="0adbd-126">İçerik uzunluğu sağlanır ve giriş boyutu eşleşiyorsa önbelleğe alınan kaynak döndürür; Aksi halde, kaynak sunucudan indirilir ve çağırana döndürülür.</span><span class="sxs-lookup"><span data-stu-id="0adbd-126">Returns the cached resource if the content length is provided and matches the entry size; otherwise, the resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="0adbd-127">Önbelleğe alınan kaynak damgası kaynak sunucuda damgası ile aynı olduğunda önbelleğe alınan kaynak döndürür; Aksi halde, kaynak sunucusundan önbellekte depolanan yüklenen ve çağırana döndürülür.</span><span class="sxs-lookup"><span data-stu-id="0adbd-127">Returns the cached resource if the timestamp of the cached resource is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, stored in the cache, and is returned to the caller.</span></span>|  
|`Reload`|<span data-ttu-id="0adbd-128">Kaynak sunucudan indirir, önbellekte depolar ve kaynak çağırana döndürür.</span><span class="sxs-lookup"><span data-stu-id="0adbd-128">Downloads the resource from the server, stores it in the cache, and returns the resource to the caller.</span></span>|  
|`NoCacheNoStore`|<span data-ttu-id="0adbd-129">Önbelleğe alınan bir kaynak zaten varsa, bu silinir.</span><span class="sxs-lookup"><span data-stu-id="0adbd-129">If a cached resource exists, it is deleted.</span></span> <span data-ttu-id="0adbd-130">Kaynak sunucudan indirilir ve çağırana döndürülür.</span><span class="sxs-lookup"><span data-stu-id="0adbd-130">The resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="0adbd-131">Bir istek zaman damgası kaynak sunucuda damgası ile aynı olduğunda, kaynak önbelleğe alınmış bir kopyasını kullanarak karşılayan; Aksi halde, kaynak sunucudan çağırana sunulan indirilir ve önbellekte depolanır,</span><span class="sxs-lookup"><span data-stu-id="0adbd-131">Satisfies a request by using the cached copy of the resource if the timestamp is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, presented to the caller, and is stored in the cache,</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0adbd-132">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="0adbd-132">Child Elements</span></span>  
  
|<span data-ttu-id="0adbd-133">Öğe</span><span class="sxs-lookup"><span data-stu-id="0adbd-133">Element</span></span>|<span data-ttu-id="0adbd-134">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0adbd-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0adbd-135">defaultHttpCachePolicy</span><span class="sxs-lookup"><span data-stu-id="0adbd-135">defaultHttpCachePolicy</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/defaulthttpcachepolicy-element-network-settings.md)|<span data-ttu-id="0adbd-136">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="0adbd-136">Optional element.</span></span><br /><br /> <span data-ttu-id="0adbd-137">HTTP önbelleğe alma etkindir ve ilke önbelleğe almayı varsayılan açıklar olup olmadığını açıklar.</span><span class="sxs-lookup"><span data-stu-id="0adbd-137">Describes whether HTTP caching is active and describes the default caching policy.</span></span>|  
|[<span data-ttu-id="0adbd-138">\<defaultFtpCachePolicy > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="0adbd-138">\<defaultFtpCachePolicy> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/defaultftpcachepolicy-element-network-settings.md)|<span data-ttu-id="0adbd-139">İsteğe bağlı öğe.</span><span class="sxs-lookup"><span data-stu-id="0adbd-139">Optional element.</span></span><br /><br /> <span data-ttu-id="0adbd-140">FTP önbelleğe alma etkindir ve ilke önbelleğe almayı varsayılan açıklar olup olmadığını açıklar.</span><span class="sxs-lookup"><span data-stu-id="0adbd-140">Describes whether FTP caching is active and describes the default caching policy.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0adbd-141">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="0adbd-141">Parent Elements</span></span>  
  
|<span data-ttu-id="0adbd-142">Öğe</span><span class="sxs-lookup"><span data-stu-id="0adbd-142">Element</span></span>|<span data-ttu-id="0adbd-143">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0adbd-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0adbd-144">System.NET</span><span class="sxs-lookup"><span data-stu-id="0adbd-144">system.net</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|<span data-ttu-id="0adbd-145">.NET Framework ağa nasıl bağlanacağını belirtin ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="0adbd-145">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="0adbd-146">Örnek</span><span class="sxs-lookup"><span data-stu-id="0adbd-146">Example</span></span>  
 <span data-ttu-id="0adbd-147">Aşağıdaki örnek, tüm önbelleğe alma devre dışı bırakmak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="0adbd-147">The following example shows how to disable all caching.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <requestCaching  
      disableAllCaching="true"  
    />  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0adbd-148">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0adbd-148">See Also</span></span>  
 <xref:System.Net.Cache?displayProperty=nameWithType>  
 [<span data-ttu-id="0adbd-149">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="0adbd-149">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
