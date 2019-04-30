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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0e2be4d9384f1e1ef73ce6064184aa2621a517a8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61674109"
---
# <a name="gcconcurrent-element"></a><span data-ttu-id="529fa-102">\<gcConcurrent > öğesi</span><span class="sxs-lookup"><span data-stu-id="529fa-102">\<gcConcurrent> Element</span></span>

<span data-ttu-id="529fa-103">Ortak dil çalışma zamanının atık toplama ayrı bir iş parçacığı üzerinde çalışıp çalışmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="529fa-103">Specifies whether the common language runtime runs garbage collection on a separate thread.</span></span>

<span data-ttu-id="529fa-104">\<Yapılandırma > \\</span><span class="sxs-lookup"><span data-stu-id="529fa-104">\<configuration>\\</span></span>
<span data-ttu-id="529fa-105">\<çalışma zamanı > \\</span><span class="sxs-lookup"><span data-stu-id="529fa-105">\<runtime>\\</span></span>
<span data-ttu-id="529fa-106">\<gcConcurrent ></span><span class="sxs-lookup"><span data-stu-id="529fa-106">\<gcConcurrent></span></span>

## <a name="syntax"></a><span data-ttu-id="529fa-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="529fa-107">Syntax</span></span>

```xml
<gcConcurrent
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="529fa-108">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="529fa-108">Attributes and elements</span></span>

<span data-ttu-id="529fa-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="529fa-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="529fa-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="529fa-110">Attributes</span></span>

|<span data-ttu-id="529fa-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="529fa-111">Attribute</span></span>|<span data-ttu-id="529fa-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="529fa-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="529fa-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="529fa-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="529fa-114">Çalışma zamanının atık toplama eşzamanlı olarak çalışıp çalışmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="529fa-114">Specifies whether the runtime runs garbage collection concurrently.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="529fa-115">Etkin öznitelik</span><span class="sxs-lookup"><span data-stu-id="529fa-115">enabled attribute</span></span>

|<span data-ttu-id="529fa-116">Değer</span><span class="sxs-lookup"><span data-stu-id="529fa-116">Value</span></span>|<span data-ttu-id="529fa-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="529fa-117">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="529fa-118">Çöp toplama, eşzamanlı olarak çalıştırılmaz.</span><span class="sxs-lookup"><span data-stu-id="529fa-118">Doesn't run garbage collection concurrently.</span></span>|
|`true`|<span data-ttu-id="529fa-119">Atık toplama eşzamanlı olarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="529fa-119">Runs garbage collection concurrently.</span></span> <span data-ttu-id="529fa-120">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="529fa-120">This is the default.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="529fa-121">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="529fa-121">Child elements</span></span>

<span data-ttu-id="529fa-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="529fa-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="529fa-123">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="529fa-123">Parent elements</span></span>

|<span data-ttu-id="529fa-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="529fa-124">Element</span></span>|<span data-ttu-id="529fa-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="529fa-125">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="529fa-126">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="529fa-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="529fa-127">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="529fa-127">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="529fa-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="529fa-128">Remarks</span></span>

<span data-ttu-id="529fa-129">Önce .NET Framework 4, atık toplama arka planda ayrı bir iş parçacığı üzerinde gerçekleştirilen eşzamanlı atık toplama, iş istasyonu çöp toplama desteklenir.</span><span class="sxs-lookup"><span data-stu-id="529fa-129">Prior to the .NET Framework 4, workstation garbage collection supported concurrent garbage collection, which performed garbage collection in the background on a separate thread.</span></span> <span data-ttu-id="529fa-130">.NET Framework 4'te, eş zamanlı çöp toplama, arka plan da ayrı bir iş parçacığı üzerinde arka planda atık toplama gerçekleştirir GC, tarafından değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="529fa-130">In the .NET Framework 4, concurrent garbage collection was replaced by background GC, which also performs garbage collection in the background on a separate thread.</span></span> <span data-ttu-id="529fa-131">.NET Framework 4.5 ile başlayarak, arka plan koleksiyonu sunucu çöp toplamada kullanıma sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="529fa-131">Starting with the .NET Framework 4.5, background collection became available in server garbage collection.</span></span> <span data-ttu-id="529fa-132">`<gcConcurrent>` Öğesi, çalışma zamanı ya da eşzamanlı gerçekleştirip gerçekleştirmediğini kontrol eder veya varsa veya ön planda atık toplama gerçekleştiğini plan çöp toplama.</span><span class="sxs-lookup"><span data-stu-id="529fa-132">The `<gcConcurrent>` element controls whether the runtime performs either concurrent or background garbage collection, if it's available, or whether it performs garbage collection in the foreground.</span></span>

### <a name="to-disable-background-garbage-collection"></a><span data-ttu-id="529fa-133">Arka plan çöp toplama devre dışı bırakmak için</span><span class="sxs-lookup"><span data-stu-id="529fa-133">To disable background garbage collection</span></span>

> [!WARNING]
> <span data-ttu-id="529fa-134">.NET Framework 4 ile başlayarak, eşzamanlı atık toplama arka plan atık toplama işlemi tarafından değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="529fa-134">Starting with the .NET Framework 4, concurrent garbage collection is replaced by background garbage collection.</span></span> <span data-ttu-id="529fa-135">Koşulları *eşzamanlı* ve *arka plan* .NET Framework belgelerinde birbirinin yerine kullanılır.</span><span class="sxs-lookup"><span data-stu-id="529fa-135">The terms *concurrent* and *background* are used interchangeably in the .NET Framework documentation.</span></span> <span data-ttu-id="529fa-136">Arka plan çöp toplama devre dışı bırakmak için `<gcConcurrent>` bu makalede ele alınan öğesi.</span><span class="sxs-lookup"><span data-stu-id="529fa-136">To disable background garbage collection, use the `<gcConcurrent>` element, as discussed in this article.</span></span>

<span data-ttu-id="529fa-137">Varsayılan, çalışma zamanı kullanan eş zamanlı veya arka plan çöp toplama, hangi gecikme süresi için optimize edilmiştir.</span><span class="sxs-lookup"><span data-stu-id="529fa-137">By default, the runtime uses concurrent or background garbage collection, which is optimized for latency.</span></span> <span data-ttu-id="529fa-138">Uygulamanız yoğun bir kullanıcı etkileşimi gerektiriyorsa, eşzamanlı çöp toplama atık toplama işini gerçekleştirmek için uygulamanın duraklatma süresi en aza indirmek için etkin bırakın.</span><span class="sxs-lookup"><span data-stu-id="529fa-138">If your application involves heavy user interaction, leave concurrent garbage collection enabled to minimize the application's pause time to perform garbage collection.</span></span> <span data-ttu-id="529fa-139">Ayarlarsanız `enabled` özniteliği `<gcConcurrent>` öğesine `false`, aktarım hızı için en iyi duruma getirilmiş eşzamanlı olmayan çöp toplama, çalışma zamanı kullanır.</span><span class="sxs-lookup"><span data-stu-id="529fa-139">If you set the `enabled` attribute of the `<gcConcurrent>` element to `false`, the runtime uses non-concurrent garbage collection, which is optimized for throughput.</span></span> <span data-ttu-id="529fa-140">Şu yapılandırma dosyasını arka plan çöp toplama devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="529fa-140">The following configuration file disables background garbage collection.</span></span>

```xml
<configuration>
   <runtime>
      <gcConcurrent enabled="false"/>
   </runtime>
