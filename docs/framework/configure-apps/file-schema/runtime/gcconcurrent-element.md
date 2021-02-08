---
description: 'Daha fazla bilgi edinin: <gcConcurrent> öğesi'
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
ms.openlocfilehash: dff8b073977c007a132cfbd685724a02ba37684b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787012"
---
# <a name="gcconcurrent-element"></a><span data-ttu-id="1856b-103">\<gcConcurrent> öğesi</span><span class="sxs-lookup"><span data-stu-id="1856b-103">\<gcConcurrent> element</span></span>

<span data-ttu-id="1856b-104">Ortak dil çalışma zamanının ayrı bir iş parçacığında çöp toplama işlemi yapıp yapmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="1856b-104">Specifies whether the common language runtime runs garbage collection on a separate thread.</span></span>

[\<configuration>](../configuration-element.md)\
&nbsp;&nbsp;[\<runtime>](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;\<gcConcurrent>

## <a name="syntax"></a><span data-ttu-id="1856b-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="1856b-105">Syntax</span></span>

```xml
<gcConcurrent
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1856b-106">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="1856b-106">Attributes and elements</span></span>

<span data-ttu-id="1856b-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1856b-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="1856b-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="1856b-108">Attributes</span></span>

|<span data-ttu-id="1856b-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="1856b-109">Attribute</span></span>|<span data-ttu-id="1856b-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1856b-110">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="1856b-111">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="1856b-111">Required attribute.</span></span><br /><br /><span data-ttu-id="1856b-112">Çalışma zamanının çöp toplamayı eşzamanlı olarak çalıştırmasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="1856b-112">Specifies whether the runtime runs garbage collection concurrently.</span></span>|

#### <a name="enabled-attribute"></a><span data-ttu-id="1856b-113">enabled özniteliği</span><span class="sxs-lookup"><span data-stu-id="1856b-113">enabled attribute</span></span>

|<span data-ttu-id="1856b-114">Değer</span><span class="sxs-lookup"><span data-stu-id="1856b-114">Value</span></span>|<span data-ttu-id="1856b-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1856b-115">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="1856b-116">Çöp toplamayı eşzamanlı olarak çalıştırmaz.</span><span class="sxs-lookup"><span data-stu-id="1856b-116">Doesn't run garbage collection concurrently.</span></span>|
|`true`|<span data-ttu-id="1856b-117">Çöp toplamayı eşzamanlı olarak çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="1856b-117">Runs garbage collection concurrently.</span></span> <span data-ttu-id="1856b-118">Bu varsayılan seçenektir.</span><span class="sxs-lookup"><span data-stu-id="1856b-118">This is the default.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="1856b-119">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="1856b-119">Child elements</span></span>

<span data-ttu-id="1856b-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="1856b-120">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="1856b-121">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="1856b-121">Parent elements</span></span>

|<span data-ttu-id="1856b-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="1856b-122">Element</span></span>|<span data-ttu-id="1856b-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1856b-123">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="1856b-124">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="1856b-124">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="1856b-125">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="1856b-125">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="1856b-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1856b-126">Remarks</span></span>

<span data-ttu-id="1856b-127">.NET Framework 4 ' ten önce iş istasyonu atık toplama, farklı bir iş parçacığında arka planda çöp toplamayı gerçekleştiren eşzamanlı çöp toplama işlemini destekliyordu.</span><span class="sxs-lookup"><span data-stu-id="1856b-127">Prior to .NET Framework 4, workstation garbage collection supported concurrent garbage collection, which performed garbage collection in the background on a separate thread.</span></span> <span data-ttu-id="1856b-128">.NET Framework 4 ' te, eşzamanlı atık toplama, arka plan GC ile değiştirilmiştir ve bu da ayrı bir iş parçacığında arka planda çöp toplama işlemi gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="1856b-128">In .NET Framework 4, concurrent garbage collection was replaced by background GC, which also performs garbage collection in the background on a separate thread.</span></span> <span data-ttu-id="1856b-129">.NET Framework 4,5 ' den başlayarak, arka plan koleksiyonu sunucu atık toplamada kullanılabilir duruma geldi.</span><span class="sxs-lookup"><span data-stu-id="1856b-129">Starting with .NET Framework 4.5, background collection became available in server garbage collection.</span></span> <span data-ttu-id="1856b-130">**GcConcurrent** öğesi, çalışma zamanının, varsa veya ön planda çöp toplama gerçekleştirip gerçekleştirmediğini kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="1856b-130">The **gcConcurrent** element controls whether the runtime performs either concurrent or background garbage collection, if it's available, or whether it performs garbage collection in the foreground.</span></span>

### <a name="to-disable-background-garbage-collection"></a><span data-ttu-id="1856b-131">Arka plan atık toplamayı devre dışı bırakmak için</span><span class="sxs-lookup"><span data-stu-id="1856b-131">To disable background garbage collection</span></span>

> [!WARNING]
> <span data-ttu-id="1856b-132">.NET Framework 4 ' ten itibaren, eşzamanlı atık toplama, arka plan atık toplama ile değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="1856b-132">Starting with .NET Framework 4, concurrent garbage collection is replaced by background garbage collection.</span></span> <span data-ttu-id="1856b-133">*Eşzamanlı* ve *arka plan* terimleri .NET Framework belgelerde birbirinin yerine kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1856b-133">The terms *concurrent* and *background* are used interchangeably in the .NET Framework documentation.</span></span> <span data-ttu-id="1856b-134">Arka plan atık toplamayı devre dışı bırakmak için, bu makalede anlatıldığı gibi **gcConcurrent** öğesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="1856b-134">To disable background garbage collection, use the **gcConcurrent** element, as discussed in this article.</span></span>

<span data-ttu-id="1856b-135">Varsayılan olarak, çalışma zamanı, gecikme süresi için en iyi duruma getirilmiş olan eşzamanlı veya arka plan çöp toplamayı kullanır.</span><span class="sxs-lookup"><span data-stu-id="1856b-135">By default, the runtime uses concurrent or background garbage collection, which is optimized for latency.</span></span> <span data-ttu-id="1856b-136">Uygulamanız ağır Kullanıcı etkileşimi içeriyorsa, çöp toplama işlemini gerçekleştirmek için uygulamanın duraklatma süresini en aza indirmek için eşzamanlı çöp toplamayı etkin bırakın.</span><span class="sxs-lookup"><span data-stu-id="1856b-136">If your application involves heavy user interaction, leave concurrent garbage collection enabled to minimize the application's pause time to perform garbage collection.</span></span> <span data-ttu-id="1856b-137">`enabled` **GcConcurrent** öğesinin özniteliğini olarak ayarlarsanız `false` , çalışma zamanı, aktarım hızı için iyileştirilmiş, eşzamanlı olmayan çöp toplamayı kullanır.</span><span class="sxs-lookup"><span data-stu-id="1856b-137">If you set the `enabled` attribute of the **gcConcurrent** element to `false`, the runtime uses non-concurrent garbage collection, which is optimized for throughput.</span></span>

<span data-ttu-id="1856b-138">Aşağıdaki yapılandırma dosyası arka plan atık toplamayı devre dışı bırakır:</span><span class="sxs-lookup"><span data-stu-id="1856b-138">The following configuration file disables background garbage collection:</span></span>

```xml
<configuration>
   <runtime>
      <gcConcurrent enabled="false"/>
   </runtime>
</configuration>
```

<span data-ttu-id="1856b-139">Makine yapılandırma dosyasında bir **gcConcurrentSetting** ayarı varsa, tüm .NET Framework uygulamalar için varsayılan değeri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1856b-139">If there's a **gcConcurrentSetting** setting in the machine configuration file, it defines the default value for all .NET Framework applications.</span></span> <span data-ttu-id="1856b-140">Makine yapılandırma dosyası ayarı, uygulama yapılandırma dosyası ayarını geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="1856b-140">The machine configuration file setting overrides the application configuration file setting.</span></span>

<span data-ttu-id="1856b-141">Eşzamanlı ve arka plan atık toplama hakkında daha fazla bilgi için bkz. [arka plan atık toplama](../../../../standard/garbage-collection/background-gc.md).</span><span class="sxs-lookup"><span data-stu-id="1856b-141">For more information on concurrent and background garbage collection, see [Background garbage collection](../../../../standard/garbage-collection/background-gc.md).</span></span>

## <a name="example"></a><span data-ttu-id="1856b-142">Örnek</span><span class="sxs-lookup"><span data-stu-id="1856b-142">Example</span></span>

<span data-ttu-id="1856b-143">Aşağıdaki örnek, arka plan atık toplamayı mümkün bir şekilde sunar:</span><span class="sxs-lookup"><span data-stu-id="1856b-143">The following example enables background garbage collection:</span></span>

```xml
<configuration>
   <runtime>
      <gcConcurrent enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="1856b-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1856b-144">See also</span></span>

- [<span data-ttu-id="1856b-145">Çalışma zamanı ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="1856b-145">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="1856b-146">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="1856b-146">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="1856b-147">Atık Toplamanın Temelleri</span><span class="sxs-lookup"><span data-stu-id="1856b-147">Fundamentals of Garbage Collection</span></span>](../../../../standard/garbage-collection/fundamentals.md)
