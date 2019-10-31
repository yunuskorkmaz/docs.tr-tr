---
title: <gcConcurrent> Öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/gcConcurrent
- http://schemas.microsoft.com/.NetConfiguration/v2.0#gcConcurrent
helpviewer_keywords:
- container tags, <gcConcurrent> element
- gcConcurrent element
- <gcConcurrent> element
ms.assetid: 503f55ba-26ed-45ac-a2ea-caf994da04cd
ms.openlocfilehash: 4897462e20b193496c44d26923d0d0e2a13f7dd6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73116807"
---
# <a name="gcconcurrent-element"></a><span data-ttu-id="9a0b1-102">\<gcConcurrent > öğesi</span><span class="sxs-lookup"><span data-stu-id="9a0b1-102">\<gcConcurrent> Element</span></span>

<span data-ttu-id="9a0b1-103">Ortak dil çalışma zamanının ayrı bir iş parçacığında çöp toplama işlemi yapıp yapmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="9a0b1-103">Specifies whether the common language runtime runs garbage collection on a separate thread.</span></span>

<span data-ttu-id="9a0b1-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="9a0b1-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="9a0b1-105">&nbsp; &nbsp;[ **\<runtime >** ](runtime-element.md) </span><span class="sxs-lookup"><span data-stu-id="9a0b1-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="9a0b1-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<gcConcurrent >**</span><span class="sxs-lookup"><span data-stu-id="9a0b1-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<gcConcurrent>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="9a0b1-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9a0b1-107">Syntax</span></span>

```xml
<gcConcurrent
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9a0b1-108">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="9a0b1-108">Attributes and elements</span></span>

<span data-ttu-id="9a0b1-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9a0b1-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="9a0b1-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="9a0b1-110">Attributes</span></span>

|<span data-ttu-id="9a0b1-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="9a0b1-111">Attribute</span></span>|<span data-ttu-id="9a0b1-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9a0b1-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="9a0b1-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="9a0b1-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="9a0b1-114">Çalışma zamanının çöp toplamayı eşzamanlı olarak çalıştırmasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="9a0b1-114">Specifies whether the runtime runs garbage collection concurrently.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="9a0b1-115">enabled özniteliği</span><span class="sxs-lookup"><span data-stu-id="9a0b1-115">enabled attribute</span></span>

|<span data-ttu-id="9a0b1-116">Değer</span><span class="sxs-lookup"><span data-stu-id="9a0b1-116">Value</span></span>|<span data-ttu-id="9a0b1-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9a0b1-117">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="9a0b1-118">Çöp toplamayı eşzamanlı olarak çalıştırmaz.</span><span class="sxs-lookup"><span data-stu-id="9a0b1-118">Doesn't run garbage collection concurrently.</span></span>|
|`true`|<span data-ttu-id="9a0b1-119">Çöp toplamayı eşzamanlı olarak çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="9a0b1-119">Runs garbage collection concurrently.</span></span> <span data-ttu-id="9a0b1-120">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="9a0b1-120">This is the default.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="9a0b1-121">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="9a0b1-121">Child elements</span></span>

<span data-ttu-id="9a0b1-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="9a0b1-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="9a0b1-123">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="9a0b1-123">Parent elements</span></span>

|<span data-ttu-id="9a0b1-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="9a0b1-124">Element</span></span>|<span data-ttu-id="9a0b1-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9a0b1-125">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="9a0b1-126">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="9a0b1-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="9a0b1-127">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="9a0b1-127">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="9a0b1-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9a0b1-128">Remarks</span></span>

<span data-ttu-id="9a0b1-129">.NET Framework 4 ' ten önce, iş istasyonu atık toplama, farklı bir iş parçacığında arka planda çöp toplamayı gerçekleştiren eşzamanlı çöp toplama işlemini destekliyordu.</span><span class="sxs-lookup"><span data-stu-id="9a0b1-129">Prior to the .NET Framework 4, workstation garbage collection supported concurrent garbage collection, which performed garbage collection in the background on a separate thread.</span></span> <span data-ttu-id="9a0b1-130">.NET Framework 4 ' te, eşzamanlı atık toplama, arka plan GC ile değiştirilmiştir ve bu da ayrı bir iş parçacığında arka planda çöp toplama işlemi gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="9a0b1-130">In the .NET Framework 4, concurrent garbage collection was replaced by background GC, which also performs garbage collection in the background on a separate thread.</span></span> <span data-ttu-id="9a0b1-131">.NET Framework 4,5 ' den başlayarak, arka plan koleksiyonu sunucu atık koleksiyonunda kullanılabilir hale geldi.</span><span class="sxs-lookup"><span data-stu-id="9a0b1-131">Starting with the .NET Framework 4.5, background collection became available in server garbage collection.</span></span> <span data-ttu-id="9a0b1-132">`<gcConcurrent>` öğesi, çalışma zamanının, varsa veya ön planda çöp toplama gerçekleştirip gerçekleştirmediğini kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="9a0b1-132">The `<gcConcurrent>` element controls whether the runtime performs either concurrent or background garbage collection, if it's available, or whether it performs garbage collection in the foreground.</span></span>

### <a name="to-disable-background-garbage-collection"></a><span data-ttu-id="9a0b1-133">Arka plan atık toplamayı devre dışı bırakmak için</span><span class="sxs-lookup"><span data-stu-id="9a0b1-133">To disable background garbage collection</span></span>

> [!WARNING]
> <span data-ttu-id="9a0b1-134">.NET Framework 4 ile başlayarak, eşzamanlı atık toplama arka plan atık toplama işlemi tarafından değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="9a0b1-134">Starting with the .NET Framework 4, concurrent garbage collection is replaced by background garbage collection.</span></span> <span data-ttu-id="9a0b1-135">*Eşzamanlı* ve *arka plan* terimleri .NET Framework belgelerde birbirinin yerine kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9a0b1-135">The terms *concurrent* and *background* are used interchangeably in the .NET Framework documentation.</span></span> <span data-ttu-id="9a0b1-136">Arka plan atık toplamayı devre dışı bırakmak için, bu makalede anlatıldığı gibi `<gcConcurrent>` öğesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="9a0b1-136">To disable background garbage collection, use the `<gcConcurrent>` element, as discussed in this article.</span></span>

<span data-ttu-id="9a0b1-137">Varsayılan olarak, çalışma zamanı, gecikme süresi için en iyi duruma getirilmiş olan eşzamanlı veya arka plan çöp toplamayı kullanır.</span><span class="sxs-lookup"><span data-stu-id="9a0b1-137">By default, the runtime uses concurrent or background garbage collection, which is optimized for latency.</span></span> <span data-ttu-id="9a0b1-138">Uygulamanız ağır Kullanıcı etkileşimi içeriyorsa, çöp toplama işlemini gerçekleştirmek için uygulamanın duraklatma süresini en aza indirmek için eşzamanlı çöp toplamayı etkin bırakın.</span><span class="sxs-lookup"><span data-stu-id="9a0b1-138">If your application involves heavy user interaction, leave concurrent garbage collection enabled to minimize the application's pause time to perform garbage collection.</span></span> <span data-ttu-id="9a0b1-139">`<gcConcurrent>` öğesinin `enabled` özniteliğini `false`olarak ayarlarsanız, çalışma zamanı işleme için optimize edilmiş, eşzamanlı olmayan çöp toplamayı kullanır.</span><span class="sxs-lookup"><span data-stu-id="9a0b1-139">If you set the `enabled` attribute of the `<gcConcurrent>` element to `false`, the runtime uses non-concurrent garbage collection, which is optimized for throughput.</span></span> <span data-ttu-id="9a0b1-140">Aşağıdaki yapılandırma dosyası arka plan atık toplamayı devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="9a0b1-140">The following configuration file disables background garbage collection.</span></span>

```xml
<configuration>
   <runtime>
      <gcConcurrent enabled="false"/>
   </runtime>
