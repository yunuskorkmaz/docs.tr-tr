---
description: 'Daha fazla bilgi edinin: <GCNoAffinitize> öğesi'
title: GCNoAffinitize öğesi
ms.date: 11/08/2019
helpviewer_keywords:
- gcNoAffinitize element
- <gcNoAffinitize> element
ms.openlocfilehash: 139c0fd9e1ec829a3569b77a85e6526bec765e21
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754556"
---
# <a name="gcnoaffinitize-element"></a><span data-ttu-id="6c7e9-103">\<GCNoAffinitize> öğesi</span><span class="sxs-lookup"><span data-stu-id="6c7e9-103">\<GCNoAffinitize> element</span></span>

<span data-ttu-id="6c7e9-104">Sunucu GC iş parçacıklarının CPU 'Lara yapılıp yapılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6c7e9-104">Specifies whether or not to affinitize server GC threads with CPUs.</span></span>

\<configuration>\
&nbsp;&nbsp;\<runtime>\
&nbsp;&nbsp;&nbsp;&nbsp;\<GCNoAffinitize>

## <a name="syntax"></a><span data-ttu-id="6c7e9-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="6c7e9-105">Syntax</span></span>

```xml
<GCNoAffinitize
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6c7e9-106">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="6c7e9-106">Attributes and elements</span></span>

<span data-ttu-id="6c7e9-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6c7e9-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="6c7e9-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6c7e9-108">Attributes</span></span>

|<span data-ttu-id="6c7e9-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="6c7e9-109">Attribute</span></span>|<span data-ttu-id="6c7e9-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6c7e9-110">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="6c7e9-111">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="6c7e9-111">Required attribute.</span></span><br /><br /><span data-ttu-id="6c7e9-112">Sunucu GC iş parçacıklarının/yığınların makinede bulunan işlemcilerle birlikte çalışıp çalışmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6c7e9-112">Specifies whether server GC threads/heaps are affinitized with the processors available on the machine.</span></span>|

#### <a name="enabled-attribute"></a><span data-ttu-id="6c7e9-113">enabled özniteliği</span><span class="sxs-lookup"><span data-stu-id="6c7e9-113">enabled attribute</span></span>

|<span data-ttu-id="6c7e9-114">Değer</span><span class="sxs-lookup"><span data-stu-id="6c7e9-114">Value</span></span>|<span data-ttu-id="6c7e9-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6c7e9-115">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="6c7e9-116">Sunucu GC iş parçacıklarını CPU 'Lara göre sıralar.</span><span class="sxs-lookup"><span data-stu-id="6c7e9-116">Affinitizes server GC threads with CPUs.</span></span> <span data-ttu-id="6c7e9-117">Bu varsayılan seçenektir.</span><span class="sxs-lookup"><span data-stu-id="6c7e9-117">This is the default.</span></span>|
|`true`|<span data-ttu-id="6c7e9-118">, Sunucu GC iş parçacıklarını CPU 'Lar ile göstermez.</span><span class="sxs-lookup"><span data-stu-id="6c7e9-118">Does not affinitize server GC threads with CPUs.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="6c7e9-119">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="6c7e9-119">Child elements</span></span>

<span data-ttu-id="6c7e9-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="6c7e9-120">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="6c7e9-121">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="6c7e9-121">Parent elements</span></span>

|<span data-ttu-id="6c7e9-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="6c7e9-122">Element</span></span>|<span data-ttu-id="6c7e9-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6c7e9-123">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="6c7e9-124">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="6c7e9-124">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="6c7e9-125">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="6c7e9-125">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="6c7e9-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6c7e9-126">Remarks</span></span>

<span data-ttu-id="6c7e9-127">Varsayılan olarak, sunucu GC iş parçacıkları ilgili CPU 'Ları ile birlikte zordur.</span><span class="sxs-lookup"><span data-stu-id="6c7e9-127">By default, server GC threads are hard-affinitized with their respective CPUs.</span></span> <span data-ttu-id="6c7e9-128">Sistemin kullanılabilir işlemcilerin her birinin kendi GC yığını ve iş parçacığı vardır.</span><span class="sxs-lookup"><span data-stu-id="6c7e9-128">Each of the system's available processors has its own GC heap and thread.</span></span> <span data-ttu-id="6c7e9-129">Bu, genellikle, önbellek kullanımını optimize eden tercih edilen ayardır.</span><span class="sxs-lookup"><span data-stu-id="6c7e9-129">This is typically the preferred setting since it optimizes cache usage.</span></span> <span data-ttu-id="6c7e9-130">.NET Framework 4.6.2 ile başlayarak, **GCNoAffinitize** öğesinin özniteliğini olarak ayarlayarak, `enabled` `true` Sunucu GC iş parçacıklarının ve CPU 'ların sıkı bir şekilde bağlı olmaması gerektiğini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6c7e9-130">Starting with .NET Framework 4.6.2, by setting the **GCNoAffinitize** element's `enabled` attribute to `true`, you can specify that server GC threads and CPUs should not be tightly coupled.</span></span>

<span data-ttu-id="6c7e9-131">**GCNoAffinitize** yapılandırma öğesini CPU Ile Sunucu GC iş parçacıklarını hiçbir şekilde yok etmek için tek başına belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6c7e9-131">You can specify the **GCNoAffinitize** configuration element alone to not affinitize server GC threads with CPUs.</span></span> <span data-ttu-id="6c7e9-132">Ayrıca, bir uygulama tarafından kullanılan GC yığınlarının ve iş parçacıklarının sayısını denetlemek için [Gcheapcount](gcheapcount-element.md) öğesiyle birlikte da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6c7e9-132">You can also use it along with the [GCHeapCount](gcheapcount-element.md) element to control the number of GC heaps and threads used by an application.</span></span>

<span data-ttu-id="6c7e9-133">`enabled` **GCNoAffinitize** öğesinin özniteliği `false` (varsayılan değeri) Ise, [gcheapcount](gcheapcount-element.md) öğesini Ayrıca, GC iş parçacıklarının ve yığınların hangi Işlemcilerin kullanılacağını belirtmek Için [Gcheapaffinitizemask](gcheapaffinitizemask-element.md) öğesiyle birlikte GC iş parçacıkları ve yığınların sayısını belirtmek için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6c7e9-133">If the `enabled` attribute of the **GCNoAffinitize** element is `false` (its default value), you can also use the [GCHeapCount](gcheapcount-element.md) element to specify the number of GC threads and heaps, along with the [GCHeapAffinitizeMask](gcheapaffinitizemask-element.md) element to specify the processors to which the GC threads and heaps are affinitized.</span></span>

## <a name="example"></a><span data-ttu-id="6c7e9-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="6c7e9-134">Example</span></span>

<span data-ttu-id="6c7e9-135">Aşağıdaki örnek, sunucu GC iş parçacıklarını sabit olarak göstermez:</span><span class="sxs-lookup"><span data-stu-id="6c7e9-135">The following example does not hard-affinitize server GC threads:</span></span>

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
      <GCNoAffinitize enabled="true"/>
   </runtime>
</configuration>
```

