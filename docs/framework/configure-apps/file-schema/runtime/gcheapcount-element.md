---
title: GCHeapCount öğesi
ms.date: 11/08/2019
helpviewer_keywords:
- gcHeapCount element
- <gcHeapCount> element
ms.openlocfilehash: 3d6cac4185af182758cb82e6bfd9d96ed24869b4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283077"
---
# <a name="gcheapcount-element"></a><span data-ttu-id="e36c3-102">\<GCHeapCount > öğesi</span><span class="sxs-lookup"><span data-stu-id="e36c3-102">\<GCHeapCount> element</span></span>

<span data-ttu-id="e36c3-103">Sunucu atık toplama için kullanılacak Heap/iş parçacığı sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e36c3-103">Specifies the number of heaps/threads to use for server garbage collection.</span></span>

<span data-ttu-id="e36c3-104">\<Yapılandırma > </span><span class="sxs-lookup"><span data-stu-id="e36c3-104">\<configuration></span></span>\
<span data-ttu-id="e36c3-105">&nbsp;&nbsp;\<çalışma zamanı > </span><span class="sxs-lookup"><span data-stu-id="e36c3-105">&nbsp;&nbsp;\<runtime></span></span>\
<span data-ttu-id="e36c3-106">&nbsp;&nbsp;&nbsp;&nbsp;\<GCHeapCount ></span><span class="sxs-lookup"><span data-stu-id="e36c3-106">&nbsp;&nbsp;&nbsp;&nbsp;\<GCHeapCount></span></span>

## <a name="syntax"></a><span data-ttu-id="e36c3-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e36c3-107">Syntax</span></span>

