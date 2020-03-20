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
ms.openlocfilehash: 5957337aa960a0d5f445249b410dbfaddb7b08e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400045"
---
# <a name="gcconcurrent-element"></a><span data-ttu-id="bdd11-102">\<gcEşzamanlı> elemanı</span><span class="sxs-lookup"><span data-stu-id="bdd11-102">\<gcConcurrent> element</span></span>

<span data-ttu-id="bdd11-103">Ortak dil çalışma zamanının çöp toplamayı ayrı bir iş parçacığı üzerinde çalıştırıp çalıştırmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="bdd11-103">Specifies whether the common language runtime runs garbage collection on a separate thread.</span></span>

<span data-ttu-id="bdd11-104">[\<yapılandırma>](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="bdd11-104">[\<configuration>](../configuration-element.md)</span></span>\
<span data-ttu-id="bdd11-105">&nbsp;&nbsp;[\<çalışma zamanı>](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="bdd11-105">&nbsp;&nbsp;[\<runtime>](runtime-element.md)</span></span>\
<span data-ttu-id="bdd11-106">&nbsp;&nbsp;&nbsp;&nbsp;\<gcEşzamanlı></span><span class="sxs-lookup"><span data-stu-id="bdd11-106">&nbsp;&nbsp;&nbsp;&nbsp;\<gcConcurrent></span></span>

## <a name="syntax"></a><span data-ttu-id="bdd11-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bdd11-107">Syntax</span></span>

```xml
<gcConcurrent
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="bdd11-108">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="bdd11-108">Attributes and elements</span></span>

<span data-ttu-id="bdd11-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="bdd11-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="bdd11-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="bdd11-110">Attributes</span></span>

|<span data-ttu-id="bdd11-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="bdd11-111">Attribute</span></span>|<span data-ttu-id="bdd11-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bdd11-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="bdd11-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="bdd11-113">Required attribute.</span></span><br /><br /><span data-ttu-id="bdd11-114">Çalışma zamanının çöp toplamayı aynı anda çalıştırıp çalıştırmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="bdd11-114">Specifies whether the runtime runs garbage collection concurrently.</span></span>|

#### <a name="enabled-attribute"></a><span data-ttu-id="bdd11-115">etkin öznitelik</span><span class="sxs-lookup"><span data-stu-id="bdd11-115">enabled attribute</span></span>

|<span data-ttu-id="bdd11-116">Değer</span><span class="sxs-lookup"><span data-stu-id="bdd11-116">Value</span></span>|<span data-ttu-id="bdd11-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bdd11-117">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="bdd11-118">Çöp toplamayı aynı anda çalıştırmıyor.</span><span class="sxs-lookup"><span data-stu-id="bdd11-118">Doesn't run garbage collection concurrently.</span></span>|
|`true`|<span data-ttu-id="bdd11-119">Çöp toplamayı aynı anda çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="bdd11-119">Runs garbage collection concurrently.</span></span> <span data-ttu-id="bdd11-120">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="bdd11-120">This is the default.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="bdd11-121">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="bdd11-121">Child elements</span></span>

<span data-ttu-id="bdd11-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="bdd11-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="bdd11-123">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="bdd11-123">Parent elements</span></span>

|<span data-ttu-id="bdd11-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="bdd11-124">Element</span></span>|<span data-ttu-id="bdd11-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bdd11-125">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="bdd11-126">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="bdd11-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="bdd11-127">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="bdd11-127">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="bdd11-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bdd11-128">Remarks</span></span>

<span data-ttu-id="bdd11-129">.NET Framework 4'ten önce, iş istasyonu çöp toplama, arka planda ayrı bir iş parçacığı üzerinde çöp toplama işlemini gerçekleştiren eşzamanlı çöp toplamayı destekler.</span><span class="sxs-lookup"><span data-stu-id="bdd11-129">Prior to .NET Framework 4, workstation garbage collection supported concurrent garbage collection, which performed garbage collection in the background on a separate thread.</span></span> <span data-ttu-id="bdd11-130">.NET Framework 4'te, eşzamanlı çöp toplama, arka planda ayrı bir iş parçacığı üzerinde çöp toplama da gerçekleştiren arka plan GC ile değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="bdd11-130">In .NET Framework 4, concurrent garbage collection was replaced by background GC, which also performs garbage collection in the background on a separate thread.</span></span> <span data-ttu-id="bdd11-131">.NET Framework 4.5 ile başlayarak, arka plan koleksiyonu sunucu çöp toplama kullanılabilir hale geldi.</span><span class="sxs-lookup"><span data-stu-id="bdd11-131">Starting with .NET Framework 4.5, background collection became available in server garbage collection.</span></span> <span data-ttu-id="bdd11-132">**gcConcurrent** öğesi, çalışma zamanının eşzamanlı veya arka plan çöp toplama gerçekleştirip gerçekleştirmediğini, kullanılabilir olup olmadığını veya ön planda çöp toplama yı gerçekleştirip gerçekleştirmediğini denetler.</span><span class="sxs-lookup"><span data-stu-id="bdd11-132">The **gcConcurrent** element controls whether the runtime performs either concurrent or background garbage collection, if it's available, or whether it performs garbage collection in the foreground.</span></span>

### <a name="to-disable-background-garbage-collection"></a><span data-ttu-id="bdd11-133">Arka plan çöp koleksiyonunu devre dışı atmak için</span><span class="sxs-lookup"><span data-stu-id="bdd11-133">To disable background garbage collection</span></span>

> [!WARNING]
> <span data-ttu-id="bdd11-134">.NET Framework 4 ile başlayarak, eşzamanlı çöp toplama arka plan çöp toplama ile değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="bdd11-134">Starting with .NET Framework 4, concurrent garbage collection is replaced by background garbage collection.</span></span> <span data-ttu-id="bdd11-135">*Eşzamanlı* ve *arka plan* terimleri .NET Framework belgelerinde birbirinin yerine kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bdd11-135">The terms *concurrent* and *background* are used interchangeably in the .NET Framework documentation.</span></span> <span data-ttu-id="bdd11-136">Arka plan çöp koleksiyonunu devre dışı katmak için, bu makalede belirtildiği gibi **gcConcurrent** öğesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="bdd11-136">To disable background garbage collection, use the **gcConcurrent** element, as discussed in this article.</span></span>

<span data-ttu-id="bdd11-137">Varsayılan olarak, çalışma süresi gecikme süresi için en iyi duruma getirilmiş eşzamanlı veya arka plan çöp toplama kullanır.</span><span class="sxs-lookup"><span data-stu-id="bdd11-137">By default, the runtime uses concurrent or background garbage collection, which is optimized for latency.</span></span> <span data-ttu-id="bdd11-138">Uygulamanız ağır kullanıcı etkileşimi içeriyorsa, eşzamanlı çöp toplamayı, uygulamanın çöp toplama gerçekleştirme süresini en aza indirmek için etkin bırakın.</span><span class="sxs-lookup"><span data-stu-id="bdd11-138">If your application involves heavy user interaction, leave concurrent garbage collection enabled to minimize the application's pause time to perform garbage collection.</span></span> <span data-ttu-id="bdd11-139">`enabled` **GcConcurrent** öğesinin özniteliğini `false`, çalışma zamanı, iş için en iyi duruma getirilmiş eşzamanlı olmayan çöp toplama yı kullanır.</span><span class="sxs-lookup"><span data-stu-id="bdd11-139">If you set the `enabled` attribute of the **gcConcurrent** element to `false`, the runtime uses non-concurrent garbage collection, which is optimized for throughput.</span></span>

<span data-ttu-id="bdd11-140">Aşağıdaki yapılandırma dosyası arka plan çöp toplama devre dışı kalmaktadır:</span><span class="sxs-lookup"><span data-stu-id="bdd11-140">The following configuration file disables background garbage collection:</span></span>

```xml
<configuration>
   <runtime>
      <gcConcurrent enabled="false"/>
   </runtime>
</configuration>
```

<span data-ttu-id="bdd11-141">Makine yapılandırma dosyasında **gcConcurrentSetting** ayarı varsa, tüm .NET Framework uygulamaları için varsayılan değeri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="bdd11-141">If there's a **gcConcurrentSetting** setting in the machine configuration file, it defines the default value for all .NET Framework applications.</span></span> <span data-ttu-id="bdd11-142">Makine yapılandırma dosyası ayarı uygulama yapılandırma dosya ayarını geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="bdd11-142">The machine configuration file setting overrides the application configuration file setting.</span></span>

<span data-ttu-id="bdd11-143">Eşzamanlı ve arka plan çöp toplama hakkında daha fazla bilgi için, [Eşzamanlı çöp toplama,](../../../../standard/garbage-collection/fundamentals.md#concurrent-garbage-collection) [Arka plan iş istasyonu çöp toplama](../../../../standard/garbage-collection/fundamentals.md#background-workstation-garbage-collection)ve Çöp Toplama [makalesinin Temelleri'ndeki](../../../../standard/garbage-collection/fundamentals.md) [Arka plan sunucusu çöp toplama](../../../../standard/garbage-collection/fundamentals.md#background-server-garbage-collection) bölümlerine bakın.</span><span class="sxs-lookup"><span data-stu-id="bdd11-143">For more information on concurrent and background garbage collection, see the [Concurrent garbage collection](../../../../standard/garbage-collection/fundamentals.md#concurrent-garbage-collection), [Background workstation garbage collection](../../../../standard/garbage-collection/fundamentals.md#background-workstation-garbage-collection), and [Background server garbage collection](../../../../standard/garbage-collection/fundamentals.md#background-server-garbage-collection) sections in the [Fundamentals of Garbage Collection](../../../../standard/garbage-collection/fundamentals.md) article.</span></span>

## <a name="example"></a><span data-ttu-id="bdd11-144">Örnek</span><span class="sxs-lookup"><span data-stu-id="bdd11-144">Example</span></span>

<span data-ttu-id="bdd11-145">Aşağıdaki örnek, arka plan çöp toplama sağlar:</span><span class="sxs-lookup"><span data-stu-id="bdd11-145">The following example enables background garbage collection:</span></span>

```xml
<configuration>
   <runtime>
      <gcConcurrent enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="bdd11-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bdd11-146">See also</span></span>

- [<span data-ttu-id="bdd11-147">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="bdd11-147">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="bdd11-148">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="bdd11-148">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="bdd11-149">Atık Toplamanın Temelleri</span><span class="sxs-lookup"><span data-stu-id="bdd11-149">Fundamentals of Garbage Collection</span></span>](../../../../standard/garbage-collection/fundamentals.md)