<span data-ttu-id="6c7e9-136">Aşağıdaki örnek, sunucu GC iş parçacıklarını göstermez ve GC Heap/iş parçacığı sayısını 10 ' a kısıtlar:</span><span class="sxs-lookup"><span data-stu-id="6c7e9-136">The following example does not affinitize server GC threads and limits the number of GC heaps/threads to 10:</span></span>

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
      <GCHeapCount enabled="10"/>
      <GCNoAffinitize enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="6c7e9-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6c7e9-137">See also</span></span>

- <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>
- [<span data-ttu-id="6c7e9-138">GCHeapAffinitizeMask öğesi</span><span class="sxs-lookup"><span data-stu-id="6c7e9-138">GCHeapAffinitizeMask element</span></span>](gcheapaffinitizemask-element.md)
- [<span data-ttu-id="6c7e9-139">GCHeapCount öğesi</span><span class="sxs-lookup"><span data-stu-id="6c7e9-139">GCHeapCount element</span></span>](gcheapcount-element.md)
- [<span data-ttu-id="6c7e9-140">Çöp toplamanın temelleri</span><span class="sxs-lookup"><span data-stu-id="6c7e9-140">Fundamentals of garbage collection</span></span>](../../../../standard/garbage-collection/fundamentals.md)
- [<span data-ttu-id="6c7e9-141">Çalışma zamanı ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="6c7e9-141">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="6c7e9-142">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="6c7e9-142">Configuration File Schema</span></span>](../index.md)
