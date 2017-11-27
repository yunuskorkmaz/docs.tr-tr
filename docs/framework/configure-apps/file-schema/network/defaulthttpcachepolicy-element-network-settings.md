---
title: "&lt;defaultHttpCachePolicy&gt; öğesi (ağ ayarları)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching/defaultHttpCachePolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultHttpCachePolicy
helpviewer_keywords:
- defaultHttpCachePolicy element
- <defaultHttpCachePolicy> element
ms.assetid: 2c1247d0-39b0-4c12-919a-a925ce075c79
caps.latest.revision: "19"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: f2db2fd10ca20209c21c8add71d8ee4f26951ca6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltdefaulthttpcachepolicygt-element-network-settings"></a><span data-ttu-id="72f47-102">&lt;defaultHttpCachePolicy&gt; öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="72f47-102">&lt;defaultHttpCachePolicy&gt; Element (Network Settings)</span></span>
<span data-ttu-id="72f47-103">HTTP önbelleğe alma etkindir ve ilke önbelleğe almayı varsayılan açıklar olup olmadığını açıklar.</span><span class="sxs-lookup"><span data-stu-id="72f47-103">Describes whether HTTP caching is active and describes the default caching policy.</span></span>  
  
 <span data-ttu-id="72f47-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="72f47-104">\<configuration></span></span>  
<span data-ttu-id="72f47-105">\<System.NET ></span><span class="sxs-lookup"><span data-stu-id="72f47-105">\<system.net></span></span>  
<span data-ttu-id="72f47-106">\<requestCaching ></span><span class="sxs-lookup"><span data-stu-id="72f47-106">\<requestCaching></span></span>  
<span data-ttu-id="72f47-107">\<defaultHttpCachePolicy ></span><span class="sxs-lookup"><span data-stu-id="72f47-107">\<defaultHttpCachePolicy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72f47-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="72f47-108">Syntax</span></span>  
  
```xml  
<defaultHttpCachePolicy  
  policyLevel="BypassCache|Default"  
  minimumFresh="d.hh:mm:ss|minValue|maxValue"  
  maximumAge="d.hh:mm:ss|minValue|maxValue"  
  maximumStale="d.hh:mm:ss|minValue|maxValue"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="72f47-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="72f47-109">Attributes and Elements</span></span>  
 <span data-ttu-id="72f47-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="72f47-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="72f47-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="72f47-111">Attributes</span></span>  
  
|<span data-ttu-id="72f47-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="72f47-112">Attribute</span></span>|<span data-ttu-id="72f47-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="72f47-113">Description</span></span>|  
|---------------|-----------------|  
|`maximumAge`|<span data-ttu-id="72f47-114">Önbelleğe alınmış nesnenin süresi dolmuş olarak işaretlenmiş önce maksimum zaman aralığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="72f47-114">Specifies the maximum time interval before a cached object is marked as expired.</span></span>|  
|`maximumStale`|<span data-ttu-id="72f47-115">Önbelleğe alınmış nesnenin süresi dolmuş olarak işaretlenmiş önce hesaplanan yenilik süresini geçen en uzun süreyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="72f47-115">Specifies the maximum time past the computed freshness time before a cached object is marked as expired.</span></span>|  
|`minimumFresh`|<span data-ttu-id="72f47-116">Yeni olarak kabul edilmesi önbelleğe alınmış bir nesne için en düşük saat belirtir.</span><span class="sxs-lookup"><span data-stu-id="72f47-116">Specifies the minimum time for a cached object to be considered fresh.</span></span>|  
|`policyLevel`|<span data-ttu-id="72f47-117">Önbellek ilkesi otomatik olup veya önbelleği atlanır olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="72f47-117">Specifies whether the caching policy is automatic, or whether the cache is bypassed.</span></span> <span data-ttu-id="72f47-118">Varsayılan değer `BypassCache` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="72f47-118">The default value is `BypassCache`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="72f47-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="72f47-119">Child Elements</span></span>  
 <span data-ttu-id="72f47-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="72f47-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="72f47-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="72f47-121">Parent Elements</span></span>  
  
|<span data-ttu-id="72f47-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="72f47-122">Element</span></span>|<span data-ttu-id="72f47-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="72f47-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="72f47-124">requestCaching</span><span class="sxs-lookup"><span data-stu-id="72f47-124">requestCaching</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)|<span data-ttu-id="72f47-125">Ağ isteği önbelleğe alma mekanizması denetler.</span><span class="sxs-lookup"><span data-stu-id="72f47-125">Controls the caching mechanism for network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="72f47-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="72f47-126">Remarks</span></span>  
 <span data-ttu-id="72f47-127">Değeri `policyLevel` özniteliktir ya da `BypassCache` veya `Default`.</span><span class="sxs-lookup"><span data-stu-id="72f47-127">The value for the `policyLevel` attribute is either `BypassCache` or `Default`.</span></span>  
  
 <span data-ttu-id="72f47-128">İçin değerler `maximumAge`, `maximumStale`, ve `minimumFresh` öğeleridir bir biçimi ile bir açık zaman aralığını *d*. *hh*:*mm*:*ss* (gün, saat, dakika ve saniye) veya sabitler `minValue` veya `maxValue`uygun şekilde.</span><span class="sxs-lookup"><span data-stu-id="72f47-128">Values for the `maximumAge`, `maximumStale`, and `minimumFresh` elements are either an explicit time interval with a format of *d*.*hh*:*mm*:*ss* (days, hours, minutes, and seconds), or the constants `minValue` or `maxValue`, as appropriate.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="72f47-129">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="72f47-129">Configuration Files</span></span>  
 <span data-ttu-id="72f47-130">Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="72f47-130">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="72f47-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="72f47-131">Example</span></span>  
 <span data-ttu-id="72f47-132">Aşağıdaki örnekte, altı saate, iki gün en fazla geçerlilik süresini ve dört saat maksimum eski süresi en az bir yeni saat belirtmek üzere gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="72f47-132">The following example shows how to specify a minimum fresh time of six hours, a maximum age time of two days, and a maximum stale time of four hours.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="72f47-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="72f47-133">See Also</span></span>  
 <xref:System.Net.Cache>  
 <xref:System.Net.WebRequest>  
 <xref:System.Net.Cache.RequestCacheLevel>  
 [<span data-ttu-id="72f47-134">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="72f47-134">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
