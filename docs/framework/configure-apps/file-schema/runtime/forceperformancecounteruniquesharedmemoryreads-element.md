---
title: <forcePerformanceCounterUniqueSharedMemoryReads> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- forcePerformanceCounterUniqueSharedMemoryReads element
- <forcePerformanceCounterUniqueSharedMemoryReads> element
ms.assetid: 91149858-4810-4f65-9b48-468488172c9b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1d4a205f643c844b2fe77d3aa5211b4bc1f322fd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59186972"
---
# <a name="forceperformancecounteruniquesharedmemoryreads-element"></a><span data-ttu-id="2e2b1-102">\<forcePerformanceCounterUniqueSharedMemoryReads> Element</span><span class="sxs-lookup"><span data-stu-id="2e2b1-102">\<forcePerformanceCounterUniqueSharedMemoryReads> Element</span></span>
<span data-ttu-id="2e2b1-103">PerfCounter.dll CategoryOptions kayıt defteri ayarı bir .NET Framework sürüm 1.1 uygulamasında kategoriye özgü paylaşılan bellek ya da genel bellek performans sayacı verilerini yüklemek karar vermek için kullanıp kullanmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="2e2b1-103">Specifies whether PerfCounter.dll uses the CategoryOptions registry setting in a .NET Framework version 1.1 application to determine whether to load performance counter data from category-specific shared memory or global memory.</span></span>  
  
 <span data-ttu-id="2e2b1-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="2e2b1-104">\<configuration></span></span>  
<span data-ttu-id="2e2b1-105">\<çalışma zamanı ></span><span class="sxs-lookup"><span data-stu-id="2e2b1-105">\<runtime></span></span>  
<span data-ttu-id="2e2b1-106">\<forcePerformanceCounterUniqueSharedMemoryReads></span><span class="sxs-lookup"><span data-stu-id="2e2b1-106">\<forcePerformanceCounterUniqueSharedMemoryReads></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e2b1-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2e2b1-107">Syntax</span></span>  
  
