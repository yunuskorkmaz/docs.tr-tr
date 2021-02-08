---
description: 'Daha fazla bilgi edinin: <GCHeapAffinitizeMask> öğesi'
title: GCHeapAffinitizeMask öğesi
ms.date: 11/08/2019
helpviewer_keywords:
- gcHeapCount element
- <gcHeapCount> element
ms.openlocfilehash: ea6be3fa3d973f228576db69d0700b1f7ddba585
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786986"
---
# <a name="gcheapaffinitizemask-element"></a><span data-ttu-id="20a51-103">\<GCHeapAffinitizeMask> öğesi</span><span class="sxs-lookup"><span data-stu-id="20a51-103">\<GCHeapAffinitizeMask> element</span></span>

<span data-ttu-id="20a51-104">GC yığınlarını ve bireysel işlemcileri arasındaki benzeşimi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="20a51-104">Defines the affinity between GC heaps and individual processors.</span></span>

\<configuration>\
&nbsp;&nbsp;\<runtime>\
&nbsp;&nbsp;&nbsp;&nbsp;\<GCHeapAffinitizeMask>

## <a name="syntax"></a><span data-ttu-id="20a51-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="20a51-105">Syntax</span></span>

```xml
<GCHeapAffinitizeMask
   enabled="nnnn"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="20a51-106">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="20a51-106">Attributes and elements</span></span>

<span data-ttu-id="20a51-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="20a51-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="20a51-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="20a51-108">Attributes</span></span>

|<span data-ttu-id="20a51-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="20a51-109">Attribute</span></span>|<span data-ttu-id="20a51-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="20a51-110">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="20a51-111">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="20a51-111">Required attribute.</span></span><br /><br /><span data-ttu-id="20a51-112">GC yığınlarını ve tek tek işlemciler arasındaki benzeşimi belirtir.</span><span class="sxs-lookup"><span data-stu-id="20a51-112">Specifies the affinity between GC heaps and individual processors.</span></span> |

#### <a name="enabled-attribute"></a><span data-ttu-id="20a51-113">enabled özniteliği</span><span class="sxs-lookup"><span data-stu-id="20a51-113">enabled attribute</span></span>

|<span data-ttu-id="20a51-114">Değer</span><span class="sxs-lookup"><span data-stu-id="20a51-114">Value</span></span>|<span data-ttu-id="20a51-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="20a51-115">Description</span></span>|
|-----------|-----------------|
|`nnnn`|<span data-ttu-id="20a51-116">Sunucu GC yığınlarını ve bireysel işlemcileri arasındaki benzeşimi tanımlayan bir bit maskesini oluşturan ondalık bir değer.</span><span class="sxs-lookup"><span data-stu-id="20a51-116">A decimal value that forms a bitmask defining the affinity between server GC heaps and individual processors.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="20a51-117">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="20a51-117">Child elements</span></span>

<span data-ttu-id="20a51-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="20a51-118">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="20a51-119">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="20a51-119">Parent elements</span></span>

|<span data-ttu-id="20a51-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="20a51-120">Element</span></span>|<span data-ttu-id="20a51-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="20a51-121">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="20a51-122">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="20a51-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="20a51-123">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="20a51-123">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="20a51-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="20a51-124">Remarks</span></span>

<span data-ttu-id="20a51-125">Varsayılan olarak, sunucu GC iş parçacıkları, her işlemci için bir GC yığını, bir sunucu GC iş parçacığı ve bir arka plan sunucusu GC iş parçacığı olmak üzere kendi CPU 'SU ile sabit olarak belirlenir.</span><span class="sxs-lookup"><span data-stu-id="20a51-125">By default, server GC threads are hard-affinitized with their respective CPU so that there is one GC heap, one server GC thread, and one background server GC thread for each processor.</span></span> <span data-ttu-id="20a51-126">.NET Framework 4.6.2 ile başlayarak, Heap sayısı **Gcheapcount** öğesiyle sınırlı olduğunda, sunucu GC yığınlarını ve işlemcileri arasındaki benzeşimi denetlemek Için **Gcheapaffinitizemask** öğesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="20a51-126">Starting with .NET Framework 4.6.2, you can use the **GCHeapAffinitizeMask** element to control the affinity between server GC heaps and processors when the number of heaps is limited by the **GCHeapCount** element.</span></span>

<span data-ttu-id="20a51-127">**Gcheapaffinitizemask** genellikle iki diğer bayraklı birlikte kullanılır:</span><span class="sxs-lookup"><span data-stu-id="20a51-127">**GCHeapAffinitizeMask** is typically used along with two other flags:</span></span>

- <span data-ttu-id="20a51-128">[GCNoAffinitize](gcnoaffinitize-element.md), sunucu GC iş parçacıklarının/yığınların CPU 'lara uygulanıp gösterilmeyeceğini denetler.</span><span class="sxs-lookup"><span data-stu-id="20a51-128">[GCNoAffinitize](gcnoaffinitize-element.md), which controls whether server GC threads/heaps are affinitized with CPUs.</span></span> <span data-ttu-id="20a51-129">`enabled` [GCNoAffinitize](gcnoaffinitize-element.md) öğesinin özniteliği, `false` kullanılacak **Gcheapaffinitizemask** ayarı için olmalıdır (varsayılan değer).</span><span class="sxs-lookup"><span data-stu-id="20a51-129">The `enabled` attribute of the [GCNoAffinitize](gcnoaffinitize-element.md) element must be `false` (its default value) for the **GCHeapAffinitizeMask** setting to be used.</span></span>

- <span data-ttu-id="20a51-130">[Gcheapcount](gcheapcount-element.md), sunucu GC için işlem tarafından kullanılan heçlerin sayısını sınırlar.</span><span class="sxs-lookup"><span data-stu-id="20a51-130">[GCHeapCount](gcheapcount-element.md), which limits the number of heaps used by the process for server GC.</span></span> <span data-ttu-id="20a51-131">Varsayılan olarak, her işlemci için bir yığın vardır.</span><span class="sxs-lookup"><span data-stu-id="20a51-131">By default, there is one heap for each processor.</span></span>

<span data-ttu-id="20a51-132">**nnnn** , ondalık değer olarak ifade edilen bir bit maskesidir.</span><span class="sxs-lookup"><span data-stu-id="20a51-132">**nnnn** is a bit mask expressed as a decimal value.</span></span> <span data-ttu-id="20a51-133">0 baytlık bit 0 işlemci 0 ' ı temsil eder, bayt 0 ' ın bit 1 ' i ve bu şekilde devam eder.</span><span class="sxs-lookup"><span data-stu-id="20a51-133">Bit 0 of byte 0 represents processor 0, bit 1 of byte 0 represents processor 1, and so on.</span></span> <span data-ttu-id="20a51-134">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="20a51-134">For example:</span></span>

```xml
<GCHeapAffinitizeMask enabled="1023"/>
```

<span data-ttu-id="20a51-135">1023 değeri 0x3FF veya 0011 1111 1111b şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="20a51-135">A value of 1023 is 0x3FF or 0011 1111 1111b.</span></span> <span data-ttu-id="20a51-136">İşlem, işlemci 0 ' dan işlemci 9 ' a kadar 10 işlemci kullanır.</span><span class="sxs-lookup"><span data-stu-id="20a51-136">The process uses 10 processors, from processor 0 through processor 9.</span></span>

## <a name="example"></a><span data-ttu-id="20a51-137">Örnek</span><span class="sxs-lookup"><span data-stu-id="20a51-137">Example</span></span>

<span data-ttu-id="20a51-138">Aşağıdaki örnek, bir uygulamanın 10 Heap/iş parçacığı ile sunucu GC kullandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="20a51-138">The following example indicates that an application uses server GC with 10 heaps/threads.</span></span> <span data-ttu-id="20a51-139">Bu yığınların sistemde çalışan diğer uygulamalardan Heap 'lerle örtüşmesini istemediğiniz için, işlemin 0 ile 9 arasında CPU kullanması gerektiğini belirtmek için **Gcheapaffinitizemask** kullanın.</span><span class="sxs-lookup"><span data-stu-id="20a51-139">Since you don't want those heaps to overlap with heaps from other applications running on the system, use **GCHeapAffinitizeMask** to specify that the process should use CPUs 0 through 9.</span></span>

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
      <GCHeapCount enabled="10"/>
      <GCHeapAffinitizeMask enabled="1023"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="20a51-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="20a51-140">See also</span></span>

- <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>
- [<span data-ttu-id="20a51-141">GCNoAffinitize öğesi</span><span class="sxs-lookup"><span data-stu-id="20a51-141">GCNoAffinitize element</span></span>](gcnoaffinitize-element.md)
- [<span data-ttu-id="20a51-142">GCHeapCount öğesi</span><span class="sxs-lookup"><span data-stu-id="20a51-142">GCHeapCount element</span></span>](gcheapcount-element.md)
- [<span data-ttu-id="20a51-143">Çöp toplamanın temelleri</span><span class="sxs-lookup"><span data-stu-id="20a51-143">Fundamentals of garbage collection</span></span>](../../../../standard/garbage-collection/fundamentals.md)
- [<span data-ttu-id="20a51-144">Çalışma zamanı ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="20a51-144">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="20a51-145">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="20a51-145">Configuration File Schema</span></span>](../index.md)
