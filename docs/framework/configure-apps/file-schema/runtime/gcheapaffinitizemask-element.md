---
title: GCHeapAffinitizeMask öğesi
ms.date: 11/08/2019
helpviewer_keywords:
- gcHeapCount element
- <gcHeapCount> element
ms.openlocfilehash: 09d6523fb10692dd3617a3827d5bccf112bc632b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73978384"
---
# <a name="gcheapaffinitizemask-element"></a><span data-ttu-id="43dde-102">\<GCHeapAffinitizeMask> öğesi</span><span class="sxs-lookup"><span data-stu-id="43dde-102">\<GCHeapAffinitizeMask> element</span></span>

<span data-ttu-id="43dde-103">GC yığınlarını ve bireysel işlemcileri arasındaki benzeşimi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="43dde-103">Defines the affinity between GC heaps and individual processors.</span></span>

\<configuration>\
&nbsp;&nbsp;\<runtime>\
&nbsp;&nbsp;&nbsp;&nbsp;\<GCHeapAffinitizeMask>

## <a name="syntax"></a><span data-ttu-id="43dde-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="43dde-104">Syntax</span></span>

```xml
<GCHeapAffinitizeMask
   enabled="nnnn"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="43dde-105">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="43dde-105">Attributes and elements</span></span>

<span data-ttu-id="43dde-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="43dde-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="43dde-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="43dde-107">Attributes</span></span>

|<span data-ttu-id="43dde-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="43dde-108">Attribute</span></span>|<span data-ttu-id="43dde-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="43dde-109">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="43dde-110">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="43dde-110">Required attribute.</span></span><br /><br /><span data-ttu-id="43dde-111">GC yığınlarını ve tek tek işlemciler arasındaki benzeşimi belirtir.</span><span class="sxs-lookup"><span data-stu-id="43dde-111">Specifies the affinity between GC heaps and individual processors.</span></span> |

#### <a name="enabled-attribute"></a><span data-ttu-id="43dde-112">enabled özniteliği</span><span class="sxs-lookup"><span data-stu-id="43dde-112">enabled attribute</span></span>

|<span data-ttu-id="43dde-113">Değer</span><span class="sxs-lookup"><span data-stu-id="43dde-113">Value</span></span>|<span data-ttu-id="43dde-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="43dde-114">Description</span></span>|
|-----------|-----------------|
|`nnnn`|<span data-ttu-id="43dde-115">Sunucu GC yığınlarını ve bireysel işlemcileri arasındaki benzeşimi tanımlayan bir bit maskesini oluşturan ondalık bir değer.</span><span class="sxs-lookup"><span data-stu-id="43dde-115">A decimal value that forms a bitmask defining the affinity between server GC heaps and individual processors.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="43dde-116">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="43dde-116">Child elements</span></span>

<span data-ttu-id="43dde-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="43dde-117">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="43dde-118">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="43dde-118">Parent elements</span></span>

|<span data-ttu-id="43dde-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="43dde-119">Element</span></span>|<span data-ttu-id="43dde-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="43dde-120">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="43dde-121">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="43dde-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="43dde-122">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="43dde-122">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="43dde-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="43dde-123">Remarks</span></span>

<span data-ttu-id="43dde-124">Varsayılan olarak, sunucu GC iş parçacıkları, her işlemci için bir GC yığını, bir sunucu GC iş parçacığı ve bir arka plan sunucusu GC iş parçacığı olmak üzere kendi CPU 'SU ile sabit olarak belirlenir.</span><span class="sxs-lookup"><span data-stu-id="43dde-124">By default, server GC threads are hard-affinitized with their respective CPU so that there is one GC heap, one server GC thread, and one background server GC thread for each processor.</span></span> <span data-ttu-id="43dde-125">.NET Framework 4.6.2 ile başlayarak, Heap sayısı **Gcheapcount** öğesiyle sınırlı olduğunda, sunucu GC yığınlarını ve işlemcileri arasındaki benzeşimi denetlemek Için **Gcheapaffinitizemask** öğesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="43dde-125">Starting with .NET Framework 4.6.2, you can use the **GCHeapAffinitizeMask** element to control the affinity between server GC heaps and processors when the number of heaps is limited by the **GCHeapCount** element.</span></span>

<span data-ttu-id="43dde-126">**Gcheapaffinitizemask** genellikle iki diğer bayraklı birlikte kullanılır:</span><span class="sxs-lookup"><span data-stu-id="43dde-126">**GCHeapAffinitizeMask** is typically used along with two other flags:</span></span>

- <span data-ttu-id="43dde-127">[GCNoAffinitize](gcnoaffinitize-element.md), sunucu GC iş parçacıklarının/yığınların CPU 'lara uygulanıp gösterilmeyeceğini denetler.</span><span class="sxs-lookup"><span data-stu-id="43dde-127">[GCNoAffinitize](gcnoaffinitize-element.md), which controls whether server GC threads/heaps are affinitized with CPUs.</span></span> <span data-ttu-id="43dde-128">`enabled` [GCNoAffinitize](gcnoaffinitize-element.md) öğesinin özniteliği, `false` kullanılacak **Gcheapaffinitizemask** ayarı için olmalıdır (varsayılan değer).</span><span class="sxs-lookup"><span data-stu-id="43dde-128">The `enabled` attribute of the [GCNoAffinitize](gcnoaffinitize-element.md) element must be `false` (its default value) for the **GCHeapAffinitizeMask** setting to be used.</span></span>

- <span data-ttu-id="43dde-129">[Gcheapcount](gcheapcount-element.md), sunucu GC için işlem tarafından kullanılan heçlerin sayısını sınırlar.</span><span class="sxs-lookup"><span data-stu-id="43dde-129">[GCHeapCount](gcheapcount-element.md), which limits the number of heaps used by the process for server GC.</span></span> <span data-ttu-id="43dde-130">Varsayılan olarak, her işlemci için bir yığın vardır.</span><span class="sxs-lookup"><span data-stu-id="43dde-130">By default, there is one heap for each processor.</span></span>

<span data-ttu-id="43dde-131">**nnnn** , ondalık değer olarak ifade edilen bir bit maskesidir.</span><span class="sxs-lookup"><span data-stu-id="43dde-131">**nnnn** is a bit mask expressed as a decimal value.</span></span> <span data-ttu-id="43dde-132">0 baytlık bit 0 işlemci 0 ' ı temsil eder, bayt 0 ' ın bit 1 ' i ve bu şekilde devam eder.</span><span class="sxs-lookup"><span data-stu-id="43dde-132">Bit 0 of byte 0 represents processor 0, bit 1 of byte 0 represents processor 1, and so on.</span></span> <span data-ttu-id="43dde-133">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="43dde-133">For example:</span></span>

```xml
<GCHeapAffinitizeMask enabled="1023"/>
```

<span data-ttu-id="43dde-134">1023 değeri 0x3FF veya 0011 1111 1111b şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="43dde-134">A value of 1023 is 0x3FF or 0011 1111 1111b.</span></span> <span data-ttu-id="43dde-135">İşlem, işlemci 0 ' dan işlemci 9 ' a kadar 10 işlemci kullanır.</span><span class="sxs-lookup"><span data-stu-id="43dde-135">The process uses 10 processors, from processor 0 through processor 9.</span></span>

## <a name="example"></a><span data-ttu-id="43dde-136">Örnek</span><span class="sxs-lookup"><span data-stu-id="43dde-136">Example</span></span>

<span data-ttu-id="43dde-137">Aşağıdaki örnek, bir uygulamanın 10 Heap/iş parçacığı ile sunucu GC kullandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="43dde-137">The following example indicates that an application uses server GC with 10 heaps/threads.</span></span> <span data-ttu-id="43dde-138">Bu yığınların sistemde çalışan diğer uygulamalardan Heap 'lerle örtüşmesini istemediğiniz için, işlemin 0 ile 9 arasında CPU kullanması gerektiğini belirtmek için **Gcheapaffinitizemask** kullanın.</span><span class="sxs-lookup"><span data-stu-id="43dde-138">Since you don't want those heaps to overlap with heaps from other applications running on the system, use **GCHeapAffinitizeMask** to specify that the process should use CPUs 0 through 9.</span></span>

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
      <GCHeapCount enabled="10"/>
      <GCHeapAffinitizeMask enabled="1023"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="43dde-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="43dde-139">See also</span></span>

- <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>
- [<span data-ttu-id="43dde-140">GCNoAffinitize öğesi</span><span class="sxs-lookup"><span data-stu-id="43dde-140">GCNoAffinitize element</span></span>](gcnoaffinitize-element.md)
- [<span data-ttu-id="43dde-141">GCHeapCount öğesi</span><span class="sxs-lookup"><span data-stu-id="43dde-141">GCHeapCount element</span></span>](gcheapcount-element.md)
- [<span data-ttu-id="43dde-142">Çöp toplamanın temelleri</span><span class="sxs-lookup"><span data-stu-id="43dde-142">Fundamentals of garbage collection</span></span>](../../../../standard/garbage-collection/fundamentals.md)
- [<span data-ttu-id="43dde-143">Çalışma zamanı ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="43dde-143">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="43dde-144">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="43dde-144">Configuration File Schema</span></span>](../index.md)
