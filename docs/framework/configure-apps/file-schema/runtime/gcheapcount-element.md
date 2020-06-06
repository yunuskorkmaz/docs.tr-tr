---
title: GCHeapCount öğesi
ms.date: 11/08/2019
helpviewer_keywords:
- gcHeapCount element
- <gcHeapCount> element
ms.openlocfilehash: 3d6cac4185af182758cb82e6bfd9d96ed24869b4
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "74283077"
---
# <a name="gcheapcount-element"></a><span data-ttu-id="70045-102">\<GCHeapCount> öğesi</span><span class="sxs-lookup"><span data-stu-id="70045-102">\<GCHeapCount> element</span></span>

<span data-ttu-id="70045-103">Sunucu atık toplama için kullanılacak Heap/iş parçacığı sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="70045-103">Specifies the number of heaps/threads to use for server garbage collection.</span></span>

\<configuration>\
&nbsp;&nbsp;\<runtime>\
&nbsp;&nbsp;&nbsp;&nbsp;\<GCHeapCount>

## <a name="syntax"></a><span data-ttu-id="70045-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="70045-104">Syntax</span></span>

```xml
<GCHeapCount
   enabled="nn"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="70045-105">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="70045-105">Attributes and elements</span></span>

<span data-ttu-id="70045-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="70045-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="70045-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="70045-107">Attributes</span></span>

|<span data-ttu-id="70045-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="70045-108">Attribute</span></span>|<span data-ttu-id="70045-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="70045-109">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="70045-110">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="70045-110">Required attribute.</span></span><br /><br /><span data-ttu-id="70045-111">Sunucu çöp toplama için kullanılacak Heap sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="70045-111">Specifies the number of heaps to use for server garbage collection.</span></span> <span data-ttu-id="70045-112">Heap sayısının gerçek sayısı, belirttiğiniz yığınlara ve işleminizin izin verilen işlemci sayısına göre en düşük gerekliliktir.</span><span class="sxs-lookup"><span data-stu-id="70045-112">The actual number of heaps is the minimum of the number of heaps you specify and the number of processors your process is allowed to use.</span></span> |

#### <a name="enabled-attribute"></a><span data-ttu-id="70045-113">enabled özniteliği</span><span class="sxs-lookup"><span data-stu-id="70045-113">enabled attribute</span></span>

|<span data-ttu-id="70045-114">Değer</span><span class="sxs-lookup"><span data-stu-id="70045-114">Value</span></span>|<span data-ttu-id="70045-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="70045-115">Description</span></span>|
|-----------|-----------------|
|`nn`|<span data-ttu-id="70045-116">Sunucu GC için kullanılacak Heap sayısı.</span><span class="sxs-lookup"><span data-stu-id="70045-116">The number of heaps to use for server GC.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="70045-117">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="70045-117">Child elements</span></span>

<span data-ttu-id="70045-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="70045-118">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="70045-119">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="70045-119">Parent elements</span></span>

|<span data-ttu-id="70045-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="70045-120">Element</span></span>|<span data-ttu-id="70045-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="70045-121">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="70045-122">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="70045-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="70045-123">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="70045-123">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="70045-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="70045-124">Remarks</span></span>

<span data-ttu-id="70045-125">Varsayılan olarak, sunucu GC iş parçacıkları, her işlemci için bir GC yığını, bir sunucu GC iş parçacığı ve bir arka plan sunucusu GC iş parçacığı olmak üzere kendi CPU 'SU ile sabit olarak belirlenir.</span><span class="sxs-lookup"><span data-stu-id="70045-125">By default, server GC threads are hard-affinitized with their respective CPU so that there is one GC heap, one server GC thread, and one background server GC thread for each processor.</span></span> <span data-ttu-id="70045-126">.NET Framework 4.6.2 ' den başlayarak, **Gcheapcount** öğesini kullanarak, uygulamanız tarafından sunucu GC için kullanılan yığınlarınızın sayısını sınırlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="70045-126">Starting with .NET Framework 4.6.2, you can use the **GCHeapCount** element to limit the number of heaps used by your application for server GC.</span></span> <span data-ttu-id="70045-127">Sunucu GC için kullanılan Heap sayısını kısıtlamak, özellikle bir sunucu uygulamasının birden çok örneğini çalıştıran sistemler için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="70045-127">Limiting the number of heaps used for server GC is particularly useful for systems that run multiple instances of a server application.</span></span>

<span data-ttu-id="70045-128">**Gcheapcount** genellikle iki diğer bayraklı birlikte kullanılır:</span><span class="sxs-lookup"><span data-stu-id="70045-128">**GCHeapCount** is typically used along with two other flags:</span></span>

- <span data-ttu-id="70045-129">[GCNoAffinitize](gcnoaffinitize-element.md), sunucu GC iş parçacıklarının/yığınların CPU 'lara uygulanıp gösterilmeyeceğini denetler.</span><span class="sxs-lookup"><span data-stu-id="70045-129">[GCNoAffinitize](gcnoaffinitize-element.md), which controls whether server GC threads/heaps are affinitized with CPUs.</span></span>

- <span data-ttu-id="70045-130">[Gcheapaffinitizemask](gcheapaffinitizemask-element.md), bu, CPU 'larla GC iş parçacıklarının/yığınların benzeşimini denetler.</span><span class="sxs-lookup"><span data-stu-id="70045-130">[GCHeapAffinitizeMask](gcheapaffinitizemask-element.md), which controls the affinity of GC threads/heaps with CPUs.</span></span>

<span data-ttu-id="70045-131">**Gcheapcount** ayarlanır ve **GCNoAffinitize** devre dışıysa (varsayılan ayarı), *nn* GC iş parçacıkları/heçileri ve ilk *nn* işlemci arasında bir benzeşim vardır.</span><span class="sxs-lookup"><span data-stu-id="70045-131">If **GCHeapCount** is set and **GCNoAffinitize** is disabled (its default setting), there is an affinity between the *nn* GC threads/heaps and the first *nn* processors.</span></span> <span data-ttu-id="70045-132">İşlemin sunucu GC yığınlarında hangi işlemcilerin kullanıldığını belirtmek için **Gcheapaffinitizemask** öğesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="70045-132">You can use the **GCHeapAffinitizeMask** element to specify which processors are used by the process's server GC heaps.</span></span> <span data-ttu-id="70045-133">Aksi halde, bir sistemde birden çok sunucu işlemi çalışıyorsa, işlemci kullanımı çakışacaktır.</span><span class="sxs-lookup"><span data-stu-id="70045-133">Otherwise, if multiple server processes are running on a system, their processor usage will overlap.</span></span>

<span data-ttu-id="70045-134">**Gcheapcount** ayarlanır ve **GCNoAffinitize** etkinleştirilmişse, atık toplayıcı sunucu GC için kullanılan işlemcilerin SAYıSıNı sınırlar, ancak GC yığınlarını ve işlemcileri göstermez.</span><span class="sxs-lookup"><span data-stu-id="70045-134">If **GCHeapCount** is set and **GCNoAffinitize** is enabled, the garbage collector limits the number of processors used for server GC but does not affinitize GC heaps and processors.</span></span>

## <a name="example"></a><span data-ttu-id="70045-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="70045-135">Example</span></span>

<span data-ttu-id="70045-136">Aşağıdaki örnek, bir uygulamanın 10 Heap/iş parçacığı ile sunucu GC kullandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="70045-136">The following example indicates that an application uses server GC with 10 heaps/threads.</span></span> <span data-ttu-id="70045-137">Bu yığınların sistemde çalışan diğer uygulamalardan Heap 'lerle örtüşmesini istemediğiniz için, işlemin 0 ile 9 arasında CPU kullanması gerektiğini belirtmek için **Gcheapaffinitizemask** kullanın.</span><span class="sxs-lookup"><span data-stu-id="70045-137">Since you don't want those heaps to overlap with heaps from other applications running on the system, you use the **GCHeapAffinitizeMask** to specify that the process should use CPUs 0 through 9.</span></span>

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
      <GCHeapCount enabled="10"/>
      <GCHeapAffinitizeMask enabled="1023"/>
   </runtime>
</configuration>
```

