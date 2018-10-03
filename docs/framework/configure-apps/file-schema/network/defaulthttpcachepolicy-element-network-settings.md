---
title: '&lt;defaultHttpCachePolicy&gt; öğesi (ağ ayarları)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching/defaultHttpCachePolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultHttpCachePolicy
helpviewer_keywords:
- defaultHttpCachePolicy element
- <defaultHttpCachePolicy> element
ms.assetid: 2c1247d0-39b0-4c12-919a-a925ce075c79
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 1e1b27cb8c0df4450c1a08151af19913b65fc2b3
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48028111"
---
# <a name="ltdefaulthttpcachepolicygt-element-network-settings"></a><span data-ttu-id="bbb38-102">&lt;defaultHttpCachePolicy&gt; öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="bbb38-102">&lt;defaultHttpCachePolicy&gt; Element (Network Settings)</span></span>
<span data-ttu-id="bbb38-103">HTTP önbelleğe alma etkindir ve önbelleğe alma ilkesi varsayılan tanımlar olup olmadığını açıklar.</span><span class="sxs-lookup"><span data-stu-id="bbb38-103">Describes whether HTTP caching is active and describes the default caching policy.</span></span>  
  
 <span data-ttu-id="bbb38-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="bbb38-104">\<configuration></span></span>  
<span data-ttu-id="bbb38-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="bbb38-105">\<system.net></span></span>  
<span data-ttu-id="bbb38-106">\<requestCaching ></span><span class="sxs-lookup"><span data-stu-id="bbb38-106">\<requestCaching></span></span>  
<span data-ttu-id="bbb38-107">\<defaultHttpCachePolicy ></span><span class="sxs-lookup"><span data-stu-id="bbb38-107">\<defaultHttpCachePolicy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bbb38-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bbb38-108">Syntax</span></span>  
  
```xml  
<defaultHttpCachePolicy  
  policyLevel="BypassCache|Default"  
  minimumFresh="d.hh:mm:ss|minValue|maxValue"  
  maximumAge="d.hh:mm:ss|minValue|maxValue"  
  maximumStale="d.hh:mm:ss|minValue|maxValue"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bbb38-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="bbb38-109">Attributes and Elements</span></span>  
 <span data-ttu-id="bbb38-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="bbb38-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bbb38-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="bbb38-111">Attributes</span></span>  
  
|<span data-ttu-id="bbb38-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="bbb38-112">Attribute</span></span>|<span data-ttu-id="bbb38-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bbb38-113">Description</span></span>|  
|---------------|-----------------|  
|`maximumAge`|<span data-ttu-id="bbb38-114">Önbelleğe alınmış nesnenin süresi dolmuş olarak işaretlenmeden önce maksimum zaman aralığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="bbb38-114">Specifies the maximum time interval before a cached object is marked as expired.</span></span>|  
|`maximumStale`|<span data-ttu-id="bbb38-115">Önbelleğe alınmış nesnenin süresi dolmuş olarak işaretlenmeden önce hesaplanan güncellik süresini geçen en uzun süreyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="bbb38-115">Specifies the maximum time past the computed freshness time before a cached object is marked as expired.</span></span>|  
|`minimumFresh`|<span data-ttu-id="bbb38-116">Yeni olarak değerlendirilmesi önbelleğe alınmış bir nesne için minimum süre belirtir.</span><span class="sxs-lookup"><span data-stu-id="bbb38-116">Specifies the minimum time for a cached object to be considered fresh.</span></span>|  
|`policyLevel`|<span data-ttu-id="bbb38-117">Önbellek ilkesi otomatik olup veya önbellek olup atlanır belirtir.</span><span class="sxs-lookup"><span data-stu-id="bbb38-117">Specifies whether the caching policy is automatic, or whether the cache is bypassed.</span></span> <span data-ttu-id="bbb38-118">Varsayılan değer `BypassCache` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="bbb38-118">The default value is `BypassCache`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bbb38-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="bbb38-119">Child Elements</span></span>  
 <span data-ttu-id="bbb38-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="bbb38-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bbb38-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="bbb38-121">Parent Elements</span></span>  
  
|<span data-ttu-id="bbb38-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="bbb38-122">Element</span></span>|<span data-ttu-id="bbb38-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bbb38-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bbb38-124">requestCaching</span><span class="sxs-lookup"><span data-stu-id="bbb38-124">requestCaching</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)|<span data-ttu-id="bbb38-125">Ağ istekleri için önbelleğe alma mekanizması denetler.</span><span class="sxs-lookup"><span data-stu-id="bbb38-125">Controls the caching mechanism for network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bbb38-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bbb38-126">Remarks</span></span>  
 <span data-ttu-id="bbb38-127">Değeri `policyLevel` özniteliği, ya da `BypassCache` veya `Default`.</span><span class="sxs-lookup"><span data-stu-id="bbb38-127">The value for the `policyLevel` attribute is either `BypassCache` or `Default`.</span></span>  
  
 <span data-ttu-id="bbb38-128">Değerleri `maximumAge`, `maximumStale`, ve `minimumFresh` öğeleri olan bir ya da açık bir zaman aralığı bir biçimi ile *d*. *hh*:*mm*:*ss* (gün, saat, dakika ve saniye) veya sabitler `minValue` veya `maxValue`uygun şekilde.</span><span class="sxs-lookup"><span data-stu-id="bbb38-128">Values for the `maximumAge`, `maximumStale`, and `minimumFresh` elements are either an explicit time interval with a format of *d*.*hh*:*mm*:*ss* (days, hours, minutes, and seconds), or the constants `minValue` or `maxValue`, as appropriate.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="bbb38-129">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="bbb38-129">Configuration Files</span></span>  
 <span data-ttu-id="bbb38-130">Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="bbb38-130">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bbb38-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="bbb38-131">Example</span></span>  
 <span data-ttu-id="bbb38-132">Aşağıdaki örnek, en düşük yeni birer birer en uzun geçerlilik süresi iki gün ve dört saatlik süre üst sınırını eski altı saat belirtin gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="bbb38-132">The following example shows how to specify a minimum fresh time of six hours, a maximum age time of two days, and a maximum stale time of four hours.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="bbb38-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bbb38-133">See Also</span></span>  
 <xref:System.Net.Cache>  
 <xref:System.Net.WebRequest>  
 <xref:System.Net.Cache.RequestCacheLevel>  
 [<span data-ttu-id="bbb38-134">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="bbb38-134">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
