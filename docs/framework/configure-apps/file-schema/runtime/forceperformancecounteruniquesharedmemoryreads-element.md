---
description: 'Daha fazla bilgi edinin: <forcePerformanceCounterUniqueSharedMemoryReads> öğesi'
title: <forcePerformanceCounterUniqueSharedMemoryReads> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- forcePerformanceCounterUniqueSharedMemoryReads element
- <forcePerformanceCounterUniqueSharedMemoryReads> element
ms.assetid: 91149858-4810-4f65-9b48-468488172c9b
ms.openlocfilehash: 63fe695cc993faa851a9ea3196294397d2992c45
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787038"
---
# <a name="forceperformancecounteruniquesharedmemoryreads-element"></a><span data-ttu-id="fa2b3-103">\<forcePerformanceCounterUniqueSharedMemoryReads> Öğesi</span><span class="sxs-lookup"><span data-stu-id="fa2b3-103">\<forcePerformanceCounterUniqueSharedMemoryReads> Element</span></span>

<span data-ttu-id="fa2b3-104">PerfCounter.dll, performans sayacı verilerinin kategoriye özgü paylaşılan bellekten mı yoksa genel bellekten mi yükleneceğini öğrenmek için, .NET Framework sürüm 1,1 uygulamasında CategoryOptions kayıt defteri ayarını kullanıp kullanmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="fa2b3-104">Specifies whether PerfCounter.dll uses the CategoryOptions registry setting in a .NET Framework version 1.1 application to determine whether to load performance counter data from category-specific shared memory or global memory.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<forcePerformanceCounterUniqueSharedMemoryReads>**  
  
## <a name="syntax"></a><span data-ttu-id="fa2b3-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="fa2b3-105">Syntax</span></span>  
  
