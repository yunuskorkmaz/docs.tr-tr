---
title: gcEşzamanlı Eleman
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
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102924"
---
# <a name="gcconcurrent-element"></a><span data-ttu-id="e5af8-102">\<gcEşzamanlı> elemanı</span><span class="sxs-lookup"><span data-stu-id="e5af8-102">\<gcConcurrent> element</span></span>

<span data-ttu-id="e5af8-103">Ortak dil çalışma zamanının çöp toplamayı ayrı bir iş parçacığı üzerinde çalıştırıp çalıştırmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e5af8-103">Specifies whether the common language runtime runs garbage collection on a separate thread.</span></span>

<span data-ttu-id="e5af8-104">[\<yapılandırma>](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e5af8-104">[\<configuration>](../configuration-element.md)</span></span>\
<span data-ttu-id="e5af8-105">&nbsp;&nbsp;[\<çalışma zamanı>](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="e5af8-105">&nbsp;&nbsp;[\<runtime>](runtime-element.md)</span></span>\
<span data-ttu-id="e5af8-106">&nbsp;&nbsp;&nbsp;&nbsp;\<gcEşzamanlı></span><span class="sxs-lookup"><span data-stu-id="e5af8-106">&nbsp;&nbsp;&nbsp;&nbsp;\<gcConcurrent></span></span>

## <a name="syntax"></a><span data-ttu-id="e5af8-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e5af8-107">Syntax</span></span>

```xml
<gcConcurrent
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e5af8-108">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="e5af8-108">Attributes and elements</span></span>

<span data-ttu-id="e5af8-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e5af8-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="e5af8-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e5af8-110">Attributes</span></span>

|<span data-ttu-id="e5af8-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e5af8-111">Attribute</span></span>|<span data-ttu-id="e5af8-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e5af8-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="e5af8-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="e5af8-113">Required attribute.</span></span><br /><br /><span data-ttu-id="e5af8-114">Çalışma zamanının çöp toplamayı aynı anda çalıştırıp çalıştırmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e5af8-114">Specifies whether the runtime runs garbage collection concurrently.</span></span>|

#### <a name="enabled-attribute"></a><span data-ttu-id="e5af8-115">etkin öznitelik</span><span class="sxs-lookup"><span data-stu-id="e5af8-115">enabled attribute</span></span>

|<span data-ttu-id="e5af8-116">Değer</span><span class="sxs-lookup"><span data-stu-id="e5af8-116">Value</span></span>|<span data-ttu-id="e5af8-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e5af8-117">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="e5af8-118">Çöp toplamayı aynı anda çalıştırmıyor.</span><span class="sxs-lookup"><span data-stu-id="e5af8-118">Doesn't run garbage collection concurrently.</span></span>|
|`true`|<span data-ttu-id="e5af8-119">Çöp toplamayı aynı anda çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="e5af8-119">Runs garbage collection concurrently.</span></span> <span data-ttu-id="e5af8-120">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="e5af8-120">This is the default.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="e5af8-121">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="e5af8-121">Child elements</span></span>

<span data-ttu-id="e5af8-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="e5af8-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e5af8-123">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="e5af8-123">Parent elements</span></span>

|<span data-ttu-id="e5af8-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="e5af8-124">Element</span></span>|<span data-ttu-id="e5af8-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e5af8-125">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="e5af8-126">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="e5af8-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="e5af8-127">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="e5af8-127">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e5af8-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e5af8-128">Remarks</span></span>

<span data-ttu-id="e5af8-129">.NET Framework 4'ten önce, iş istasyonu çöp toplama, arka planda ayrı bir iş parçacığı üzerinde çöp toplama işlemini gerçekleştiren eşzamanlı çöp toplamayı destekler.</span><span class="sxs-lookup"><span data-stu-id="e5af8-129">Prior to .NET Framework 4, workstation garbage collection supported concurrent garbage collection, which performed garbage collection in the background on a separate thread.</span></span> <span data-ttu-id="e5af8-130">.NET Framework 4'te, eşzamanlı çöp toplama, arka planda ayrı bir iş parçacığı üzerinde çöp toplama da gerçekleştiren arka plan GC ile değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="e5af8-130">In .NET Framework 4, concurrent garbage collection was replaced by background GC, which also performs garbage collection in the background on a separate thread.</span></span> <span data-ttu-id="e5af8-131">.NET Framework 4.5 ile başlayarak, arka plan koleksiyonu sunucu çöp toplama kullanılabilir hale geldi.</span><span class="sxs-lookup"><span data-stu-id="e5af8-131">Starting with .NET Framework 4.5, background collection became available in server garbage collection.</span></span> <span data-ttu-id="e5af8-132">**gcConcurrent** öğesi, çalışma zamanının eşzamanlı veya arka plan çöp toplama gerçekleştirip gerçekleştirmediğini, kullanılabilir olup olmadığını veya ön planda çöp toplama yı gerçekleştirip gerçekleştirmediğini denetler.</span><span class="sxs-lookup"><span data-stu-id="e5af8-132">The **gcConcurrent** element controls whether the runtime performs either concurrent or background garbage collection, if it's available, or whether it performs garbage collection in the foreground.</span></span>

### <a name="to-disable-background-garbage-collection"></a><span data-ttu-id="e5af8-133">Arka plan çöp koleksiyonunu devre dışı atmak için</span><span class="sxs-lookup"><span data-stu-id="e5af8-133">To disable background garbage collection</span></span>

> [!WARNING]
> <span data-ttu-id="e5af8-134">.NET Framework 4 ile başlayarak, eşzamanlı çöp toplama arka plan çöp toplama ile değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="e5af8-134">Starting with .NET Framework 4, concurrent garbage collection is replaced by background garbage collection.</span></span> <span data-ttu-id="e5af8-135">*Eşzamanlı* ve *arka plan* terimleri .NET Framework belgelerinde birbirinin yerine kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e5af8-135">The terms *concurrent* and *background* are used interchangeably in the .NET Framework documentation.</span></span> <span data-ttu-id="e5af8-136">Arka plan çöp koleksiyonunu devre dışı katmak için, bu makalede belirtildiği gibi **gcConcurrent** öğesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="e5af8-136">To disable background garbage collection, use the **gcConcurrent** element, as discussed in this article.</span></span>

<span data-ttu-id="e5af8-137">Varsayılan olarak, çalışma süresi gecikme süresi için en iyi duruma getirilmiş eşzamanlı veya arka plan çöp toplama kullanır.</span><span class="sxs-lookup"><span data-stu-id="e5af8-137">By default, the runtime uses concurrent or background garbage collection, which is optimized for latency.</span></span> <span data-ttu-id="e5af8-138">Uygulamanız ağır kullanıcı etkileşimi içeriyorsa, eşzamanlı çöp toplamayı, uygulamanın çöp toplama gerçekleştirme süresini en aza indirmek için etkin bırakın.</span><span class="sxs-lookup"><span data-stu-id="e5af8-138">If your application involves heavy user interaction, leave concurrent garbage collection enabled to minimize the application's pause time to perform garbage collection.</span></span> <span data-ttu-id="e5af8-139">`enabled` **GcConcurrent** öğesinin özniteliğini `false`, çalışma zamanı, iş için en iyi duruma getirilmiş eşzamanlı olmayan çöp toplama yı kullanır.</span><span class="sxs-lookup"><span data-stu-id="e5af8-139">If you set the `enabled` attribute of the **gcConcurrent** element to `false`, the runtime uses non-concurrent garbage collection, which is optimized for throughput.</span></span>

<span data-ttu-id="e5af8-140">Aşağıdaki yapılandırma dosyası arka plan çöp toplama devre dışı kalmaktadır:</span><span class="sxs-lookup"><span data-stu-id="e5af8-140">The following configuration file disables background garbage collection:</span></span>

```xml
<configuration>
   <runtime>
      <gcConcurrent enabled="false"/>
   </runtime>
</configuration>
```

<span data-ttu-id="e5af8-141">Makine yapılandırma dosyasında **gcConcurrentSetting** ayarı varsa, tüm .NET Framework uygulamaları için varsayılan değeri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e5af8-141">If there's a **gcConcurrentSetting** setting in the machine configuration file, it defines the default value for all .NET Framework applications.</span></span> <span data-ttu-id="e5af8-142">Makine yapılandırma dosyası ayarı uygulama yapılandırma dosya ayarını geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="e5af8-142">The machine configuration file setting overrides the application configuration file setting.</span></span>

<span data-ttu-id="e5af8-143">Eşzamanlı ve arka plan çöp toplama hakkında daha fazla bilgi için [bkz.](../../../../standard/garbage-collection/background-gc.md)</span><span class="sxs-lookup"><span data-stu-id="e5af8-143">For more information on concurrent and background garbage collection, see [Background garbage collection](../../../../standard/garbage-collection/background-gc.md).</span></span>

## <a name="example"></a><span data-ttu-id="e5af8-144">Örnek</span><span class="sxs-lookup"><span data-stu-id="e5af8-144">Example</span></span>

<span data-ttu-id="e5af8-145">Aşağıdaki örnek, arka plan çöp toplama sağlar:</span><span class="sxs-lookup"><span data-stu-id="e5af8-145">The following example enables background garbage collection:</span></span>

```xml
<configuration>
   <runtime>
      <gcConcurrent enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="e5af8-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e5af8-146">See also</span></span>

- [<span data-ttu-id="e5af8-147">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="e5af8-147">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="e5af8-148">Yapılandırma Dosya Şema</span><span class="sxs-lookup"><span data-stu-id="e5af8-148">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="e5af8-149">Atık Toplamanın Temelleri</span><span class="sxs-lookup"><span data-stu-id="e5af8-149">Fundamentals of Garbage Collection</span></span>](../../../../standard/garbage-collection/fundamentals.md)