</configuration>
```

 <span data-ttu-id="9a0b1-141">Makine yapılandırma dosyasında bir `<gcConcurrentSetting>` ayarı varsa, tüm .NET Framework uygulamalar için varsayılan değeri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9a0b1-141">If there's a `<gcConcurrentSetting>` setting in the machine configuration file, it defines the default value for all .NET Framework applications.</span></span> <span data-ttu-id="9a0b1-142">Makine yapılandırma dosyası ayarı, uygulama yapılandırma dosyası ayarını geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="9a0b1-142">The machine configuration file setting overrides the application configuration file setting.</span></span>

 <span data-ttu-id="9a0b1-143">Eş zamanlı ve arka plan atık toplama hakkında daha fazla bilgi için [çöp toplama temelleri](../../../../standard/garbage-collection/fundamentals.md) makalesinin [eş zamanlı çöp toplama](../../../../standard/garbage-collection/fundamentals.md#concurrent-garbage-collection) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="9a0b1-143">For more information on concurrent and background garbage collection, see the [Concurrent garbage collection](../../../../standard/garbage-collection/fundamentals.md#concurrent-garbage-collection) section in the [Fundamentals of Garbage Collection](../../../../standard/garbage-collection/fundamentals.md) article.</span></span>

## <a name="example"></a><span data-ttu-id="9a0b1-144">Örnek</span><span class="sxs-lookup"><span data-stu-id="9a0b1-144">Example</span></span>

<span data-ttu-id="9a0b1-145">Aşağıdaki örnek, eşzamanlı atık toplamayı mümkün bir şekilde sunar:</span><span class="sxs-lookup"><span data-stu-id="9a0b1-145">The following example enables concurrent garbage collection:</span></span>

```xml
<configuration>
   <runtime>
      <gcConcurrent enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="9a0b1-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9a0b1-146">See also</span></span>

- [<span data-ttu-id="9a0b1-147">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="9a0b1-147">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="9a0b1-148">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="9a0b1-148">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="9a0b1-149">Atık Toplamanın Temelleri</span><span class="sxs-lookup"><span data-stu-id="9a0b1-149">Fundamentals of Garbage Collection</span></span>](../../../../standard/garbage-collection/fundamentals.md)