```xml  
<forcePerformanceCounterUniqueSharedMemoryReads   
enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2e2b1-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="2e2b1-108">Attributes and Elements</span></span>  
 <span data-ttu-id="2e2b1-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2e2b1-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2e2b1-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="2e2b1-110">Attributes</span></span>  
  
|<span data-ttu-id="2e2b1-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="2e2b1-111">Attribute</span></span>|<span data-ttu-id="2e2b1-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2e2b1-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="2e2b1-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="2e2b1-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="2e2b1-114">PerfCounter.dll kategoriye özgü paylaşılan bellek ya da genel bellek performans sayacı verilerini yüklemek karar vermek için CategoryOptions kayıt defteri ayarı kullanıp kullanmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="2e2b1-114">Indicates whether PerfCounter.dll uses the CategoryOptions registry setting to determine whether to load performance counter data from category-specific shared memory or global memory.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="2e2b1-115">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="2e2b1-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="2e2b1-116">Değer</span><span class="sxs-lookup"><span data-stu-id="2e2b1-116">Value</span></span>|<span data-ttu-id="2e2b1-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2e2b1-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="2e2b1-118">PerfCounter.dll CategoryOptions kullanmayan kayıt defteri ayarı bu varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="2e2b1-118">PerfCounter.dll does not use the CategoryOptions registry setting This is the default.</span></span>|  
|`true`|<span data-ttu-id="2e2b1-119">PerfCounter.dll CategoryOptions kayıt defteri ayarını kullanın.</span><span class="sxs-lookup"><span data-stu-id="2e2b1-119">PerfCounter.dll does use the CategoryOptions registry setting.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2e2b1-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="2e2b1-120">Child Elements</span></span>  
 <span data-ttu-id="2e2b1-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="2e2b1-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2e2b1-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="2e2b1-122">Parent Elements</span></span>  
  
|<span data-ttu-id="2e2b1-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="2e2b1-123">Element</span></span>|<span data-ttu-id="2e2b1-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2e2b1-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="2e2b1-125">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="2e2b1-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="2e2b1-126">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="2e2b1-126">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2e2b1-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2e2b1-127">Remarks</span></span>  
 <span data-ttu-id="2e2b1-128">Önce .NET Framework sürümlerinde [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], işlemde yüklü çalışma zamanı sürümü yüklendi PerfCounter.dll corresponded.</span><span class="sxs-lookup"><span data-stu-id="2e2b1-128">In versions of the .NET Framework before the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], the version of PerfCounter.dll that was loaded corresponded to the runtime that was loaded in the process.</span></span> <span data-ttu-id="2e2b1-129">Bir bilgisayar hem de .NET Framework sürüm 1.1 sahip olduğu ve [!INCLUDE[dnprdnlong](../../../../../includes/dnprdnlong-md.md)] yüklü .NET Framework 1.1 uygulama PerfCounter.dll .NET Framework 1.1 sürümü yüklenir.</span><span class="sxs-lookup"><span data-stu-id="2e2b1-129">If a computer had both the .NET Framework version 1.1 and the [!INCLUDE[dnprdnlong](../../../../../includes/dnprdnlong-md.md)] installed, a .NET Framework 1.1 application would load the .NET Framework 1.1 version of PerfCounter.dll.</span></span> <span data-ttu-id="2e2b1-130">İle başlayarak [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], PerfCounter.dll en yeni yüklü sürümü yüklendi.</span><span class="sxs-lookup"><span data-stu-id="2e2b1-130">Starting with the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], the newest installed version of PerfCounter.dll is loaded.</span></span> <span data-ttu-id="2e2b1-131">.NET Framework 1.1 uygulama yüklenir yani [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] PerfCounter.dll sürümünü, [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] bilgisayara yüklendi.</span><span class="sxs-lookup"><span data-stu-id="2e2b1-131">This means that a .NET Framework 1.1 application will load the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] version of PerfCounter.dll if the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] is installed on the computer.</span></span>  
  
 <span data-ttu-id="2e2b1-132">İle başlayarak [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], performans sayaçları tüketildiğinde, paylaşılan bellek kategorisi özel veya genel paylaşılan bellek gözükmelidir olup olmadığını belirlemek her bir sağlayıcı CategoryOptions kayıt defteri girişini PerfCounter.dll denetler.</span><span class="sxs-lookup"><span data-stu-id="2e2b1-132">Starting with the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], when consuming performance counters, PerfCounter.dll checks the CategoryOptions registry entry for each provider to determine whether it should read from category-specific shared memory or global shared memory.</span></span> <span data-ttu-id="2e2b1-133">Kategori özgü paylaşılan bellek farkında olmadığından System.Numerics.vectors.dll o kayıt defteri girdisini .NET Framework 1.1 PerfCounter.dll okumaz; her zaman, paylaşılan genel bellekten okur.</span><span class="sxs-lookup"><span data-stu-id="2e2b1-133">The .NET Framework 1.1 PerfCounter.dll does not read that registry entry, because it is not aware of category-specific shared memory; it always reads from global shared memory.</span></span>  
  
 <span data-ttu-id="2e2b1-134">Geriye dönük uyumluluk için [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] PerfCounter.dll bir .NET Framework 1.1 uygulamasında çalışırken CategoryOptions kayıt defteri girdisini denetlemez.</span><span class="sxs-lookup"><span data-stu-id="2e2b1-134">For backward compatibility, the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] PerfCounter.dll does not check the CategoryOptions registry entry when running in a .NET Framework 1.1 application.</span></span> <span data-ttu-id="2e2b1-135">Yalnızca, .NET Framework 1.1 PerfCounter.dll gibi genel paylaşılan bellek kullanır.</span><span class="sxs-lookup"><span data-stu-id="2e2b1-135">It simply uses global shared memory, just like the .NET Framework 1.1 PerfCounter.dll.</span></span> <span data-ttu-id="2e2b1-136">Ancak, bildirebilirsiniz [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] kayıt defteri ayarı etkinleştirerek denetlemek için PerfCounter.dll `<forcePerformanceCounterUniqueSharedMemoryReads>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="2e2b1-136">However, you can instruct the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] PerfCounter.dll to check the registry setting by enabling the `<forcePerformanceCounterUniqueSharedMemoryReads>` element.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2e2b1-137">Etkinleştirme `<forcePerformanceCounterUniqueSharedMemoryReads>` öğesi kategorisi özgü paylaşılan bellek kullanılacak garantilemez.</span><span class="sxs-lookup"><span data-stu-id="2e2b1-137">Enabling the `<forcePerformanceCounterUniqueSharedMemoryReads>` element does not guarantee that category-specific shared memory will be used.</span></span> <span data-ttu-id="2e2b1-138">Ayar için etkin `true` PerfCounter.dll CategoryOptions kayıt defteri ayarı başvurmak yalnızca neden olur.</span><span class="sxs-lookup"><span data-stu-id="2e2b1-138">Setting enabled to `true` only causes PerfCounter.dll to reference the CategoryOptions registry setting.</span></span> <span data-ttu-id="2e2b1-139">Kategori özgü paylaşılan bellek kullanmasına CategoryOptions için varsayılan ayar olan; Ancak, genel paylaşılan bellek kullanılması gerektiğini belirtmek için CategoryOptions değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2e2b1-139">The default setting for CategoryOptions is to use category-specific shared memory; however, you can change CategoryOptions to indicate that global shared memory should be used.</span></span>  
  
 <span data-ttu-id="2e2b1-140">HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services CategoryOptions ayarları içeren kayıt defteri anahtarıdır\\< categoryName\>\Performance.</span><span class="sxs-lookup"><span data-stu-id="2e2b1-140">The registry key that contains the CategoryOptions setting is HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\\<categoryName\>\Performance.</span></span> <span data-ttu-id="2e2b1-141">Varsayılan olarak, CategoryOptions 3'e hangi PerfCounter.dll bildirir kategoriye özgü paylaşılan bellek kullanacak şekilde ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="2e2b1-141">By default, CategoryOptions is set to 3, which instructs PerfCounter.dll to use category-specific shared memory.</span></span> <span data-ttu-id="2e2b1-142">CategoryOptions 0 olarak ayarlarsanız, PerfCounter.dll genel paylaşılan bellek kullanır.</span><span class="sxs-lookup"><span data-stu-id="2e2b1-142">If CategoryOptions is set to 0, PerfCounter.dll uses global shared memory.</span></span> <span data-ttu-id="2e2b1-143">Örnek verileri yeniden oluşturulan örneğinin adını yeniden kullanılıyor örnekle aynı ise kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2e2b1-143">Instance data will be reused only if the name of the instance being created is identical to the instance being reused.</span></span> <span data-ttu-id="2e2b1-144">Tüm sürümler kategorisine yazma mümkün olacaktır.</span><span class="sxs-lookup"><span data-stu-id="2e2b1-144">All versions will be able to write to the category.</span></span> <span data-ttu-id="2e2b1-145">CategoryOptions 1 olarak ayarlarsanız, genel paylaşılan bellek kullanılır, ancak aynı uzunlukta yeniden kullanılıyor kategorisi kategori adı ise, örnek verileri yeniden kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2e2b1-145">If CategoryOptions is set to 1, global shared memory is used, but instance data can be reused if the category name is the same length as the category being reused.</span></span>  
  
 <span data-ttu-id="2e2b1-146">0 ile 1 ayarları, bellek sızıntılarını ve yukarı doldurmanın performans sayacı bellek neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="2e2b1-146">The settings 0 and 1 can lead to memory leaks and the filling up of performance counter memory.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2e2b1-147">Örnek</span><span class="sxs-lookup"><span data-stu-id="2e2b1-147">Example</span></span>  
 <span data-ttu-id="2e2b1-148">Aşağıdaki örnek, PerfCounter.dll kategoriye özgü paylaşılan bellek kullanması gerekip gerekmediğini belirlemek için CategoryOptions kayıt defteri girdisini başvurmalıdır belirtmek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2e2b1-148">The following example shows how to specify that PerfCounter.dll should reference the CategoryOptions registry entry to determine whether it should use category-specific shared memory.</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <forcePerformanceCounterUniqueSharedMemoryReads enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2e2b1-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2e2b1-149">See also</span></span>

- [<span data-ttu-id="2e2b1-150">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="2e2b1-150">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="2e2b1-151">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="2e2b1-151">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
