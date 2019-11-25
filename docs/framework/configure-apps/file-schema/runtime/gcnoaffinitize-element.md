---
title: GCNoAffinitize öğesi
ms.date: 11/08/2019
helpviewer_keywords:
- gcNoAffinitize element
- <gcNoAffinitize> element
ms.openlocfilehash: 4031ff19131c905072696837d1622dbb6e54ae61
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73978377"
---
# <a name="gcnoaffinitize-element"></a><span data-ttu-id="abcc1-102">\<GCNoAffinitize > öğesi</span><span class="sxs-lookup"><span data-stu-id="abcc1-102">\<GCNoAffinitize> element</span></span>

<span data-ttu-id="abcc1-103">Sunucu GC iş parçacıklarının CPU 'Lara yapılıp yapılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="abcc1-103">Specifies whether or not to affinitize server GC threads with CPUs.</span></span>

<span data-ttu-id="abcc1-104">\<Yapılandırma > </span><span class="sxs-lookup"><span data-stu-id="abcc1-104">\<configuration></span></span>\
<span data-ttu-id="abcc1-105">&nbsp;&nbsp;\<çalışma zamanı > </span><span class="sxs-lookup"><span data-stu-id="abcc1-105">&nbsp;&nbsp;\<runtime></span></span>\
<span data-ttu-id="abcc1-106">&nbsp;&nbsp;&nbsp;&nbsp;\<GCNoAffinitize ></span><span class="sxs-lookup"><span data-stu-id="abcc1-106">&nbsp;&nbsp;&nbsp;&nbsp;\<GCNoAffinitize></span></span>

## <a name="syntax"></a><span data-ttu-id="abcc1-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="abcc1-107">Syntax</span></span>

