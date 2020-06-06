---
title: gcServer öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/gcServer
- http://schemas.microsoft.com/.NetConfiguration/v2.0#gcServer
helpviewer_keywords:
- gcServer element
- <gcServer> element
ms.assetid: 8d25b80e-2581-4803-bd87-a59528e3cb03
ms.openlocfilehash: 8eab5e36bab90510aff4f1a3e15328197ac59ed7
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73968942"
---
# <a name="gcserver-element"></a><span data-ttu-id="75031-102">\<gcServer> öğesi</span><span class="sxs-lookup"><span data-stu-id="75031-102">\<gcServer> element</span></span>

<span data-ttu-id="75031-103">Ortak dil çalışma zamanının sunucu çöp toplamayı çalıştırmasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="75031-103">Specifies whether the common language runtime runs server garbage collection.</span></span>

[\<configuration>](../configuration-element.md)\
&nbsp;&nbsp;[\<runtime>](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;\<gcServer>

## <a name="syntax"></a><span data-ttu-id="75031-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="75031-104">Syntax</span></span>

```xml
<gcServer
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="75031-105">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="75031-105">Attributes and elements</span></span>

<span data-ttu-id="75031-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="75031-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="75031-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="75031-107">Attributes</span></span>

|<span data-ttu-id="75031-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="75031-108">Attribute</span></span>|<span data-ttu-id="75031-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="75031-109">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="75031-110">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="75031-110">Required attribute.</span></span><br /><br /><span data-ttu-id="75031-111">Çalışma zamanının sunucu çöp toplamayı çalıştırmasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="75031-111">Specifies whether the runtime runs server garbage collection.</span></span>|

#### <a name="enabled-attribute"></a><span data-ttu-id="75031-112">enabled özniteliği</span><span class="sxs-lookup"><span data-stu-id="75031-112">enabled attribute</span></span>

|<span data-ttu-id="75031-113">Değer</span><span class="sxs-lookup"><span data-stu-id="75031-113">Value</span></span>|<span data-ttu-id="75031-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="75031-114">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="75031-115">Sunucu çöp toplamayı çalıştırmaz.</span><span class="sxs-lookup"><span data-stu-id="75031-115">Does not run server garbage collection.</span></span> <span data-ttu-id="75031-116">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="75031-116">This is the default.</span></span>|
|`true`|<span data-ttu-id="75031-117">Sunucu çöp toplamayı çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="75031-117">Runs server garbage collection.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="75031-118">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="75031-118">Child elements</span></span>

<span data-ttu-id="75031-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="75031-119">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="75031-120">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="75031-120">Parent elements</span></span>

|<span data-ttu-id="75031-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="75031-121">Element</span></span>|<span data-ttu-id="75031-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="75031-122">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="75031-123">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="75031-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="75031-124">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="75031-124">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="75031-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="75031-125">Remarks</span></span>

<span data-ttu-id="75031-126">Ortak dil çalışma zamanı (CLR) iki tür çöp toplamayı destekler: tüm sistemlerde kullanılabilen iş istasyonu çöp toplama ve çok işlemcili sistemlerde bulunan sunucu çöp toplama.</span><span class="sxs-lookup"><span data-stu-id="75031-126">The common language runtime (CLR) supports two types of garbage collection: workstation garbage collection, which is available on all systems, and server garbage collection, which is available on multiprocessor systems.</span></span> <span data-ttu-id="75031-127">CLR 'nin gerçekleştirdiği çöp toplamanın türünü denetlemek için **gcServer** öğesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="75031-127">Use the **gcServer** element to control the type of garbage collection the CLR performs.</span></span> <span data-ttu-id="75031-128"><xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>Sunucu çöp toplamanın etkinleştirilip etkinleştirilmediğini anlamak için özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="75031-128">Use the <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType> property to determine if server garbage collection is enabled.</span></span>

<span data-ttu-id="75031-129">Tek işlemcili bilgisayarlar için varsayılan iş istasyonu atık toplama en hızlı seçenek olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="75031-129">For single-processor computers, the default workstation garbage collection should be the fastest option.</span></span> <span data-ttu-id="75031-130">İki işlemcili bilgisayarlar için iş istasyonu veya sunucu kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="75031-130">Either workstation or server can be used for two-processor computers.</span></span> <span data-ttu-id="75031-131">Sunucu çöp toplama, ikiden fazla işlemci için en hızlı seçenek olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="75031-131">Server garbage collection should be the fastest option for more than two processors.</span></span> <span data-ttu-id="75031-132">En yaygın olarak, çok işlemcili sunucu sistemleri sunucu GC 'yi devre dışı bırakır ve bir sunucu uygulamasının birçok örneği aynı makinede çalıştığında bunun yerine Workstation GC kullanır.</span><span class="sxs-lookup"><span data-stu-id="75031-132">Most commonly, multiprocessor server systems disable server GC and use workstation GC instead when many instances of a server app run on the same machine.</span></span>

<span data-ttu-id="75031-133">Bu öğe yalnızca uygulama yapılandırma dosyasında kullanılabilir; makine yapılandırma dosyasında ise yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="75031-133">This element can be used only in the application configuration file; it is ignored if it is in the machine configuration file.</span></span>

> [!NOTE]
> <span data-ttu-id="75031-134">.NET Framework 4 ve önceki sürümlerde, sunucu çöp toplama etkinleştirildiğinde eşzamanlı çöp toplama kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="75031-134">In the .NET Framework 4 and earlier versions, concurrent garbage collection is not available when server garbage collection is enabled.</span></span> <span data-ttu-id="75031-135">4,5 .NET Framework başlayarak, sunucu çöp toplama işlemi eşzamanlı olur.</span><span class="sxs-lookup"><span data-stu-id="75031-135">Starting with the .NET Framework 4.5, server garbage collection is concurrent.</span></span> <span data-ttu-id="75031-136">Eş zamanlı olmayan sunucu çöp toplamayı kullanmak için **gcServer** öğesini `true` ve [gcConcurrent öğesini](gcconcurrent-element.md) olarak ayarlayın `false` .</span><span class="sxs-lookup"><span data-stu-id="75031-136">To use non-concurrent server garbage collection, set the **gcServer** element to `true` and the [gcConcurrent element](gcconcurrent-element.md) to `false`.</span></span>

<span data-ttu-id="75031-137">.NET Framework 4.6.2 ile başlayarak, sunucu GC 'yi yapılandırmak için aşağıdaki öğeleri de kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="75031-137">Starting with .NET Framework 4.6.2, you can also use the following elements to configure server GC:</span></span>

- <span data-ttu-id="75031-138">[GCNoAffinitize](gcnoaffinitize-element.md), sunucu GC yığınlarını ve işlemcileri arasında bir benzeşim olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="75031-138">[GCNoAffinitize](gcnoaffinitize-element.md), which specifies whether there is an affinity between server GC heaps and processors.</span></span> <span data-ttu-id="75031-139">Varsayılan olarak, her işlemci için bir sunucu GC yığını vardır.</span><span class="sxs-lookup"><span data-stu-id="75031-139">By default, there is one server GC heap for each processor.</span></span>

- <span data-ttu-id="75031-140">Bir işlem tarafından kullanılan Heap sayısını sınırlayan [Gcheapcount](gcheapcount-element.md).</span><span class="sxs-lookup"><span data-stu-id="75031-140">[GCHeapCount](gcheapcount-element.md), which limits the number of heaps used by a process.</span></span>

- <span data-ttu-id="75031-141">Kullanılabilir sunucu GC yığınlarını ve bireysel işlemcileri arasındaki benzeşimi tanımlayan [Gcheapaffinitizemask](gcheapaffinitizemask-element.md).</span><span class="sxs-lookup"><span data-stu-id="75031-141">[GCHeapAffinitizeMask](gcheapaffinitizemask-element.md), which defines the affinity between the available server GC heaps and individual processors.</span></span>

## <a name="example"></a><span data-ttu-id="75031-142">Örnek</span><span class="sxs-lookup"><span data-stu-id="75031-142">Example</span></span>

<span data-ttu-id="75031-143">Aşağıdaki örnek, sunucu çöp toplamayı mümkün bir şekilde sunar:</span><span class="sxs-lookup"><span data-stu-id="75031-143">The following example enables server garbage collection:</span></span>

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="75031-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="75031-144">See also</span></span>

- <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>
- [<span data-ttu-id="75031-145">Çalışma zamanı ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="75031-145">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="75031-146">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="75031-146">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="75031-147">Eşzamanlı atık toplamayı devre dışı bırakmak için</span><span class="sxs-lookup"><span data-stu-id="75031-147">To disable concurrent garbage collection</span></span>](gcconcurrent-element.md#to-disable-background-garbage-collection)