```xml
<GCHeapCount
   enabled="nn"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e36c3-108">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="e36c3-108">Attributes and elements</span></span>

<span data-ttu-id="e36c3-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e36c3-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="e36c3-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e36c3-110">Attributes</span></span>

|<span data-ttu-id="e36c3-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e36c3-111">Attribute</span></span>|<span data-ttu-id="e36c3-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e36c3-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="e36c3-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="e36c3-113">Required attribute.</span></span><br /><br /><span data-ttu-id="e36c3-114">Sunucu çöp toplama için kullanılacak Heap sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e36c3-114">Specifies the number of heaps to use for server garbage collection.</span></span> <span data-ttu-id="e36c3-115">Heap sayısının gerçek sayısı, belirttiğiniz yığınlara ve işleminizin izin verilen işlemci sayısına göre en düşük gerekliliktir.</span><span class="sxs-lookup"><span data-stu-id="e36c3-115">The actual number of heaps is the minimum of the number of heaps you specify and the number of processors your process is allowed to use.</span></span> |

#### <a name="enabled-attribute"></a><span data-ttu-id="e36c3-116">enabled özniteliği</span><span class="sxs-lookup"><span data-stu-id="e36c3-116">enabled attribute</span></span>

|<span data-ttu-id="e36c3-117">Değer</span><span class="sxs-lookup"><span data-stu-id="e36c3-117">Value</span></span>|<span data-ttu-id="e36c3-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e36c3-118">Description</span></span>|
|-----------|-----------------|
|`nn`|<span data-ttu-id="e36c3-119">Sunucu GC için kullanılacak Heap sayısı.</span><span class="sxs-lookup"><span data-stu-id="e36c3-119">The number of heaps to use for server GC.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="e36c3-120">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="e36c3-120">Child elements</span></span>

<span data-ttu-id="e36c3-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="e36c3-121">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e36c3-122">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="e36c3-122">Parent elements</span></span>

|<span data-ttu-id="e36c3-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="e36c3-123">Element</span></span>|<span data-ttu-id="e36c3-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e36c3-124">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="e36c3-125">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="e36c3-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="e36c3-126">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="e36c3-126">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e36c3-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e36c3-127">Remarks</span></span>

<span data-ttu-id="e36c3-128">Varsayılan olarak, sunucu GC iş parçacıkları, her işlemci için bir GC yığını, bir sunucu GC iş parçacığı ve bir arka plan sunucusu GC iş parçacığı olmak üzere kendi CPU 'SU ile sabit olarak belirlenir.</span><span class="sxs-lookup"><span data-stu-id="e36c3-128">By default, server GC threads are hard-affinitized with their respective CPU so that there is one GC heap, one server GC thread, and one background server GC thread for each processor.</span></span> <span data-ttu-id="e36c3-129">.NET Framework 4.6.2 ' den başlayarak, **Gcheapcount** öğesini kullanarak, uygulamanız tarafından sunucu GC için kullanılan yığınlarınızın sayısını sınırlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e36c3-129">Starting with .NET Framework 4.6.2, you can use the **GCHeapCount** element to limit the number of heaps used by your application for server GC.</span></span> <span data-ttu-id="e36c3-130">Sunucu GC için kullanılan Heap sayısını kısıtlamak, özellikle bir sunucu uygulamasının birden çok örneğini çalıştıran sistemler için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="e36c3-130">Limiting the number of heaps used for server GC is particularly useful for systems that run multiple instances of a server application.</span></span>

<span data-ttu-id="e36c3-131">**Gcheapcount** genellikle iki diğer bayraklı birlikte kullanılır:</span><span class="sxs-lookup"><span data-stu-id="e36c3-131">**GCHeapCount** is typically used along with two other flags:</span></span>

- <span data-ttu-id="e36c3-132">[GCNoAffinitize](gcnoaffinitize-element.md), sunucu GC iş parçacıklarının/yığınların CPU 'lara uygulanıp gösterilmeyeceğini denetler.</span><span class="sxs-lookup"><span data-stu-id="e36c3-132">[GCNoAffinitize](gcnoaffinitize-element.md), which controls whether server GC threads/heaps are affinitized with CPUs.</span></span>

- <span data-ttu-id="e36c3-133">[Gcheapaffinitizemask](gcheapaffinitizemask-element.md), bu, CPU 'larla GC iş parçacıklarının/yığınların benzeşimini denetler.</span><span class="sxs-lookup"><span data-stu-id="e36c3-133">[GCHeapAffinitizeMask](gcheapaffinitizemask-element.md), which controls the affinity of GC threads/heaps with CPUs.</span></span>

<span data-ttu-id="e36c3-134">**Gcheapcount** ayarlanır ve **GCNoAffinitize** devre dışıysa (varsayılan ayarı), *nn* GC iş parçacıkları/heçileri ve ilk *nn* işlemci arasında bir benzeşim vardır.</span><span class="sxs-lookup"><span data-stu-id="e36c3-134">If **GCHeapCount** is set and **GCNoAffinitize** is disabled (its default setting), there is an affinity between the *nn* GC threads/heaps and the first *nn* processors.</span></span> <span data-ttu-id="e36c3-135">İşlemin sunucu GC yığınlarında hangi işlemcilerin kullanıldığını belirtmek için **Gcheapaffinitizemask** öğesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e36c3-135">You can use the **GCHeapAffinitizeMask** element to specify which processors are used by the process's server GC heaps.</span></span> <span data-ttu-id="e36c3-136">Aksi halde, bir sistemde birden çok sunucu işlemi çalışıyorsa, işlemci kullanımı çakışacaktır.</span><span class="sxs-lookup"><span data-stu-id="e36c3-136">Otherwise, if multiple server processes are running on a system, their processor usage will overlap.</span></span>

<span data-ttu-id="e36c3-137">**Gcheapcount** ayarlanır ve **GCNoAffinitize** etkinleştirilmişse, atık toplayıcı sunucu GC için kullanılan işlemcilerin SAYıSıNı sınırlar, ancak GC yığınlarını ve işlemcileri göstermez.</span><span class="sxs-lookup"><span data-stu-id="e36c3-137">If **GCHeapCount** is set and **GCNoAffinitize** is enabled, the garbage collector limits the number of processors used for server GC but does not affinitize GC heaps and processors.</span></span>

## <a name="example"></a><span data-ttu-id="e36c3-138">Örnek</span><span class="sxs-lookup"><span data-stu-id="e36c3-138">Example</span></span>

<span data-ttu-id="e36c3-139">Aşağıdaki örnek, bir uygulamanın 10 Heap/iş parçacığı ile sunucu GC kullandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e36c3-139">The following example indicates that an application uses server GC with 10 heaps/threads.</span></span> <span data-ttu-id="e36c3-140">Bu yığınların sistemde çalışan diğer uygulamalardan Heap 'lerle örtüşmesini istemediğiniz için, işlemin 0 ile 9 arasında CPU kullanması gerektiğini belirtmek için **Gcheapaffinitizemask** kullanın.</span><span class="sxs-lookup"><span data-stu-id="e36c3-140">Since you don't want those heaps to overlap with heaps from other applications running on the system, you use the **GCHeapAffinitizeMask** to specify that the process should use CPUs 0 through 9.</span></span>

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
      <GCHeapCount enabled="10"/>
      <GCHeapAffinitizeMask enabled="1023"/>
   </runtime>
</configuration>
```

<span data-ttu-id="e36c3-141">Aşağıdaki örnek, sunucu GC iş parçacıklarını göstermez ve GC Heap/iş parçacığı sayısını 10 ' a kısıtlar.</span><span class="sxs-lookup"><span data-stu-id="e36c3-141">The following example does not affinitize server GC threads and limits the number of GC heaps/threads to 10.</span></span>

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
      <GCHeapCount enabled="10"/>
      <GCNoAffinitize enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="e36c3-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e36c3-142">See also</span></span>

- <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>
- [<span data-ttu-id="e36c3-143">GCNoAffinitize öğesi</span><span class="sxs-lookup"><span data-stu-id="e36c3-143">GCNoAffinitize element</span></span>](gcnoaffinitize-element.md)
- [<span data-ttu-id="e36c3-144">GCHeapAffinitizeMask öğesi</span><span class="sxs-lookup"><span data-stu-id="e36c3-144">GCHeapAffinitizeMask element</span></span>](gcheapaffinitizemask-element.md)
- [<span data-ttu-id="e36c3-145">Çöp toplamanın temelleri</span><span class="sxs-lookup"><span data-stu-id="e36c3-145">Fundamentals of garbage collection</span></span>](../../../../standard/garbage-collection/fundamentals.md)
- [<span data-ttu-id="e36c3-146">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="e36c3-146">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="e36c3-147">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="e36c3-147">Configuration File Schema</span></span>](../index.md)
