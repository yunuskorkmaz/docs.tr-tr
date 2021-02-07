---
description: 'Daha fazla bilgi edinin: <gcServer> öğesi'
title: gcServer öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/gcServer
- http://schemas.microsoft.com/.NetConfiguration/v2.0#gcServer
helpviewer_keywords:
- gcServer element
- <gcServer> element
ms.assetid: 8d25b80e-2581-4803-bd87-a59528e3cb03
ms.openlocfilehash: bed347699786682421292392a8d2449b7aac61d0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754543"
---
# <a name="gcserver-element"></a><span data-ttu-id="e7646-103">\<gcServer> öğesi</span><span class="sxs-lookup"><span data-stu-id="e7646-103">\<gcServer> element</span></span>

<span data-ttu-id="e7646-104">Ortak dil çalışma zamanının sunucu çöp toplamayı çalıştırmasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e7646-104">Specifies whether the common language runtime runs server garbage collection.</span></span>

[\<configuration>](../configuration-element.md)\
&nbsp;&nbsp;[\<runtime>](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;\<gcServer>

## <a name="syntax"></a><span data-ttu-id="e7646-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="e7646-105">Syntax</span></span>

```xml
<gcServer
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e7646-106">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="e7646-106">Attributes and elements</span></span>

<span data-ttu-id="e7646-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e7646-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="e7646-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e7646-108">Attributes</span></span>

|<span data-ttu-id="e7646-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e7646-109">Attribute</span></span>|<span data-ttu-id="e7646-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e7646-110">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="e7646-111">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="e7646-111">Required attribute.</span></span><br /><br /><span data-ttu-id="e7646-112">Çalışma zamanının sunucu çöp toplamayı çalıştırmasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e7646-112">Specifies whether the runtime runs server garbage collection.</span></span>|

#### <a name="enabled-attribute"></a><span data-ttu-id="e7646-113">enabled özniteliği</span><span class="sxs-lookup"><span data-stu-id="e7646-113">enabled attribute</span></span>

|<span data-ttu-id="e7646-114">Değer</span><span class="sxs-lookup"><span data-stu-id="e7646-114">Value</span></span>|<span data-ttu-id="e7646-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e7646-115">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="e7646-116">Sunucu çöp toplamayı çalıştırmaz.</span><span class="sxs-lookup"><span data-stu-id="e7646-116">Does not run server garbage collection.</span></span> <span data-ttu-id="e7646-117">Bu varsayılan seçenektir.</span><span class="sxs-lookup"><span data-stu-id="e7646-117">This is the default.</span></span>|
|`true`|<span data-ttu-id="e7646-118">Sunucu çöp toplamayı çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="e7646-118">Runs server garbage collection.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="e7646-119">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="e7646-119">Child elements</span></span>

<span data-ttu-id="e7646-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="e7646-120">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e7646-121">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="e7646-121">Parent elements</span></span>

|<span data-ttu-id="e7646-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="e7646-122">Element</span></span>|<span data-ttu-id="e7646-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e7646-123">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="e7646-124">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="e7646-124">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="e7646-125">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="e7646-125">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e7646-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e7646-126">Remarks</span></span>

<span data-ttu-id="e7646-127">Ortak dil çalışma zamanı (CLR) iki tür çöp toplamayı destekler: tüm sistemlerde kullanılabilen iş istasyonu çöp toplama ve çok işlemcili sistemlerde bulunan sunucu çöp toplama.</span><span class="sxs-lookup"><span data-stu-id="e7646-127">The common language runtime (CLR) supports two types of garbage collection: workstation garbage collection, which is available on all systems, and server garbage collection, which is available on multiprocessor systems.</span></span> <span data-ttu-id="e7646-128">CLR 'nin gerçekleştirdiği çöp toplamanın türünü denetlemek için **gcServer** öğesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="e7646-128">Use the **gcServer** element to control the type of garbage collection the CLR performs.</span></span> <span data-ttu-id="e7646-129"><xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>Sunucu çöp toplamanın etkinleştirilip etkinleştirilmediğini anlamak için özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="e7646-129">Use the <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType> property to determine if server garbage collection is enabled.</span></span>

<span data-ttu-id="e7646-130">Tek işlemcili bilgisayarlar için varsayılan iş istasyonu atık toplama en hızlı seçenek olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e7646-130">For single-processor computers, the default workstation garbage collection should be the fastest option.</span></span> <span data-ttu-id="e7646-131">İki işlemcili bilgisayarlar için iş istasyonu veya sunucu kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e7646-131">Either workstation or server can be used for two-processor computers.</span></span> <span data-ttu-id="e7646-132">Sunucu çöp toplama, ikiden fazla işlemci için en hızlı seçenek olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e7646-132">Server garbage collection should be the fastest option for more than two processors.</span></span> <span data-ttu-id="e7646-133">En yaygın olarak, çok işlemcili sunucu sistemleri sunucu GC 'yi devre dışı bırakır ve bir sunucu uygulamasının birçok örneği aynı makinede çalıştığında bunun yerine Workstation GC kullanır.</span><span class="sxs-lookup"><span data-stu-id="e7646-133">Most commonly, multiprocessor server systems disable server GC and use workstation GC instead when many instances of a server app run on the same machine.</span></span>

<span data-ttu-id="e7646-134">Bu öğe yalnızca uygulama yapılandırma dosyasında kullanılabilir; makine yapılandırma dosyasında ise yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="e7646-134">This element can be used only in the application configuration file; it is ignored if it is in the machine configuration file.</span></span>

> [!NOTE]
> <span data-ttu-id="e7646-135">.NET Framework 4 ve önceki sürümlerde, sunucu çöp toplama etkinleştirildiğinde eşzamanlı çöp toplama kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="e7646-135">In the .NET Framework 4 and earlier versions, concurrent garbage collection is not available when server garbage collection is enabled.</span></span> <span data-ttu-id="e7646-136">4,5 .NET Framework başlayarak, sunucu çöp toplama işlemi eşzamanlı olur.</span><span class="sxs-lookup"><span data-stu-id="e7646-136">Starting with the .NET Framework 4.5, server garbage collection is concurrent.</span></span> <span data-ttu-id="e7646-137">Eş zamanlı olmayan sunucu çöp toplamayı kullanmak için **gcServer** öğesini `true` ve [gcConcurrent öğesini](gcconcurrent-element.md) olarak ayarlayın `false` .</span><span class="sxs-lookup"><span data-stu-id="e7646-137">To use non-concurrent server garbage collection, set the **gcServer** element to `true` and the [gcConcurrent element](gcconcurrent-element.md) to `false`.</span></span>

<span data-ttu-id="e7646-138">.NET Framework 4.6.2 ile başlayarak, sunucu GC 'yi yapılandırmak için aşağıdaki öğeleri de kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e7646-138">Starting with .NET Framework 4.6.2, you can also use the following elements to configure server GC:</span></span>

- <span data-ttu-id="e7646-139">[GCNoAffinitize](gcnoaffinitize-element.md), sunucu GC yığınlarını ve işlemcileri arasında bir benzeşim olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e7646-139">[GCNoAffinitize](gcnoaffinitize-element.md), which specifies whether there is an affinity between server GC heaps and processors.</span></span> <span data-ttu-id="e7646-140">Varsayılan olarak, her işlemci için bir sunucu GC yığını vardır.</span><span class="sxs-lookup"><span data-stu-id="e7646-140">By default, there is one server GC heap for each processor.</span></span>

- <span data-ttu-id="e7646-141">Bir işlem tarafından kullanılan Heap sayısını sınırlayan [Gcheapcount](gcheapcount-element.md).</span><span class="sxs-lookup"><span data-stu-id="e7646-141">[GCHeapCount](gcheapcount-element.md), which limits the number of heaps used by a process.</span></span>

- <span data-ttu-id="e7646-142">Kullanılabilir sunucu GC yığınlarını ve bireysel işlemcileri arasındaki benzeşimi tanımlayan [Gcheapaffinitizemask](gcheapaffinitizemask-element.md).</span><span class="sxs-lookup"><span data-stu-id="e7646-142">[GCHeapAffinitizeMask](gcheapaffinitizemask-element.md), which defines the affinity between the available server GC heaps and individual processors.</span></span>

## <a name="example"></a><span data-ttu-id="e7646-143">Örnek</span><span class="sxs-lookup"><span data-stu-id="e7646-143">Example</span></span>

<span data-ttu-id="e7646-144">Aşağıdaki örnek, sunucu çöp toplamayı mümkün bir şekilde sunar:</span><span class="sxs-lookup"><span data-stu-id="e7646-144">The following example enables server garbage collection:</span></span>

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="e7646-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e7646-145">See also</span></span>

- <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>
- [<span data-ttu-id="e7646-146">Çalışma zamanı ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="e7646-146">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="e7646-147">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="e7646-147">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="e7646-148">Eşzamanlı atık toplamayı devre dışı bırakmak için</span><span class="sxs-lookup"><span data-stu-id="e7646-148">To disable concurrent garbage collection</span></span>](gcconcurrent-element.md#to-disable-background-garbage-collection)