```xml
<GCNoAffinitize
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="abcc1-108">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="abcc1-108">Attributes and elements</span></span>

<span data-ttu-id="abcc1-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="abcc1-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="abcc1-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="abcc1-110">Attributes</span></span>

|<span data-ttu-id="abcc1-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="abcc1-111">Attribute</span></span>|<span data-ttu-id="abcc1-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="abcc1-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="abcc1-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="abcc1-113">Required attribute.</span></span><br /><br /><span data-ttu-id="abcc1-114">Sunucu GC iş parçacıklarının/yığınların makinede bulunan işlemcilerle birlikte çalışıp çalışmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="abcc1-114">Specifies whether server GC threads/heaps are affinitized with the processors available on the machine.</span></span>|

#### <a name="enabled-attribute"></a><span data-ttu-id="abcc1-115">enabled özniteliği</span><span class="sxs-lookup"><span data-stu-id="abcc1-115">enabled attribute</span></span>

|<span data-ttu-id="abcc1-116">Değer</span><span class="sxs-lookup"><span data-stu-id="abcc1-116">Value</span></span>|<span data-ttu-id="abcc1-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="abcc1-117">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="abcc1-118">Sunucu GC iş parçacıklarını CPU 'Lara göre sıralar.</span><span class="sxs-lookup"><span data-stu-id="abcc1-118">Affinitizes server GC threads with CPUs.</span></span> <span data-ttu-id="abcc1-119">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="abcc1-119">This is the default.</span></span>|
|`true`|<span data-ttu-id="abcc1-120">, Sunucu GC iş parçacıklarını CPU 'Lar ile göstermez.</span><span class="sxs-lookup"><span data-stu-id="abcc1-120">Does not affinitize server GC threads with CPUs.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="abcc1-121">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="abcc1-121">Child elements</span></span>

<span data-ttu-id="abcc1-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="abcc1-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="abcc1-123">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="abcc1-123">Parent elements</span></span>

|<span data-ttu-id="abcc1-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="abcc1-124">Element</span></span>|<span data-ttu-id="abcc1-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="abcc1-125">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="abcc1-126">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="abcc1-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="abcc1-127">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="abcc1-127">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="abcc1-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="abcc1-128">Remarks</span></span>

<span data-ttu-id="abcc1-129">Varsayılan olarak, sunucu GC iş parçacıkları ilgili CPU 'Ları ile birlikte zordur.</span><span class="sxs-lookup"><span data-stu-id="abcc1-129">By default, server GC threads are hard-affinitized with their respective CPUs.</span></span> <span data-ttu-id="abcc1-130">Sistemin kullanılabilir işlemcilerin her birinin kendi GC yığını ve iş parçacığı vardır.</span><span class="sxs-lookup"><span data-stu-id="abcc1-130">Each of the system's available processors has its own GC heap and thread.</span></span> <span data-ttu-id="abcc1-131">Bu, genellikle, önbellek kullanımını optimize eden tercih edilen ayardır.</span><span class="sxs-lookup"><span data-stu-id="abcc1-131">This is typically the preferred setting since it optimizes cache usage.</span></span> <span data-ttu-id="abcc1-132">.NET Framework 4.6.2 ile başlayarak, **GCNoAffinitize** öğesinin `enabled` özniteliğini `false`olarak ayarlayarak, sunucu GC iş parçacıklarının ve CPU 'ların sıkı bir şekilde bağlı olmaması gerektiğini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="abcc1-132">Starting with .NET Framework 4.6.2, by setting the **GCNoAffinitize** element's `enabled` attribute to `false`, you can specify that server GC threads and CPUs should not be tightly coupled.</span></span>

<span data-ttu-id="abcc1-133">**GCNoAffinitize** yapılandırma öğesini CPU Ile Sunucu GC iş parçacıklarını hiçbir şekilde yok etmek için tek başına belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="abcc1-133">You can specify the **GCNoAffinitize** configuration element alone to not affinitize server GC threads with CPUs.</span></span> <span data-ttu-id="abcc1-134">Ayrıca, bir uygulama tarafından kullanılan GC yığınlarının ve iş parçacıklarının sayısını denetlemek için [Gcheapcount](gcheapcount-element.md) öğesiyle birlikte da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="abcc1-134">You can also use it along with the [GCHeapCount](gcheapcount-element.md) element to control the number of GC heaps and threads used by an application.</span></span>

<span data-ttu-id="abcc1-135">**GCNoAffinitize** öğesinin `enabled` özniteliği `false` (varsayılan değeri) ise, GC iş parçacıklarının ve yığınların hangi işlemcileri belirlemek Için [Gcheapaffinitizemask](gcheapaffinitizemask-element.md) öğesiyle birlikte GC iş parçacıklarının ve yığınların sayısını belirtmek Için [gcheapcount](gcheapcount-element.md) öğesini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="abcc1-135">If the `enabled` attribute of the **GCNoAffinitize** element is `false` (its default value), you can also use the [GCHeapCount](gcheapcount-element.md) element to specify the number of GC threads and heaps, along with the [GCHeapAffinitizeMask](gcheapaffinitizemask-element.md) element to specify the processors to which the GC threads and heaps are affinitized.</span></span>

## <a name="example"></a><span data-ttu-id="abcc1-136">Örnek</span><span class="sxs-lookup"><span data-stu-id="abcc1-136">Example</span></span>

<span data-ttu-id="abcc1-137">Aşağıdaki örnek, sunucu GC iş parçacıklarını sabit olarak göstermez:</span><span class="sxs-lookup"><span data-stu-id="abcc1-137">The following example does not hard-affinitize server GC threads:</span></span>

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
      <GCNoAffinitize enabled="true"/>
   </runtime>
</configuration>
```

<span data-ttu-id="abcc1-138">Aşağıdaki örnek, sunucu GC iş parçacıklarını göstermez ve GC Heap/iş parçacığı sayısını 10 ' a kısıtlar:</span><span class="sxs-lookup"><span data-stu-id="abcc1-138">The following example does not affinitize server GC threads and limits the number of GC heaps/threads to 10:</span></span>

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
      <GCHeapCount enabled="10"/>
      <GCNoAffinitize enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="abcc1-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="abcc1-139">See also</span></span>

- <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>
- [<span data-ttu-id="abcc1-140">GCHeapAffinitizeMask öğesi</span><span class="sxs-lookup"><span data-stu-id="abcc1-140">GCHeapAffinitizeMask element</span></span>](gcheapaffinitizemask-element.md)
- [<span data-ttu-id="abcc1-141">GCHeapCount öğesi</span><span class="sxs-lookup"><span data-stu-id="abcc1-141">GCHeapCount element</span></span>](gcheapcount-element.md)
- [<span data-ttu-id="abcc1-142">Çöp toplamanın temelleri</span><span class="sxs-lookup"><span data-stu-id="abcc1-142">Fundamentals of garbage collection</span></span>](../../../../standard/garbage-collection/fundamentals.md)
- [<span data-ttu-id="abcc1-143">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="abcc1-143">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="abcc1-144">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="abcc1-144">Configuration File Schema</span></span>](../index.md)
