---
title: GCHeapAffinitizeMask öğesi
ms.date: 11/08/2019
helpviewer_keywords:
- gcHeapCount element
- <gcHeapCount> element
ms.openlocfilehash: 09d6523fb10692dd3617a3827d5bccf112bc632b
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73978384"
---
# <a name="gcheapaffinitizemask-element"></a><span data-ttu-id="c9a71-102">GCHeapAffinitizeMask > öğesi \<</span><span class="sxs-lookup"><span data-stu-id="c9a71-102">\<GCHeapAffinitizeMask> element</span></span>

<span data-ttu-id="c9a71-103">GC yığınlarını ve bireysel işlemcileri arasındaki benzeşimi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c9a71-103">Defines the affinity between GC heaps and individual processors.</span></span>

<span data-ttu-id="c9a71-104">\<Yapılandırma > </span><span class="sxs-lookup"><span data-stu-id="c9a71-104">\<configuration></span></span>\
<span data-ttu-id="c9a71-105">&nbsp;&nbsp;\<çalışma zamanı > </span><span class="sxs-lookup"><span data-stu-id="c9a71-105">&nbsp;&nbsp;\<runtime></span></span>\
<span data-ttu-id="c9a71-106">&nbsp;&nbsp;&nbsp;&nbsp;\<GCHeapAffinitizeMask ></span><span class="sxs-lookup"><span data-stu-id="c9a71-106">&nbsp;&nbsp;&nbsp;&nbsp;\<GCHeapAffinitizeMask></span></span>

## <a name="syntax"></a><span data-ttu-id="c9a71-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c9a71-107">Syntax</span></span>

