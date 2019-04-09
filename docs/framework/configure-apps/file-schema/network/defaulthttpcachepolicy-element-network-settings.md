---
title: <defaultHttpCachePolicy> Öğesi (ağ ayarları)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching/defaultHttpCachePolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultHttpCachePolicy
helpviewer_keywords:
- defaultHttpCachePolicy element
- <defaultHttpCachePolicy> element
ms.assetid: 2c1247d0-39b0-4c12-919a-a925ce075c79
ms.openlocfilehash: 20d9b92ca2bbffd6b98b8641e5cef5e567cb84cc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59177391"
---
# <a name="defaulthttpcachepolicy-element-network-settings"></a><span data-ttu-id="e70bd-102">\<defaultHttpCachePolicy > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="e70bd-102">\<defaultHttpCachePolicy> Element (Network Settings)</span></span>
<span data-ttu-id="e70bd-103">HTTP önbelleğe alma etkindir ve önbelleğe alma ilkesi varsayılan tanımlar olup olmadığını açıklar.</span><span class="sxs-lookup"><span data-stu-id="e70bd-103">Describes whether HTTP caching is active and describes the default caching policy.</span></span>  
  
 <span data-ttu-id="e70bd-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="e70bd-104">\<configuration></span></span>  
<span data-ttu-id="e70bd-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="e70bd-105">\<system.net></span></span>  
<span data-ttu-id="e70bd-106">\<requestCaching ></span><span class="sxs-lookup"><span data-stu-id="e70bd-106">\<requestCaching></span></span>  
<span data-ttu-id="e70bd-107">\<defaultHttpCachePolicy ></span><span class="sxs-lookup"><span data-stu-id="e70bd-107">\<defaultHttpCachePolicy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e70bd-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e70bd-108">Syntax</span></span>  
  
```xml  
<defaultHttpCachePolicy  
  policyLevel="BypassCache|Default"  
  minimumFresh="d.hh:mm:ss|minValue|maxValue"  
  maximumAge="d.hh:mm:ss|minValue|maxValue"  
  maximumStale="d.hh:mm:ss|minValue|maxValue"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e70bd-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e70bd-109">Attributes and Elements</span></span>  
 <span data-ttu-id="e70bd-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e70bd-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e70bd-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e70bd-111">Attributes</span></span>  
  
|<span data-ttu-id="e70bd-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e70bd-112">Attribute</span></span>|<span data-ttu-id="e70bd-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e70bd-113">Description</span></span>|  
|---------------|-----------------|  
|`maximumAge`|<span data-ttu-id="e70bd-114">Önbelleğe alınmış nesnenin süresi dolmuş olarak işaretlenmeden önce maksimum zaman aralığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e70bd-114">Specifies the maximum time interval before a cached object is marked as expired.</span></span>|  
|`maximumStale`|<span data-ttu-id="e70bd-115">Önbelleğe alınmış nesnenin süresi dolmuş olarak işaretlenmeden önce hesaplanan güncellik süresini geçen en uzun süreyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="e70bd-115">Specifies the maximum time past the computed freshness time before a cached object is marked as expired.</span></span>|  
|`minimumFresh`|<span data-ttu-id="e70bd-116">Yeni olarak değerlendirilmesi önbelleğe alınmış bir nesne için minimum süre belirtir.</span><span class="sxs-lookup"><span data-stu-id="e70bd-116">Specifies the minimum time for a cached object to be considered fresh.</span></span>|  
|`policyLevel`|<span data-ttu-id="e70bd-117">Önbellek ilkesi otomatik olup veya önbellek olup atlanır belirtir.</span><span class="sxs-lookup"><span data-stu-id="e70bd-117">Specifies whether the caching policy is automatic, or whether the cache is bypassed.</span></span> <span data-ttu-id="e70bd-118">Varsayılan değer `BypassCache` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="e70bd-118">The default value is `BypassCache`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e70bd-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e70bd-119">Child Elements</span></span>  
 <span data-ttu-id="e70bd-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="e70bd-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e70bd-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e70bd-121">Parent Elements</span></span>  
  
|<span data-ttu-id="e70bd-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="e70bd-122">Element</span></span>|<span data-ttu-id="e70bd-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e70bd-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e70bd-124">requestCaching</span><span class="sxs-lookup"><span data-stu-id="e70bd-124">requestCaching</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)|<span data-ttu-id="e70bd-125">Ağ istekleri için önbelleğe alma mekanizması denetler.</span><span class="sxs-lookup"><span data-stu-id="e70bd-125">Controls the caching mechanism for network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e70bd-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e70bd-126">Remarks</span></span>  
 <span data-ttu-id="e70bd-127">Değeri `policyLevel` özniteliği, ya da `BypassCache` veya `Default`.</span><span class="sxs-lookup"><span data-stu-id="e70bd-127">The value for the `policyLevel` attribute is either `BypassCache` or `Default`.</span></span>  
  
 <span data-ttu-id="e70bd-128">Değerleri `maximumAge`, `maximumStale`, ve `minimumFresh` öğeleri olan bir ya da açık bir zaman aralığı bir biçimi ile *d*. *hh*:*mm*:*ss* (gün, saat, dakika ve saniye) veya sabitler `minValue` veya `maxValue`uygun şekilde.</span><span class="sxs-lookup"><span data-stu-id="e70bd-128">Values for the `maximumAge`, `maximumStale`, and `minimumFresh` elements are either an explicit time interval with a format of *d*.*hh*:*mm*:*ss* (days, hours, minutes, and seconds), or the constants `minValue` or `maxValue`, as appropriate.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="e70bd-129">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="e70bd-129">Configuration Files</span></span>  
 <span data-ttu-id="e70bd-130">Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e70bd-130">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e70bd-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="e70bd-131">Example</span></span>  
 <span data-ttu-id="e70bd-132">Aşağıdaki örnek, en düşük yeni birer birer en uzun geçerlilik süresi iki gün ve dört saatlik süre üst sınırını eski altı saat belirtin gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="e70bd-132">The following example shows how to specify a minimum fresh time of six hours, a maximum age time of two days, and a maximum stale time of four hours.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e70bd-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e70bd-133">See also</span></span>

- <xref:System.Net.Cache>
- <xref:System.Net.WebRequest>
- <xref:System.Net.Cache.RequestCacheLevel>
- [<span data-ttu-id="e70bd-134">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="e70bd-134">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
