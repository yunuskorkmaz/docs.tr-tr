---
description: 'Daha fazla bilgi edinin: <defaultHttpCachePolicy> öğesi (ağ ayarları)'
title: <defaultHttpCachePolicy> Öğesi (Ağ Ayarları)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching/defaultHttpCachePolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultHttpCachePolicy
helpviewer_keywords:
- defaultHttpCachePolicy element
- <defaultHttpCachePolicy> element
ms.assetid: 2c1247d0-39b0-4c12-919a-a925ce075c79
ms.openlocfilehash: d2df27c9b140c9bdb4def49aef7de1a3d80f4a11
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99740333"
---
# <a name="defaulthttpcachepolicy-element-network-settings"></a><span data-ttu-id="335e8-103">\<defaultHttpCachePolicy> Öğesi (Ağ Ayarları)</span><span class="sxs-lookup"><span data-stu-id="335e8-103">\<defaultHttpCachePolicy> Element (Network Settings)</span></span>

<span data-ttu-id="335e8-104">HTTP önbelleğe almanın etkin olup olmadığını ve varsayılan önbelleğe alma ilkesini açıklar.</span><span class="sxs-lookup"><span data-stu-id="335e8-104">Describes whether HTTP caching is active and describes the default caching policy.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<requestCaching>**](requestcaching-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<defaultHttpCachePolicy>**

## <a name="syntax"></a><span data-ttu-id="335e8-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="335e8-105">Syntax</span></span>  
  
```xml  
<defaultHttpCachePolicy  
  policyLevel="BypassCache|Default"  
  minimumFresh="d.hh:mm:ss|minValue|maxValue"  
  maximumAge="d.hh:mm:ss|minValue|maxValue"  
  maximumStale="d.hh:mm:ss|minValue|maxValue"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="335e8-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="335e8-106">Attributes and Elements</span></span>  

 <span data-ttu-id="335e8-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="335e8-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="335e8-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="335e8-108">Attributes</span></span>  
  
|<span data-ttu-id="335e8-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="335e8-109">Attribute</span></span>|<span data-ttu-id="335e8-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="335e8-110">Description</span></span>|  
|---------------|-----------------|  
|`maximumAge`|<span data-ttu-id="335e8-111">Önbelleğe alınan bir nesnenin süresi dolmadan önce geçen maksimum zaman aralığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="335e8-111">Specifies the maximum time interval before a cached object is marked as expired.</span></span>|  
|`maximumStale`|<span data-ttu-id="335e8-112">Önbelleğe alınmış bir nesne, süresi dolmadan önce, hesaplanan yeniliği geçen en uzun süreyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="335e8-112">Specifies the maximum time past the computed freshness time before a cached object is marked as expired.</span></span>|  
|`minimumFresh`|<span data-ttu-id="335e8-113">Önbelleğe alınmış bir nesnenin yeni olarak kabul edileceği en kısa süreyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="335e8-113">Specifies the minimum time for a cached object to be considered fresh.</span></span>|  
|`policyLevel`|<span data-ttu-id="335e8-114">Önbelleğe alma ilkesinin otomatik olup olmadığını veya önbelleğin atlanıp atlanmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="335e8-114">Specifies whether the caching policy is automatic, or whether the cache is bypassed.</span></span> <span data-ttu-id="335e8-115">`BypassCache` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="335e8-115">The default value is `BypassCache`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="335e8-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="335e8-116">Child Elements</span></span>  

 <span data-ttu-id="335e8-117">Yok</span><span class="sxs-lookup"><span data-stu-id="335e8-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="335e8-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="335e8-118">Parent Elements</span></span>  
  
|<span data-ttu-id="335e8-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="335e8-119">Element</span></span>|<span data-ttu-id="335e8-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="335e8-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="335e8-121">requestCaching</span><span class="sxs-lookup"><span data-stu-id="335e8-121">requestCaching</span></span>](requestcaching-element-network-settings.md)|<span data-ttu-id="335e8-122">Ağ istekleri için önbelleğe alma mekanizmasını denetler.</span><span class="sxs-lookup"><span data-stu-id="335e8-122">Controls the caching mechanism for network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="335e8-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="335e8-123">Remarks</span></span>  

 <span data-ttu-id="335e8-124">Özniteliği için olan değer `policyLevel` ya da olur `BypassCache` `Default` .</span><span class="sxs-lookup"><span data-stu-id="335e8-124">The value for the `policyLevel` attribute is either `BypassCache` or `Default`.</span></span>  
  
 <span data-ttu-id="335e8-125">`maximumAge`, `maximumStale` , Ve `minimumFresh` öğelerinin değerleri *d* biçimindeki açık bir zaman aralığıdır.*SS*:*dd*:*SS* (gün, saat, dakika, saniye) veya sabitler `minValue` ya da `maxValue` uygun şekilde.</span><span class="sxs-lookup"><span data-stu-id="335e8-125">Values for the `maximumAge`, `maximumStale`, and `minimumFresh` elements are either an explicit time interval with a format of *d*.*hh*:*mm*:*ss* (days, hours, minutes, and seconds), or the constants `minValue` or `maxValue`, as appropriate.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="335e8-126">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="335e8-126">Configuration Files</span></span>  

 <span data-ttu-id="335e8-127">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="335e8-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="335e8-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="335e8-128">Example</span></span>  

 <span data-ttu-id="335e8-129">Aşağıdaki örnek, en az altı saat, iki güne ait maksimum yaş süresi ve dört saatlik en fazla eski süreyi belirtmek için nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="335e8-129">The following example shows how to specify a minimum fresh time of six hours, a maximum age time of two days, and a maximum stale time of four hours.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="335e8-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="335e8-130">See also</span></span>

- <xref:System.Net.Cache>
- <xref:System.Net.WebRequest>
- <xref:System.Net.Cache.RequestCacheLevel>
- [<span data-ttu-id="335e8-131">Ağ ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="335e8-131">Network Settings Schema</span></span>](index.md)
