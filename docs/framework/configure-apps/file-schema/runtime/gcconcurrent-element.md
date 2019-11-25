---
title: gcConcurrent öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/gcConcurrent
- http://schemas.microsoft.com/.NetConfiguration/v2.0#gcConcurrent
helpviewer_keywords:
- container tags, <gcConcurrent> element
- gcConcurrent element
- <gcConcurrent> element
ms.assetid: 503f55ba-26ed-45ac-a2ea-caf994da04cd
ms.openlocfilehash: 5957337aa960a0d5f445249b410dbfaddb7b08e9
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73969228"
---
# <a name="gcconcurrent-element"></a><span data-ttu-id="c1889-102">\<gcConcurrent > öğesi</span><span class="sxs-lookup"><span data-stu-id="c1889-102">\<gcConcurrent> element</span></span>

<span data-ttu-id="c1889-103">Ortak dil çalışma zamanının ayrı bir iş parçacığında çöp toplama işlemi yapıp yapmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c1889-103">Specifies whether the common language runtime runs garbage collection on a separate thread.</span></span>

<span data-ttu-id="c1889-104">[\<yapılandırma >](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c1889-104">[\<configuration>](../configuration-element.md)</span></span>\
<span data-ttu-id="c1889-105">&nbsp;&nbsp;[\<çalışma zamanı >](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="c1889-105">&nbsp;&nbsp;[\<runtime>](runtime-element.md)</span></span>\
<span data-ttu-id="c1889-106">&nbsp;&nbsp;&nbsp;&nbsp;\<gcConcurrent ></span><span class="sxs-lookup"><span data-stu-id="c1889-106">&nbsp;&nbsp;&nbsp;&nbsp;\<gcConcurrent></span></span>

## <a name="syntax"></a><span data-ttu-id="c1889-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c1889-107">Syntax</span></span>

```xml
<gcConcurrent
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c1889-108">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="c1889-108">Attributes and elements</span></span>

<span data-ttu-id="c1889-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c1889-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="c1889-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c1889-110">Attributes</span></span>

|<span data-ttu-id="c1889-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c1889-111">Attribute</span></span>|<span data-ttu-id="c1889-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c1889-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="c1889-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="c1889-113">Required attribute.</span></span><br /><br /><span data-ttu-id="c1889-114">Çalışma zamanının çöp toplamayı eşzamanlı olarak çalıştırmasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c1889-114">Specifies whether the runtime runs garbage collection concurrently.</span></span>|

#### <a name="enabled-attribute"></a><span data-ttu-id="c1889-115">enabled özniteliği</span><span class="sxs-lookup"><span data-stu-id="c1889-115">enabled attribute</span></span>

|<span data-ttu-id="c1889-116">Değer</span><span class="sxs-lookup"><span data-stu-id="c1889-116">Value</span></span>|<span data-ttu-id="c1889-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c1889-117">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="c1889-118">Çöp toplamayı eşzamanlı olarak çalıştırmaz.</span><span class="sxs-lookup"><span data-stu-id="c1889-118">Doesn't run garbage collection concurrently.</span></span>|
|`true`|<span data-ttu-id="c1889-119">Çöp toplamayı eşzamanlı olarak çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="c1889-119">Runs garbage collection concurrently.</span></span> <span data-ttu-id="c1889-120">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="c1889-120">This is the default.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="c1889-121">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="c1889-121">Child elements</span></span>

<span data-ttu-id="c1889-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="c1889-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c1889-123">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="c1889-123">Parent elements</span></span>

|<span data-ttu-id="c1889-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="c1889-124">Element</span></span>|<span data-ttu-id="c1889-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c1889-125">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="c1889-126">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="c1889-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="c1889-127">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="c1889-127">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c1889-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c1889-128">Remarks</span></span>

<span data-ttu-id="c1889-129">.NET Framework 4 ' ten önce iş istasyonu atık toplama, farklı bir iş parçacığında arka planda çöp toplamayı gerçekleştiren eşzamanlı çöp toplama işlemini destekliyordu.</span><span class="sxs-lookup"><span data-stu-id="c1889-129">Prior to .NET Framework 4, workstation garbage collection supported concurrent garbage collection, which performed garbage collection in the background on a separate thread.</span></span> <span data-ttu-id="c1889-130">.NET Framework 4 ' te, eşzamanlı atık toplama, arka plan GC ile değiştirilmiştir ve bu da ayrı bir iş parçacığında arka planda çöp toplama işlemi gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="c1889-130">In .NET Framework 4, concurrent garbage collection was replaced by background GC, which also performs garbage collection in the background on a separate thread.</span></span> <span data-ttu-id="c1889-131">.NET Framework 4,5 ' den başlayarak, arka plan koleksiyonu sunucu atık toplamada kullanılabilir duruma geldi.</span><span class="sxs-lookup"><span data-stu-id="c1889-131">Starting with .NET Framework 4.5, background collection became available in server garbage collection.</span></span> <span data-ttu-id="c1889-132">**GcConcurrent** öğesi, çalışma zamanının, varsa veya ön planda çöp toplama gerçekleştirip gerçekleştirmediğini kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="c1889-132">The **gcConcurrent** element controls whether the runtime performs either concurrent or background garbage collection, if it's available, or whether it performs garbage collection in the foreground.</span></span>

### <a name="to-disable-background-garbage-collection"></a><span data-ttu-id="c1889-133">Arka plan atık toplamayı devre dışı bırakmak için</span><span class="sxs-lookup"><span data-stu-id="c1889-133">To disable background garbage collection</span></span>

> [!WARNING]
> <span data-ttu-id="c1889-134">.NET Framework 4 ' ten itibaren, eşzamanlı atık toplama, arka plan atık toplama ile değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="c1889-134">Starting with .NET Framework 4, concurrent garbage collection is replaced by background garbage collection.</span></span> <span data-ttu-id="c1889-135">*Eşzamanlı* ve *arka plan* terimleri .NET Framework belgelerde birbirinin yerine kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c1889-135">The terms *concurrent* and *background* are used interchangeably in the .NET Framework documentation.</span></span> <span data-ttu-id="c1889-136">Arka plan atık toplamayı devre dışı bırakmak için, bu makalede anlatıldığı gibi **gcConcurrent** öğesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="c1889-136">To disable background garbage collection, use the **gcConcurrent** element, as discussed in this article.</span></span>

<span data-ttu-id="c1889-137">Varsayılan olarak, çalışma zamanı, gecikme süresi için en iyi duruma getirilmiş olan eşzamanlı veya arka plan çöp toplamayı kullanır.</span><span class="sxs-lookup"><span data-stu-id="c1889-137">By default, the runtime uses concurrent or background garbage collection, which is optimized for latency.</span></span> <span data-ttu-id="c1889-138">Uygulamanız ağır Kullanıcı etkileşimi içeriyorsa, çöp toplama işlemini gerçekleştirmek için uygulamanın duraklatma süresini en aza indirmek için eşzamanlı çöp toplamayı etkin bırakın.</span><span class="sxs-lookup"><span data-stu-id="c1889-138">If your application involves heavy user interaction, leave concurrent garbage collection enabled to minimize the application's pause time to perform garbage collection.</span></span> <span data-ttu-id="c1889-139">**GcConcurrent** öğesinin `enabled` özniteliğini `false`olarak ayarlarsanız, çalışma zamanı işleme için optimize edilmiş, eşzamanlı olmayan çöp toplamayı kullanır.</span><span class="sxs-lookup"><span data-stu-id="c1889-139">If you set the `enabled` attribute of the **gcConcurrent** element to `false`, the runtime uses non-concurrent garbage collection, which is optimized for throughput.</span></span>

<span data-ttu-id="c1889-140">Aşağıdaki yapılandırma dosyası arka plan atık toplamayı devre dışı bırakır:</span><span class="sxs-lookup"><span data-stu-id="c1889-140">The following configuration file disables background garbage collection:</span></span>

```xml
<configuration>
   <runtime>
      <gcConcurrent enabled="false"/>
   </runtime>
</configuration>
```

<span data-ttu-id="c1889-141">Makine yapılandırma dosyasında bir **gcConcurrentSetting** ayarı varsa, tüm .NET Framework uygulamalar için varsayılan değeri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c1889-141">If there's a **gcConcurrentSetting** setting in the machine configuration file, it defines the default value for all .NET Framework applications.</span></span> <span data-ttu-id="c1889-142">Makine yapılandırma dosyası ayarı, uygulama yapılandırma dosyası ayarını geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="c1889-142">The machine configuration file setting overrides the application configuration file setting.</span></span>

<span data-ttu-id="c1889-143">Eş zamanlı ve arka plan atık toplama hakkında daha fazla bilgi için [çöp toplama temelleri](../../../../standard/garbage-collection/fundamentals.md) makalesinin [eş zamanlı çöp toplama](../../../../standard/garbage-collection/fundamentals.md#concurrent-garbage-collection), [arka plan Iş Istasyonu çöp toplama](../../../../standard/garbage-collection/fundamentals.md#background-workstation-garbage-collection)ve [arka plan sunucusu çöp toplama](../../../../standard/garbage-collection/fundamentals.md#background-server-garbage-collection) bölümlerine bakın.</span><span class="sxs-lookup"><span data-stu-id="c1889-143">For more information on concurrent and background garbage collection, see the [Concurrent garbage collection](../../../../standard/garbage-collection/fundamentals.md#concurrent-garbage-collection), [Background workstation garbage collection](../../../../standard/garbage-collection/fundamentals.md#background-workstation-garbage-collection), and [Background server garbage collection](../../../../standard/garbage-collection/fundamentals.md#background-server-garbage-collection) sections in the [Fundamentals of Garbage Collection](../../../../standard/garbage-collection/fundamentals.md) article.</span></span>

## <a name="example"></a><span data-ttu-id="c1889-144">Örnek</span><span class="sxs-lookup"><span data-stu-id="c1889-144">Example</span></span>

<span data-ttu-id="c1889-145">Aşağıdaki örnek, arka plan atık toplamayı mümkün bir şekilde sunar:</span><span class="sxs-lookup"><span data-stu-id="c1889-145">The following example enables background garbage collection:</span></span>

```xml
<configuration>
   <runtime>
      <gcConcurrent enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="c1889-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c1889-146">See also</span></span>

- [<span data-ttu-id="c1889-147">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="c1889-147">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="c1889-148">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="c1889-148">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="c1889-149">Atık Toplamanın Temelleri</span><span class="sxs-lookup"><span data-stu-id="c1889-149">Fundamentals of Garbage Collection</span></span>](../../../../standard/garbage-collection/fundamentals.md)
