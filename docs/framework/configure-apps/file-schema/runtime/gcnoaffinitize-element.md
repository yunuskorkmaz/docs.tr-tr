---
title: GCNoAffinitize öğesi
ms.date: 11/08/2019
helpviewer_keywords:
- gcNoAffinitize element
- <gcNoAffinitize> element
ms.openlocfilehash: 16d6e5adefe2b632d7251669650058d7df7cea70
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84004744"
---
# <a name="gcnoaffinitize-element"></a><span data-ttu-id="73435-102">\<GCNoAffinitize> öğesi</span><span class="sxs-lookup"><span data-stu-id="73435-102">\<GCNoAffinitize> element</span></span>

<span data-ttu-id="73435-103">Sunucu GC iş parçacıklarının CPU 'Lara yapılıp yapılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="73435-103">Specifies whether or not to affinitize server GC threads with CPUs.</span></span>

\<configuration>\
&nbsp;&nbsp;\<runtime>\
&nbsp;&nbsp;&nbsp;&nbsp;\<GCNoAffinitize>

## <a name="syntax"></a><span data-ttu-id="73435-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="73435-104">Syntax</span></span>

```xml
<GCNoAffinitize
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="73435-105">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="73435-105">Attributes and elements</span></span>

<span data-ttu-id="73435-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="73435-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="73435-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="73435-107">Attributes</span></span>

|<span data-ttu-id="73435-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="73435-108">Attribute</span></span>|<span data-ttu-id="73435-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="73435-109">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="73435-110">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="73435-110">Required attribute.</span></span><br /><br /><span data-ttu-id="73435-111">Sunucu GC iş parçacıklarının/yığınların makinede bulunan işlemcilerle birlikte çalışıp çalışmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="73435-111">Specifies whether server GC threads/heaps are affinitized with the processors available on the machine.</span></span>|

#### <a name="enabled-attribute"></a><span data-ttu-id="73435-112">enabled özniteliği</span><span class="sxs-lookup"><span data-stu-id="73435-112">enabled attribute</span></span>

|<span data-ttu-id="73435-113">Değer</span><span class="sxs-lookup"><span data-stu-id="73435-113">Value</span></span>|<span data-ttu-id="73435-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="73435-114">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="73435-115">Sunucu GC iş parçacıklarını CPU 'Lara göre sıralar.</span><span class="sxs-lookup"><span data-stu-id="73435-115">Affinitizes server GC threads with CPUs.</span></span> <span data-ttu-id="73435-116">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="73435-116">This is the default.</span></span>|
|`true`|<span data-ttu-id="73435-117">, Sunucu GC iş parçacıklarını CPU 'Lar ile göstermez.</span><span class="sxs-lookup"><span data-stu-id="73435-117">Does not affinitize server GC threads with CPUs.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="73435-118">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="73435-118">Child elements</span></span>

<span data-ttu-id="73435-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="73435-119">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="73435-120">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="73435-120">Parent elements</span></span>

|<span data-ttu-id="73435-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="73435-121">Element</span></span>|<span data-ttu-id="73435-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="73435-122">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="73435-123">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="73435-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="73435-124">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="73435-124">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="73435-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="73435-125">Remarks</span></span>

<span data-ttu-id="73435-126">Varsayılan olarak, sunucu GC iş parçacıkları ilgili CPU 'Ları ile birlikte zordur.</span><span class="sxs-lookup"><span data-stu-id="73435-126">By default, server GC threads are hard-affinitized with their respective CPUs.</span></span> <span data-ttu-id="73435-127">Sistemin kullanılabilir işlemcilerin her birinin kendi GC yığını ve iş parçacığı vardır.</span><span class="sxs-lookup"><span data-stu-id="73435-127">Each of the system's available processors has its own GC heap and thread.</span></span> <span data-ttu-id="73435-128">Bu, genellikle, önbellek kullanımını optimize eden tercih edilen ayardır.</span><span class="sxs-lookup"><span data-stu-id="73435-128">This is typically the preferred setting since it optimizes cache usage.</span></span> <span data-ttu-id="73435-129">.NET Framework 4.6.2 ile başlayarak, **GCNoAffinitize** öğesinin özniteliğini olarak ayarlayarak, `enabled` `true` Sunucu GC iş parçacıklarının ve CPU 'ların sıkı bir şekilde bağlı olmaması gerektiğini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="73435-129">Starting with .NET Framework 4.6.2, by setting the **GCNoAffinitize** element's `enabled` attribute to `true`, you can specify that server GC threads and CPUs should not be tightly coupled.</span></span>

<span data-ttu-id="73435-130">**GCNoAffinitize** yapılandırma öğesini CPU Ile Sunucu GC iş parçacıklarını hiçbir şekilde yok etmek için tek başına belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="73435-130">You can specify the **GCNoAffinitize** configuration element alone to not affinitize server GC threads with CPUs.</span></span> <span data-ttu-id="73435-131">Ayrıca, bir uygulama tarafından kullanılan GC yığınlarının ve iş parçacıklarının sayısını denetlemek için [Gcheapcount](gcheapcount-element.md) öğesiyle birlikte da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="73435-131">You can also use it along with the [GCHeapCount](gcheapcount-element.md) element to control the number of GC heaps and threads used by an application.</span></span>

<span data-ttu-id="73435-132">`enabled` **GCNoAffinitize** öğesinin özniteliği `false` (varsayılan değeri) Ise, [gcheapcount](gcheapcount-element.md) öğesini Ayrıca, GC iş parçacıklarının ve yığınların hangi Işlemcilerin kullanılacağını belirtmek Için [Gcheapaffinitizemask](gcheapaffinitizemask-element.md) öğesiyle birlikte GC iş parçacıkları ve yığınların sayısını belirtmek için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="73435-132">If the `enabled` attribute of the **GCNoAffinitize** element is `false` (its default value), you can also use the [GCHeapCount](gcheapcount-element.md) element to specify the number of GC threads and heaps, along with the [GCHeapAffinitizeMask](gcheapaffinitizemask-element.md) element to specify the processors to which the GC threads and heaps are affinitized.</span></span>

## <a name="example"></a><span data-ttu-id="73435-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="73435-133">Example</span></span>

<span data-ttu-id="73435-134">Aşağıdaki örnek, sunucu GC iş parçacıklarını sabit olarak göstermez:</span><span class="sxs-lookup"><span data-stu-id="73435-134">The following example does not hard-affinitize server GC threads:</span></span>

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
      <GCNoAffinitize enabled="true"/>
   </runtime>
</configuration>
```