```xml  
<forcePerformanceCounterUniqueSharedMemoryReads
enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fa2b3-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="fa2b3-106">Attributes and Elements</span></span>  

 <span data-ttu-id="fa2b3-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fa2b3-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fa2b3-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="fa2b3-108">Attributes</span></span>  
  
|<span data-ttu-id="fa2b3-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="fa2b3-109">Attribute</span></span>|<span data-ttu-id="fa2b3-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fa2b3-110">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="fa2b3-111">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="fa2b3-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="fa2b3-112">PerfCounter.dll, performans sayacı verilerinin kategoriye özgü paylaşılan bellekten mi yoksa genel bellekten mi yükleneceğini öğrenmek için CategoryOptions kayıt defteri ayarını kullanıp kullanmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="fa2b3-112">Indicates whether PerfCounter.dll uses the CategoryOptions registry setting to determine whether to load performance counter data from category-specific shared memory or global memory.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="fa2b3-113">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="fa2b3-113">enabled Attribute</span></span>  
  
|<span data-ttu-id="fa2b3-114">Değer</span><span class="sxs-lookup"><span data-stu-id="fa2b3-114">Value</span></span>|<span data-ttu-id="fa2b3-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fa2b3-115">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="fa2b3-116">PerfCounter.dll CategoryOptions kayıt defteri ayarını kullanmaz. bu varsayılan ayardır.</span><span class="sxs-lookup"><span data-stu-id="fa2b3-116">PerfCounter.dll does not use the CategoryOptions registry setting This is the default.</span></span>|  
|`true`|<span data-ttu-id="fa2b3-117">PerfCounter.dll CategoryOptions kayıt defteri ayarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="fa2b3-117">PerfCounter.dll does use the CategoryOptions registry setting.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fa2b3-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="fa2b3-118">Child Elements</span></span>  

 <span data-ttu-id="fa2b3-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="fa2b3-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fa2b3-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="fa2b3-120">Parent Elements</span></span>  
  
|<span data-ttu-id="fa2b3-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="fa2b3-121">Element</span></span>|<span data-ttu-id="fa2b3-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fa2b3-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="fa2b3-123">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="fa2b3-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="fa2b3-124">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="fa2b3-124">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fa2b3-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fa2b3-125">Remarks</span></span>  

 <span data-ttu-id="fa2b3-126">.NET Framework 4 ' ün öncesindeki .NET Framework sürümlerinde, yüklenmiş olan PerfCounter.dll sürümü, işleme yüklenmiş çalışma zamanına karşılık gelen sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="fa2b3-126">In versions of the .NET Framework before the .NET Framework 4, the version of PerfCounter.dll that was loaded corresponded to the runtime that was loaded in the process.</span></span> <span data-ttu-id="fa2b3-127">Bir bilgisayarda .NET Framework sürüm 1,1 ve .NET Framework 2,0 yüklüyse, bir .NET Framework 1,1 uygulaması PerfCounter.dll .NET Framework 1,1 sürümünü yükler.</span><span class="sxs-lookup"><span data-stu-id="fa2b3-127">If a computer had both the .NET Framework version 1.1 and the .NET Framework 2.0 installed, a .NET Framework 1.1 application would load the .NET Framework 1.1 version of PerfCounter.dll.</span></span> <span data-ttu-id="fa2b3-128">.NET Framework 4 ' te başlayarak, PerfCounter.dll en yeni yüklü sürümü yüklenir.</span><span class="sxs-lookup"><span data-stu-id="fa2b3-128">Starting with the .NET Framework 4, the newest installed version of PerfCounter.dll is loaded.</span></span> <span data-ttu-id="fa2b3-129">Bu, .NET Framework 1,1 uygulamasının, bilgisayarda .NET Framework 4 yüklüyse PerfCounter.dll .NET Framework 4 sürümünü yükleyemeyeceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="fa2b3-129">This means that a .NET Framework 1.1 application will load the .NET Framework 4 version of PerfCounter.dll if the .NET Framework 4 is installed on the computer.</span></span>  
  
 <span data-ttu-id="fa2b3-130">.NET Framework 4 ' ten başlayarak, performans sayaçlarını tüketerek, PerfCounter.dll kategoriye özgü paylaşılan bellekten veya genel paylaşılan bellekten okunup okunmayacağını öğrenmek için her bir sağlayıcı için CategoryOptions kayıt defteri girişini denetler.</span><span class="sxs-lookup"><span data-stu-id="fa2b3-130">Starting with the .NET Framework 4, when consuming performance counters, PerfCounter.dll checks the CategoryOptions registry entry for each provider to determine whether it should read from category-specific shared memory or global shared memory.</span></span> <span data-ttu-id="fa2b3-131">.NET Framework 1,1 PerfCounter.dll, kategoriye özgü paylaşılan belleğin farkında olmadığından, bu kayıt defteri girişini okummıyor; her zaman genel paylaşılan bellekten okur.</span><span class="sxs-lookup"><span data-stu-id="fa2b3-131">The .NET Framework 1.1 PerfCounter.dll does not read that registry entry, because it is not aware of category-specific shared memory; it always reads from global shared memory.</span></span>  
  
 <span data-ttu-id="fa2b3-132">Geriye dönük uyumluluk için .NET Framework 4 PerfCounter.dll, bir .NET Framework 1,1 uygulamasında çalışırken CategoryOptions kayıt defteri girişini denetlemez.</span><span class="sxs-lookup"><span data-stu-id="fa2b3-132">For backward compatibility, the .NET Framework 4 PerfCounter.dll does not check the CategoryOptions registry entry when running in a .NET Framework 1.1 application.</span></span> <span data-ttu-id="fa2b3-133">Yalnızca .NET Framework 1,1 PerfCounter.dll gibi genel paylaşılan belleği kullanır.</span><span class="sxs-lookup"><span data-stu-id="fa2b3-133">It simply uses global shared memory, just like the .NET Framework 1.1 PerfCounter.dll.</span></span> <span data-ttu-id="fa2b3-134">Ancak, .NET Framework 4 PerfCounter.dll öğesini etkinleştirerek kayıt defteri ayarını kontrol edebilirsiniz `<forcePerformanceCounterUniqueSharedMemoryReads>` .</span><span class="sxs-lookup"><span data-stu-id="fa2b3-134">However, you can instruct the .NET Framework 4 PerfCounter.dll to check the registry setting by enabling the `<forcePerformanceCounterUniqueSharedMemoryReads>` element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fa2b3-135">Öğesinin etkinleştirilmesi, `<forcePerformanceCounterUniqueSharedMemoryReads>` kategoriye özgü paylaşılan belleğin kullanılacağını garanti etmez.</span><span class="sxs-lookup"><span data-stu-id="fa2b3-135">Enabling the `<forcePerformanceCounterUniqueSharedMemoryReads>` element does not guarantee that category-specific shared memory will be used.</span></span> <span data-ttu-id="fa2b3-136">Enabled ayarı `true` yalnızca PerfCounter.dll CategoryOptions kayıt defteri ayarına başvuracak.</span><span class="sxs-lookup"><span data-stu-id="fa2b3-136">Setting enabled to `true` only causes PerfCounter.dll to reference the CategoryOptions registry setting.</span></span> <span data-ttu-id="fa2b3-137">CategoryOptions için varsayılan ayar, kategoriye özgü paylaşılan bellek kullanmaktır; Ancak, genel paylaşılan belleğin kullanılması gerektiğini belirtmek için CategoryOptions ' ı değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fa2b3-137">The default setting for CategoryOptions is to use category-specific shared memory; however, you can change CategoryOptions to indicate that global shared memory should be used.</span></span>  
  
 <span data-ttu-id="fa2b3-138">CategoryOptions ayarını içeren kayıt defteri anahtarı HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\\<CategoryName \> \ performanceşeklindedir.</span><span class="sxs-lookup"><span data-stu-id="fa2b3-138">The registry key that contains the CategoryOptions setting is HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\\<categoryName\>\Performance.</span></span> <span data-ttu-id="fa2b3-139">Varsayılan olarak, CategoryOptions 3 olarak ayarlanır, bu da kategoriye özgü paylaşılan belleği kullanmak PerfCounter.dll bildirir.</span><span class="sxs-lookup"><span data-stu-id="fa2b3-139">By default, CategoryOptions is set to 3, which instructs PerfCounter.dll to use category-specific shared memory.</span></span> <span data-ttu-id="fa2b3-140">CategoryOptions 0 olarak ayarlandıysa, PerfCounter.dll genel paylaşılan belleği kullanır.</span><span class="sxs-lookup"><span data-stu-id="fa2b3-140">If CategoryOptions is set to 0, PerfCounter.dll uses global shared memory.</span></span> <span data-ttu-id="fa2b3-141">Örnek verileri yalnızca oluşturulan örneğin adı, yeniden kullanılan örnekle aynıysa yeniden kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fa2b3-141">Instance data will be reused only if the name of the instance being created is identical to the instance being reused.</span></span> <span data-ttu-id="fa2b3-142">Tüm sürümler kategoriye yazabilecektir.</span><span class="sxs-lookup"><span data-stu-id="fa2b3-142">All versions will be able to write to the category.</span></span> <span data-ttu-id="fa2b3-143">Kategorili olarak 1 olarak ayarlanırsa, genel paylaşılan bellek kullanılır, ancak kategori adı, yeniden kullanılan kategoriyle aynı uzunluktadır sonra örnek verileri yeniden kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="fa2b3-143">If CategoryOptions is set to 1, global shared memory is used, but instance data can be reused if the category name is the same length as the category being reused.</span></span>  
  
 <span data-ttu-id="fa2b3-144">0 ve 1 ayarları, bellek sızıntılarına ve performans sayacı belleğinin doldurulmasına yol açabilir.</span><span class="sxs-lookup"><span data-stu-id="fa2b3-144">The settings 0 and 1 can lead to memory leaks and the filling up of performance counter memory.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fa2b3-145">Örnek</span><span class="sxs-lookup"><span data-stu-id="fa2b3-145">Example</span></span>  

 <span data-ttu-id="fa2b3-146">Aşağıdaki örnek, kategoriye özgü paylaşılan bellek kullanması gerekip gerekmediğini belirlemek için PerfCounter.dll kategorili kayıt defteri girişine başvurması gerektiğini nasıl belirleyeceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="fa2b3-146">The following example shows how to specify that PerfCounter.dll should reference the CategoryOptions registry entry to determine whether it should use category-specific shared memory.</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <forcePerformanceCounterUniqueSharedMemoryReads enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="fa2b3-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fa2b3-147">See also</span></span>

- [<span data-ttu-id="fa2b3-148">Çalışma zamanı ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="fa2b3-148">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="fa2b3-149">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="fa2b3-149">Configuration File Schema</span></span>](../index.md)