<span data-ttu-id="70045-138">Aşağıdaki örnek, sunucu GC iş parçacıklarını göstermez ve GC Heap/iş parçacığı sayısını 10 ' a kısıtlar.</span><span class="sxs-lookup"><span data-stu-id="70045-138">The following example does not affinitize server GC threads and limits the number of GC heaps/threads to 10.</span></span>

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
      <GCHeapCount enabled="10"/>
      <GCNoAffinitize enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="70045-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="70045-139">See also</span></span>

- <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>
- [<span data-ttu-id="70045-140">GCNoAffinitize öğesi</span><span class="sxs-lookup"><span data-stu-id="70045-140">GCNoAffinitize element</span></span>](gcnoaffinitize-element.md)
- [<span data-ttu-id="70045-141">GCHeapAffinitizeMask öğesi</span><span class="sxs-lookup"><span data-stu-id="70045-141">GCHeapAffinitizeMask element</span></span>](gcheapaffinitizemask-element.md)
- [<span data-ttu-id="70045-142">Çöp toplamanın temelleri</span><span class="sxs-lookup"><span data-stu-id="70045-142">Fundamentals of garbage collection</span></span>](../../../../standard/garbage-collection/fundamentals.md)
- [<span data-ttu-id="70045-143">Çalışma zamanı ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="70045-143">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="70045-144">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="70045-144">Configuration File Schema</span></span>](../index.md)
