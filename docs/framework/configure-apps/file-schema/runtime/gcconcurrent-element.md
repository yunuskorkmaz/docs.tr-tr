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
ms.openlocfilehash: 249518ae7477d284d50f9010757db83b7752c657
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "82102924"
---
# <a name="gcconcurrent-element"></a><span data-ttu-id="85034-102">\<gcConcurrent> öğesi</span><span class="sxs-lookup"><span data-stu-id="85034-102">\<gcConcurrent> element</span></span>

<span data-ttu-id="85034-103">Ortak dil çalışma zamanının ayrı bir iş parçacığında çöp toplama işlemi yapıp yapmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="85034-103">Specifies whether the common language runtime runs garbage collection on a separate thread.</span></span>

[\<configuration>](../configuration-element.md)\
&nbsp;&nbsp;[\<runtime>](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;\<gcConcurrent>

## <a name="syntax"></a><span data-ttu-id="85034-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="85034-104">Syntax</span></span>

```xml
<gcConcurrent
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="85034-105">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="85034-105">Attributes and elements</span></span>

<span data-ttu-id="85034-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="85034-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="85034-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="85034-107">Attributes</span></span>

|<span data-ttu-id="85034-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="85034-108">Attribute</span></span>|<span data-ttu-id="85034-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="85034-109">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="85034-110">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="85034-110">Required attribute.</span></span><br /><br /><span data-ttu-id="85034-111">Çalışma zamanının çöp toplamayı eşzamanlı olarak çalıştırmasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="85034-111">Specifies whether the runtime runs garbage collection concurrently.</span></span>|

#### <a name="enabled-attribute"></a><span data-ttu-id="85034-112">enabled özniteliği</span><span class="sxs-lookup"><span data-stu-id="85034-112">enabled attribute</span></span>

|<span data-ttu-id="85034-113">Değer</span><span class="sxs-lookup"><span data-stu-id="85034-113">Value</span></span>|<span data-ttu-id="85034-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="85034-114">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="85034-115">Çöp toplamayı eşzamanlı olarak çalıştırmaz.</span><span class="sxs-lookup"><span data-stu-id="85034-115">Doesn't run garbage collection concurrently.</span></span>|
|`true`|<span data-ttu-id="85034-116">Çöp toplamayı eşzamanlı olarak çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="85034-116">Runs garbage collection concurrently.</span></span> <span data-ttu-id="85034-117">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="85034-117">This is the default.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="85034-118">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="85034-118">Child elements</span></span>

<span data-ttu-id="85034-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="85034-119">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="85034-120">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="85034-120">Parent elements</span></span>

|<span data-ttu-id="85034-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="85034-121">Element</span></span>|<span data-ttu-id="85034-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="85034-122">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="85034-123">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="85034-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="85034-124">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="85034-124">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="85034-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="85034-125">Remarks</span></span>

<span data-ttu-id="85034-126">.NET Framework 4 ' ten önce iş istasyonu atık toplama, farklı bir iş parçacığında arka planda çöp toplamayı gerçekleştiren eşzamanlı çöp toplama işlemini destekliyordu.</span><span class="sxs-lookup"><span data-stu-id="85034-126">Prior to .NET Framework 4, workstation garbage collection supported concurrent garbage collection, which performed garbage collection in the background on a separate thread.</span></span> <span data-ttu-id="85034-127">.NET Framework 4 ' te, eşzamanlı atık toplama, arka plan GC ile değiştirilmiştir ve bu da ayrı bir iş parçacığında arka planda çöp toplama işlemi gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="85034-127">In .NET Framework 4, concurrent garbage collection was replaced by background GC, which also performs garbage collection in the background on a separate thread.</span></span> <span data-ttu-id="85034-128">.NET Framework 4,5 ' den başlayarak, arka plan koleksiyonu sunucu atık toplamada kullanılabilir duruma geldi.</span><span class="sxs-lookup"><span data-stu-id="85034-128">Starting with .NET Framework 4.5, background collection became available in server garbage collection.</span></span> <span data-ttu-id="85034-129">**GcConcurrent** öğesi, çalışma zamanının, varsa veya ön planda çöp toplama gerçekleştirip gerçekleştirmediğini kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="85034-129">The **gcConcurrent** element controls whether the runtime performs either concurrent or background garbage collection, if it's available, or whether it performs garbage collection in the foreground.</span></span>

### <a name="to-disable-background-garbage-collection"></a><span data-ttu-id="85034-130">Arka plan atık toplamayı devre dışı bırakmak için</span><span class="sxs-lookup"><span data-stu-id="85034-130">To disable background garbage collection</span></span>

> [!WARNING]
> <span data-ttu-id="85034-131">.NET Framework 4 ' ten itibaren, eşzamanlı atık toplama, arka plan atık toplama ile değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="85034-131">Starting with .NET Framework 4, concurrent garbage collection is replaced by background garbage collection.</span></span> <span data-ttu-id="85034-132">*Eşzamanlı* ve *arka plan* terimleri .NET Framework belgelerde birbirinin yerine kullanılır.</span><span class="sxs-lookup"><span data-stu-id="85034-132">The terms *concurrent* and *background* are used interchangeably in the .NET Framework documentation.</span></span> <span data-ttu-id="85034-133">Arka plan atık toplamayı devre dışı bırakmak için, bu makalede anlatıldığı gibi **gcConcurrent** öğesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="85034-133">To disable background garbage collection, use the **gcConcurrent** element, as discussed in this article.</span></span>

<span data-ttu-id="85034-134">Varsayılan olarak, çalışma zamanı, gecikme süresi için en iyi duruma getirilmiş olan eşzamanlı veya arka plan çöp toplamayı kullanır.</span><span class="sxs-lookup"><span data-stu-id="85034-134">By default, the runtime uses concurrent or background garbage collection, which is optimized for latency.</span></span> <span data-ttu-id="85034-135">Uygulamanız ağır Kullanıcı etkileşimi içeriyorsa, çöp toplama işlemini gerçekleştirmek için uygulamanın duraklatma süresini en aza indirmek için eşzamanlı çöp toplamayı etkin bırakın.</span><span class="sxs-lookup"><span data-stu-id="85034-135">If your application involves heavy user interaction, leave concurrent garbage collection enabled to minimize the application's pause time to perform garbage collection.</span></span> <span data-ttu-id="85034-136">`enabled` **GcConcurrent** öğesinin özniteliğini olarak ayarlarsanız `false` , çalışma zamanı, aktarım hızı için iyileştirilmiş, eşzamanlı olmayan çöp toplamayı kullanır.</span><span class="sxs-lookup"><span data-stu-id="85034-136">If you set the `enabled` attribute of the **gcConcurrent** element to `false`, the runtime uses non-concurrent garbage collection, which is optimized for throughput.</span></span>

<span data-ttu-id="85034-137">Aşağıdaki yapılandırma dosyası arka plan atık toplamayı devre dışı bırakır:</span><span class="sxs-lookup"><span data-stu-id="85034-137">The following configuration file disables background garbage collection:</span></span>

```xml
<configuration>
   <runtime>
      <gcConcurrent enabled="false"/>
   </runtime>
</configuration>
```

<span data-ttu-id="85034-138">Makine yapılandırma dosyasında bir **gcConcurrentSetting** ayarı varsa, tüm .NET Framework uygulamalar için varsayılan değeri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="85034-138">If there's a **gcConcurrentSetting** setting in the machine configuration file, it defines the default value for all .NET Framework applications.</span></span> <span data-ttu-id="85034-139">Makine yapılandırma dosyası ayarı, uygulama yapılandırma dosyası ayarını geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="85034-139">The machine configuration file setting overrides the application configuration file setting.</span></span>

<span data-ttu-id="85034-140">Eşzamanlı ve arka plan atık toplama hakkında daha fazla bilgi için bkz. [arka plan atık toplama](../../../../standard/garbage-collection/background-gc.md).</span><span class="sxs-lookup"><span data-stu-id="85034-140">For more information on concurrent and background garbage collection, see [Background garbage collection](../../../../standard/garbage-collection/background-gc.md).</span></span>

## <a name="example"></a><span data-ttu-id="85034-141">Örnek</span><span class="sxs-lookup"><span data-stu-id="85034-141">Example</span></span>

<span data-ttu-id="85034-142">Aşağıdaki örnek, arka plan atık toplamayı mümkün bir şekilde sunar:</span><span class="sxs-lookup"><span data-stu-id="85034-142">The following example enables background garbage collection:</span></span>

```xml
<configuration>
   <runtime>
      <gcConcurrent enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="85034-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="85034-143">See also</span></span>

- [<span data-ttu-id="85034-144">Çalışma zamanı ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="85034-144">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="85034-145">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="85034-145">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="85034-146">Atık Toplamanın Temelleri</span><span class="sxs-lookup"><span data-stu-id="85034-146">Fundamentals of Garbage Collection</span></span>](../../../../standard/garbage-collection/fundamentals.md)