</configuration>
```

 <span data-ttu-id="529fa-141">Varsa bir `<gcConcurrentSetting>` makine yapılandırma dosyasında ayarı, tüm .NET Framework uygulamaları için varsayılan değer tanımlar.</span><span class="sxs-lookup"><span data-stu-id="529fa-141">If there's a `<gcConcurrentSetting>` setting in the machine configuration file, it defines the default value for all .NET Framework applications.</span></span> <span data-ttu-id="529fa-142">Makine yapılandırma dosyası ayarı, uygulama yapılandırma dosyası ayarı geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="529fa-142">The machine configuration file setting overrides the application configuration file setting.</span></span>

 <span data-ttu-id="529fa-143">Daha fazla eşzamanlı hakkında bilgi ve arka plan çöp toplama için bkz: [eş zamanlı çöp toplama](../../../../standard/garbage-collection/fundamentals.md#concurrent-garbage-collection) konusundaki [çöp toplamanın Temelleri](../../../../standard/garbage-collection/fundamentals.md) makalesi.</span><span class="sxs-lookup"><span data-stu-id="529fa-143">For more information on concurrent and background garbage collection, see the [Concurrent garbage collection](../../../../standard/garbage-collection/fundamentals.md#concurrent-garbage-collection) section in the [Fundamentals of Garbage Collection](../../../../standard/garbage-collection/fundamentals.md) article.</span></span>

## <a name="example"></a><span data-ttu-id="529fa-144">Örnek</span><span class="sxs-lookup"><span data-stu-id="529fa-144">Example</span></span>

<span data-ttu-id="529fa-145">Aşağıdaki örnek, eş zamanlı çöp toplama sağlar:</span><span class="sxs-lookup"><span data-stu-id="529fa-145">The following example enables concurrent garbage collection:</span></span>

```xml
<configuration>
   <runtime>
      <gcConcurrent enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="529fa-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="529fa-146">See also</span></span>

- [<span data-ttu-id="529fa-147">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="529fa-147">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="529fa-148">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="529fa-148">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="529fa-149">Atık Toplamanın Temelleri</span><span class="sxs-lookup"><span data-stu-id="529fa-149">Fundamentals of Garbage Collection</span></span>](../../../../standard/garbage-collection/fundamentals.md)