<span data-ttu-id="73435-135">Aşağıdaki örnek, sunucu GC iş parçacıklarını göstermez ve GC Heap/iş parçacığı sayısını 10 ' a kısıtlar:</span><span class="sxs-lookup"><span data-stu-id="73435-135">The following example does not affinitize server GC threads and limits the number of GC heaps/threads to 10:</span></span>

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
      <GCHeapCount enabled="10"/>
      <GCNoAffinitize enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="73435-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="73435-136">See also</span></span>

- <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>
- [<span data-ttu-id="73435-137">GCHeapAffinitizeMask öğesi</span><span class="sxs-lookup"><span data-stu-id="73435-137">GCHeapAffinitizeMask element</span></span>](gcheapaffinitizemask-element.md)
- [<span data-ttu-id="73435-138">GCHeapCount öğesi</span><span class="sxs-lookup"><span data-stu-id="73435-138">GCHeapCount element</span></span>](gcheapcount-element.md)
- [<span data-ttu-id="73435-139">Çöp toplamanın temelleri</span><span class="sxs-lookup"><span data-stu-id="73435-139">Fundamentals of garbage collection</span></span>](../../../../standard/garbage-collection/fundamentals.md)
- [<span data-ttu-id="73435-140">Çalışma zamanı ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="73435-140">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="73435-141">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="73435-141">Configuration File Schema</span></span>](../index.md)