```xml
<GCHeapAffinitizeMask
   enabled="nnnn"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c9a71-108">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="c9a71-108">Attributes and elements</span></span>

<span data-ttu-id="c9a71-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c9a71-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="c9a71-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c9a71-110">Attributes</span></span>

|<span data-ttu-id="c9a71-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c9a71-111">Attribute</span></span>|<span data-ttu-id="c9a71-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c9a71-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="c9a71-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="c9a71-113">Required attribute.</span></span><br /><br /><span data-ttu-id="c9a71-114">GC yığınlarını ve tek tek işlemciler arasındaki benzeşimi belirtir.</span><span class="sxs-lookup"><span data-stu-id="c9a71-114">Specifies the affinity between GC heaps and individual processors.</span></span> |

#### <a name="enabled-attribute"></a><span data-ttu-id="c9a71-115">enabled özniteliği</span><span class="sxs-lookup"><span data-stu-id="c9a71-115">enabled attribute</span></span>

|<span data-ttu-id="c9a71-116">Değer</span><span class="sxs-lookup"><span data-stu-id="c9a71-116">Value</span></span>|<span data-ttu-id="c9a71-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c9a71-117">Description</span></span>|
|-----------|-----------------|
|`nnnn`|<span data-ttu-id="c9a71-118">Sunucu GC yığınlarını ve bireysel işlemcileri arasındaki benzeşimi tanımlayan bir bit maskesini oluşturan ondalık bir değer.</span><span class="sxs-lookup"><span data-stu-id="c9a71-118">A decimal value that forms a bitmask defining the affinity between server GC heaps and individual processors.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="c9a71-119">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="c9a71-119">Child elements</span></span>

<span data-ttu-id="c9a71-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="c9a71-120">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c9a71-121">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="c9a71-121">Parent elements</span></span>

|<span data-ttu-id="c9a71-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="c9a71-122">Element</span></span>|<span data-ttu-id="c9a71-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c9a71-123">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="c9a71-124">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="c9a71-124">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="c9a71-125">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="c9a71-125">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c9a71-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c9a71-126">Remarks</span></span>

<span data-ttu-id="c9a71-127">Varsayılan olarak, sunucu GC iş parçacıkları, her işlemci için bir GC yığını, bir sunucu GC iş parçacığı ve bir arka plan sunucusu GC iş parçacığı olmak üzere kendi CPU 'SU ile sabit olarak belirlenir.</span><span class="sxs-lookup"><span data-stu-id="c9a71-127">By default, server GC threads are hard-affinitized with their respective CPU so that there is one GC heap, one server GC thread, and one background server GC thread for each processor.</span></span> <span data-ttu-id="c9a71-128">.NET Framework 4.6.2 ile başlayarak, Heap sayısı **Gcheapcount** öğesiyle sınırlı olduğunda, sunucu GC yığınlarını ve işlemcileri arasındaki benzeşimi denetlemek Için **Gcheapaffinitizemask** öğesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c9a71-128">Starting with .NET Framework 4.6.2, you can use the **GCHeapAffinitizeMask** element to control the affinity between server GC heaps and processors when the number of heaps is limited by the **GCHeapCount** element.</span></span>

<span data-ttu-id="c9a71-129">**Gcheapaffinitizemask** genellikle iki diğer bayraklı birlikte kullanılır:</span><span class="sxs-lookup"><span data-stu-id="c9a71-129">**GCHeapAffinitizeMask** is typically used along with two other flags:</span></span>

- <span data-ttu-id="c9a71-130">[GCNoAffinitize](gcnoaffinitize-element.md), sunucu GC iş parçacıklarının/yığınların CPU 'lara uygulanıp gösterilmeyeceğini denetler.</span><span class="sxs-lookup"><span data-stu-id="c9a71-130">[GCNoAffinitize](gcnoaffinitize-element.md), which controls whether server GC threads/heaps are affinitized with CPUs.</span></span> <span data-ttu-id="c9a71-131">[GCNoAffinitize](gcnoaffinitize-element.md) öğesinin `enabled` özniteliği, **Gcheapaffinitizemask** ayarının kullanılması için `false` (varsayılan değeri) olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c9a71-131">The `enabled` attribute of the [GCNoAffinitize](gcnoaffinitize-element.md) element must be `false` (its default value) for the **GCHeapAffinitizeMask** setting to be used.</span></span>

- <span data-ttu-id="c9a71-132">[Gcheapcount](gcheapcount-element.md), sunucu GC için işlem tarafından kullanılan heçlerin sayısını sınırlar.</span><span class="sxs-lookup"><span data-stu-id="c9a71-132">[GCHeapCount](gcheapcount-element.md), which limits the number of heaps used by the process for server GC.</span></span> <span data-ttu-id="c9a71-133">Varsayılan olarak, her işlemci için bir yığın vardır.</span><span class="sxs-lookup"><span data-stu-id="c9a71-133">By default, there is one heap for each processor.</span></span>

<span data-ttu-id="c9a71-134">**nnnn** , ondalık değer olarak ifade edilen bir bit maskesidir.</span><span class="sxs-lookup"><span data-stu-id="c9a71-134">**nnnn** is a bit mask expressed as a decimal value.</span></span> <span data-ttu-id="c9a71-135">0 baytlık bit 0 işlemci 0 ' ı temsil eder, bayt 0 ' ın bit 1 ' i ve bu şekilde devam eder.</span><span class="sxs-lookup"><span data-stu-id="c9a71-135">Bit 0 of byte 0 represents processor 0, bit 1 of byte 0 represents processor 1, and so on.</span></span> <span data-ttu-id="c9a71-136">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="c9a71-136">For example:</span></span>

```xml
<GCHeapAffinitizeMask enabled="1023"/>
```

<span data-ttu-id="c9a71-137">1023 değeri 0x3FF veya 0011 1111 1111b şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="c9a71-137">A value of 1023 is 0x3FF or 0011 1111 1111b.</span></span> <span data-ttu-id="c9a71-138">İşlem, işlemci 0 ' dan işlemci 9 ' a kadar 10 işlemci kullanır.</span><span class="sxs-lookup"><span data-stu-id="c9a71-138">The process uses 10 processors, from processor 0 through processor 9.</span></span>

## <a name="example"></a><span data-ttu-id="c9a71-139">Örnek</span><span class="sxs-lookup"><span data-stu-id="c9a71-139">Example</span></span>

<span data-ttu-id="c9a71-140">Aşağıdaki örnek, bir uygulamanın 10 Heap/iş parçacığı ile sunucu GC kullandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c9a71-140">The following example indicates that an application uses server GC with 10 heaps/threads.</span></span> <span data-ttu-id="c9a71-141">Bu yığınların sistemde çalışan diğer uygulamalardan Heap 'lerle örtüşmesini istemediğiniz için, işlemin 0 ile 9 arasında CPU kullanması gerektiğini belirtmek için **Gcheapaffinitizemask** kullanın.</span><span class="sxs-lookup"><span data-stu-id="c9a71-141">Since you don't want those heaps to overlap with heaps from other applications running on the system, use **GCHeapAffinitizeMask** to specify that the process should use CPUs 0 through 9.</span></span>

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
      <GCHeapCount enabled="10"/>
      <GCHeapAffinitizeMask enabled="1023"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="c9a71-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c9a71-142">See also</span></span>

- <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>
- [<span data-ttu-id="c9a71-143">GCNoAffinitize öğesi</span><span class="sxs-lookup"><span data-stu-id="c9a71-143">GCNoAffinitize element</span></span>](gcnoaffinitize-element.md)
- [<span data-ttu-id="c9a71-144">GCHeapCount öğesi</span><span class="sxs-lookup"><span data-stu-id="c9a71-144">GCHeapCount element</span></span>](gcheapcount-element.md)
- [<span data-ttu-id="c9a71-145">Çöp toplamanın temelleri</span><span class="sxs-lookup"><span data-stu-id="c9a71-145">Fundamentals of garbage collection</span></span>](../../../../standard/garbage-collection/fundamentals.md)
- [<span data-ttu-id="c9a71-146">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="c9a71-146">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="c9a71-147">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="c9a71-147">Configuration File Schema</span></span>](../index.md)
