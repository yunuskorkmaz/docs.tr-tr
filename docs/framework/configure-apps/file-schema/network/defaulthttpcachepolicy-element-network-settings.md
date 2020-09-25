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
ms.openlocfilehash: 4120c57fbb65da1c124414cbe9cfba7ae64388f8
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91190325"
---
# <a name="defaulthttpcachepolicy-element-network-settings"></a><span data-ttu-id="35d2f-102">\<defaultHttpCachePolicy> Öğesi (Ağ Ayarları)</span><span class="sxs-lookup"><span data-stu-id="35d2f-102">\<defaultHttpCachePolicy> Element (Network Settings)</span></span>

<span data-ttu-id="35d2f-103">HTTP önbelleğe almanın etkin olup olmadığını ve varsayılan önbelleğe alma ilkesini açıklar.</span><span class="sxs-lookup"><span data-stu-id="35d2f-103">Describes whether HTTP caching is active and describes the default caching policy.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<requestCaching>**](requestcaching-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<defaultHttpCachePolicy>**

## <a name="syntax"></a><span data-ttu-id="35d2f-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="35d2f-104">Syntax</span></span>  
  
```xml  
<defaultHttpCachePolicy  
  policyLevel="BypassCache|Default"  
  minimumFresh="d.hh:mm:ss|minValue|maxValue"  
  maximumAge="d.hh:mm:ss|minValue|maxValue"  
  maximumStale="d.hh:mm:ss|minValue|maxValue"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="35d2f-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="35d2f-105">Attributes and Elements</span></span>  

 <span data-ttu-id="35d2f-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="35d2f-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="35d2f-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="35d2f-107">Attributes</span></span>  
  
|<span data-ttu-id="35d2f-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="35d2f-108">Attribute</span></span>|<span data-ttu-id="35d2f-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="35d2f-109">Description</span></span>|  
|---------------|-----------------|  
|`maximumAge`|<span data-ttu-id="35d2f-110">Önbelleğe alınan bir nesnenin süresi dolmadan önce geçen maksimum zaman aralığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="35d2f-110">Specifies the maximum time interval before a cached object is marked as expired.</span></span>|  
|`maximumStale`|<span data-ttu-id="35d2f-111">Önbelleğe alınmış bir nesne, süresi dolmadan önce, hesaplanan yeniliği geçen en uzun süreyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="35d2f-111">Specifies the maximum time past the computed freshness time before a cached object is marked as expired.</span></span>|  
|`minimumFresh`|<span data-ttu-id="35d2f-112">Önbelleğe alınmış bir nesnenin yeni olarak kabul edileceği en kısa süreyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="35d2f-112">Specifies the minimum time for a cached object to be considered fresh.</span></span>|  
|`policyLevel`|<span data-ttu-id="35d2f-113">Önbelleğe alma ilkesinin otomatik olup olmadığını veya önbelleğin atlanıp atlanmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="35d2f-113">Specifies whether the caching policy is automatic, or whether the cache is bypassed.</span></span> <span data-ttu-id="35d2f-114">Varsayılan değer: `BypassCache`.</span><span class="sxs-lookup"><span data-stu-id="35d2f-114">The default value is `BypassCache`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="35d2f-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="35d2f-115">Child Elements</span></span>  

 <span data-ttu-id="35d2f-116">Yok</span><span class="sxs-lookup"><span data-stu-id="35d2f-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="35d2f-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="35d2f-117">Parent Elements</span></span>  
  
|<span data-ttu-id="35d2f-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="35d2f-118">Element</span></span>|<span data-ttu-id="35d2f-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="35d2f-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="35d2f-120">requestCaching</span><span class="sxs-lookup"><span data-stu-id="35d2f-120">requestCaching</span></span>](requestcaching-element-network-settings.md)|<span data-ttu-id="35d2f-121">Ağ istekleri için önbelleğe alma mekanizmasını denetler.</span><span class="sxs-lookup"><span data-stu-id="35d2f-121">Controls the caching mechanism for network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="35d2f-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="35d2f-122">Remarks</span></span>  

 <span data-ttu-id="35d2f-123">Özniteliği için olan değer `policyLevel` ya da olur `BypassCache` `Default` .</span><span class="sxs-lookup"><span data-stu-id="35d2f-123">The value for the `policyLevel` attribute is either `BypassCache` or `Default`.</span></span>  
  
 <span data-ttu-id="35d2f-124">`maximumAge`, `maximumStale` , Ve `minimumFresh` öğelerinin değerleri *d*biçimindeki açık bir zaman aralığıdır.\* SS*:*dd*:*SS\* (gün, saat, dakika, saniye) veya sabitler `minValue` ya da `maxValue` uygun şekilde.</span><span class="sxs-lookup"><span data-stu-id="35d2f-124">Values for the `maximumAge`, `maximumStale`, and `minimumFresh` elements are either an explicit time interval with a format of *d*.*hh*:*mm*:*ss* (days, hours, minutes, and seconds), or the constants `minValue` or `maxValue`, as appropriate.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="35d2f-125">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="35d2f-125">Configuration Files</span></span>  

 <span data-ttu-id="35d2f-126">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="35d2f-126">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="35d2f-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="35d2f-127">Example</span></span>  

 <span data-ttu-id="35d2f-128">Aşağıdaki örnek, en az altı saat, iki güne ait maksimum yaş süresi ve dört saatlik en fazla eski süreyi belirtmek için nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="35d2f-128">The following example shows how to specify a minimum fresh time of six hours, a maximum age time of two days, and a maximum stale time of four hours.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="35d2f-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="35d2f-129">See also</span></span>

- <xref:System.Net.Cache>
- <xref:System.Net.WebRequest>
- <xref:System.Net.Cache.RequestCacheLevel>
- [<span data-ttu-id="35d2f-130">Ağ ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="35d2f-130">Network Settings Schema</span></span>](index.md)
