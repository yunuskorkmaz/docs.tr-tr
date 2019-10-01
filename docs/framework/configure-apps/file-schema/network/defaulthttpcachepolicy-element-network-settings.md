---
title: <defaultHttpCachePolicy> Öğesi (Ağ Ayarları)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching/defaultHttpCachePolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultHttpCachePolicy
helpviewer_keywords:
- defaultHttpCachePolicy element
- <defaultHttpCachePolicy> element
ms.assetid: 2c1247d0-39b0-4c12-919a-a925ce075c79
ms.openlocfilehash: f3b029e8b931e976bee85c98dd926e020c5b8743
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698274"
---
# <a name="defaulthttpcachepolicy-element-network-settings"></a><span data-ttu-id="15a35-102">\<defaultHttpCachePolicy > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="15a35-102">\<defaultHttpCachePolicy> Element (Network Settings)</span></span>
<span data-ttu-id="15a35-103">HTTP önbelleğe almanın etkin olup olmadığını ve varsayılan önbelleğe alma ilkesini açıklar.</span><span class="sxs-lookup"><span data-stu-id="15a35-103">Describes whether HTTP caching is active and describes the default caching policy.</span></span>  
  
[<span data-ttu-id="15a35-104"> **\<Yapılandırma >** </span><span class="sxs-lookup"><span data-stu-id="15a35-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="15a35-105">&nbsp; @ no__t-1[ **@no__t -4system. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="15a35-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="15a35-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<requestCaching >** ](requestcaching-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="15a35-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<requestCaching>**](requestcaching-element-network-settings.md)</span></span>  
<span data-ttu-id="15a35-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 **\<defaultHttpCachePolicy >**</span><span class="sxs-lookup"><span data-stu-id="15a35-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<defaultHttpCachePolicy>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15a35-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="15a35-108">Syntax</span></span>  
  
```xml  
<defaultHttpCachePolicy  
  policyLevel="BypassCache|Default"  
  minimumFresh="d.hh:mm:ss|minValue|maxValue"  
  maximumAge="d.hh:mm:ss|minValue|maxValue"  
  maximumStale="d.hh:mm:ss|minValue|maxValue"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="15a35-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="15a35-109">Attributes and Elements</span></span>  
 <span data-ttu-id="15a35-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="15a35-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="15a35-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="15a35-111">Attributes</span></span>  
  
|<span data-ttu-id="15a35-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="15a35-112">Attribute</span></span>|<span data-ttu-id="15a35-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="15a35-113">Description</span></span>|  
|---------------|-----------------|  
|`maximumAge`|<span data-ttu-id="15a35-114">Önbelleğe alınan bir nesnenin süresi dolmadan önce geçen maksimum zaman aralığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="15a35-114">Specifies the maximum time interval before a cached object is marked as expired.</span></span>|  
|`maximumStale`|<span data-ttu-id="15a35-115">Önbelleğe alınmış bir nesne, süresi dolmadan önce, hesaplanan yeniliği geçen en uzun süreyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="15a35-115">Specifies the maximum time past the computed freshness time before a cached object is marked as expired.</span></span>|  
|`minimumFresh`|<span data-ttu-id="15a35-116">Önbelleğe alınmış bir nesnenin yeni olarak kabul edileceği en kısa süreyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="15a35-116">Specifies the minimum time for a cached object to be considered fresh.</span></span>|  
|`policyLevel`|<span data-ttu-id="15a35-117">Önbelleğe alma ilkesinin otomatik olup olmadığını veya önbelleğin atlanıp atlanmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="15a35-117">Specifies whether the caching policy is automatic, or whether the cache is bypassed.</span></span> <span data-ttu-id="15a35-118">Varsayılan değer `BypassCache` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="15a35-118">The default value is `BypassCache`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="15a35-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="15a35-119">Child Elements</span></span>  
 <span data-ttu-id="15a35-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="15a35-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="15a35-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="15a35-121">Parent Elements</span></span>  
  
|<span data-ttu-id="15a35-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="15a35-122">Element</span></span>|<span data-ttu-id="15a35-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="15a35-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="15a35-124">requestCaching</span><span class="sxs-lookup"><span data-stu-id="15a35-124">requestCaching</span></span>](requestcaching-element-network-settings.md)|<span data-ttu-id="15a35-125">Ağ istekleri için önbelleğe alma mekanizmasını denetler.</span><span class="sxs-lookup"><span data-stu-id="15a35-125">Controls the caching mechanism for network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="15a35-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="15a35-126">Remarks</span></span>  
 <span data-ttu-id="15a35-127">@No__t-0 özniteliğinin değeri `BypassCache` ya da `Default` ' dir.</span><span class="sxs-lookup"><span data-stu-id="15a35-127">The value for the `policyLevel` attribute is either `BypassCache` or `Default`.</span></span>  
  
 <span data-ttu-id="15a35-128">@No__t-0, `maximumStale` ve `minimumFresh` öğelerinin değerleri, *d*biçimindeki açık bir zaman aralığıdır. *SS*:*dd*:*SS* (gün, saat, dakika, saniye) veya `minValue` veya `maxValue` sabitleri uygun şekilde.</span><span class="sxs-lookup"><span data-stu-id="15a35-128">Values for the `maximumAge`, `maximumStale`, and `minimumFresh` elements are either an explicit time interval with a format of *d*.*hh*:*mm*:*ss* (days, hours, minutes, and seconds), or the constants `minValue` or `maxValue`, as appropriate.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="15a35-129">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="15a35-129">Configuration Files</span></span>  
 <span data-ttu-id="15a35-130">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine. config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="15a35-130">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="15a35-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="15a35-131">Example</span></span>  
 <span data-ttu-id="15a35-132">Aşağıdaki örnek, en az altı saat, iki güne ait maksimum yaş süresi ve dört saatlik en fazla eski süreyi belirtmek için nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="15a35-132">The following example shows how to specify a minimum fresh time of six hours, a maximum age time of two days, and a maximum stale time of four hours.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <requestCaching>  
      <defaultHttpCachePolicy  
        minimumFresh="0.06:00:00"  
        maximumAge="2.00:00:00"  
        maximumStale="0.04:00:00"
      />  
    </requestCaching>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="15a35-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="15a35-133">See also</span></span>

- <xref:System.Net.Cache>
- <xref:System.Net.WebRequest>
- <xref:System.Net.Cache.RequestCacheLevel>
- [<span data-ttu-id="15a35-134">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="15a35-134">Network Settings Schema</span></span>](index.md)
