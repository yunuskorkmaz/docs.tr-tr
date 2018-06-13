---
title: '&lt;forcePerformanceCounterUniqueSharedMemoryReads&gt; öğesi'
ms.date: 03/30/2017
helpviewer_keywords:
- forcePerformanceCounterUniqueSharedMemoryReads element
- <forcePerformanceCounterUniqueSharedMemoryReads> element
ms.assetid: 91149858-4810-4f65-9b48-468488172c9b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e1f041cbfb4195b2c649c3af4fa061bf63e227df
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32754294"
---
# <a name="ltforceperformancecounteruniquesharedmemoryreadsgt-element"></a><span data-ttu-id="a657b-102">&lt;forcePerformanceCounterUniqueSharedMemoryReads&gt; öğesi</span><span class="sxs-lookup"><span data-stu-id="a657b-102">&lt;forcePerformanceCounterUniqueSharedMemoryReads&gt; Element</span></span>
<span data-ttu-id="a657b-103">PerfCounter.dll CategoryOptions kayıt defteri ayarını bir .NET Framework sürüm 1.1 uygulamasında kategoriye özel paylaşılan bellek ya da genel bellek performans sayacı verilerini yüklemeye karar vermek için kullanıp kullanmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a657b-103">Specifies whether PerfCounter.dll uses the CategoryOptions registry setting in a .NET Framework version 1.1 application to determine whether to load performance counter data from category-specific shared memory or global memory.</span></span>  
  
 <span data-ttu-id="a657b-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="a657b-104">\<configuration></span></span>  
<span data-ttu-id="a657b-105">\<çalışma zamanı ></span><span class="sxs-lookup"><span data-stu-id="a657b-105">\<runtime></span></span>  
<span data-ttu-id="a657b-106">\<forcePerformanceCounterUniqueSharedMemoryReads ></span><span class="sxs-lookup"><span data-stu-id="a657b-106">\<forcePerformanceCounterUniqueSharedMemoryReads></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a657b-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a657b-107">Syntax</span></span>  
  
```xml  
<forcePerformanceCounterUniqueSharedMemoryReads   
enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a657b-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a657b-108">Attributes and Elements</span></span>  
 <span data-ttu-id="a657b-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a657b-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a657b-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a657b-110">Attributes</span></span>  
  
|<span data-ttu-id="a657b-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a657b-111">Attribute</span></span>|<span data-ttu-id="a657b-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a657b-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="a657b-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="a657b-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="a657b-114">PerfCounter.dll kategoriye özel paylaşılan bellek ya da genel bellek performans sayacı verilerini yüklemeye karar vermek için CategoryOptions kayıt defteri ayarını kullanıp kullanmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a657b-114">Indicates whether PerfCounter.dll uses the CategoryOptions registry setting to determine whether to load performance counter data from category-specific shared memory or global memory.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="a657b-115">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a657b-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="a657b-116">Değer</span><span class="sxs-lookup"><span data-stu-id="a657b-116">Value</span></span>|<span data-ttu-id="a657b-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a657b-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="a657b-118">PerfCounter.dll CategoryOptions kullanmaz kayıt defteri ayarı bu varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="a657b-118">PerfCounter.dll does not use the CategoryOptions registry setting This is the default.</span></span>|  
|`true`|<span data-ttu-id="a657b-119">PerfCounter.dll CategoryOptions kayıt defteri ayarını kullanın.</span><span class="sxs-lookup"><span data-stu-id="a657b-119">PerfCounter.dll does use the CategoryOptions registry setting.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a657b-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a657b-120">Child Elements</span></span>  
 <span data-ttu-id="a657b-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="a657b-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a657b-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a657b-122">Parent Elements</span></span>  
  
|<span data-ttu-id="a657b-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="a657b-123">Element</span></span>|<span data-ttu-id="a657b-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a657b-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="a657b-125">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="a657b-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="a657b-126">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="a657b-126">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a657b-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a657b-127">Remarks</span></span>  
 <span data-ttu-id="a657b-128">Önce .NET Framework sürümlerinde [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], işlemde yüklendi çalışma zamanı yüklendi PerfCounter.dll sürümü corresponded.</span><span class="sxs-lookup"><span data-stu-id="a657b-128">In versions of the .NET Framework before the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], the version of PerfCounter.dll that was loaded corresponded to the runtime that was loaded in the process.</span></span> <span data-ttu-id="a657b-129">Bir bilgisayar hem de .NET Framework sürüm 1.1 sahip ve [!INCLUDE[dnprdnlong](../../../../../includes/dnprdnlong-md.md)] yüklü .NET Framework 1.1 uygulamayı PerfCounter.dll .NET Framework 1.1 sürümünü yüklemek.</span><span class="sxs-lookup"><span data-stu-id="a657b-129">If a computer had both the .NET Framework version 1.1 and the [!INCLUDE[dnprdnlong](../../../../../includes/dnprdnlong-md.md)] installed, a .NET Framework 1.1 application would load the .NET Framework 1.1 version of PerfCounter.dll.</span></span> <span data-ttu-id="a657b-130">İle başlayarak [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], PerfCounter.dll yüklü en son sürümü yüklendi.</span><span class="sxs-lookup"><span data-stu-id="a657b-130">Starting with the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], the newest installed version of PerfCounter.dll is loaded.</span></span> <span data-ttu-id="a657b-131">Bir .NET Framework 1.1 uygulamasını yükleyecek yani [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] PerfCounter.dll sürümü varsa [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] bilgisayara yüklendi.</span><span class="sxs-lookup"><span data-stu-id="a657b-131">This means that a .NET Framework 1.1 application will load the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] version of PerfCounter.dll if the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] is installed on the computer.</span></span>  
  
 <span data-ttu-id="a657b-132">İle başlayarak [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], performans sayaçları kullanırken PerfCounter.dll CategoryOptions kayıt defteri girdisini paylaşılan bellek kategoriye özel veya genel paylaşılan bellek gözükmelidir olup olmadığını belirlemek her bir sağlayıcı için denetler.</span><span class="sxs-lookup"><span data-stu-id="a657b-132">Starting with the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], when consuming performance counters, PerfCounter.dll checks the CategoryOptions registry entry for each provider to determine whether it should read from category-specific shared memory or global shared memory.</span></span> <span data-ttu-id="a657b-133">.NET Framework 1.1 PerfCounter.dll kategoriye özel paylaşılan bellek farkında olmadığından bu kayıt defteri girişi okumaz; her zaman, genel Paylaşılan bellekten okur.</span><span class="sxs-lookup"><span data-stu-id="a657b-133">The .NET Framework 1.1 PerfCounter.dll does not read that registry entry, because it is not aware of category-specific shared memory; it always reads from global shared memory.</span></span>  
  
 <span data-ttu-id="a657b-134">Geriye dönük uyumluluk için [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] PerfCounter.dll bir .NET Framework 1.1 uygulamasında çalıştırırken CategoryOptions kayıt defteri girdisini denetlemez.</span><span class="sxs-lookup"><span data-stu-id="a657b-134">For backward compatibility, the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] PerfCounter.dll does not check the CategoryOptions registry entry when running in a .NET Framework 1.1 application.</span></span> <span data-ttu-id="a657b-135">Bu, yalnızca .NET Framework 1.1 PerfCounter.dll gibi genel paylaşılan bellek kullanır.</span><span class="sxs-lookup"><span data-stu-id="a657b-135">It simply uses global shared memory, just like the .NET Framework 1.1 PerfCounter.dll.</span></span> <span data-ttu-id="a657b-136">Ancak, söyleyebilirsiniz [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] kayıt defteri ayarını etkinleştirerek denetlemek için PerfCounter.dll `<forcePerformanceCounterUniqueSharedMemoryReads>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="a657b-136">However, you can instruct the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] PerfCounter.dll to check the registry setting by enabling the `<forcePerformanceCounterUniqueSharedMemoryReads>` element.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a657b-137">Etkinleştirme `<forcePerformanceCounterUniqueSharedMemoryReads>` öğesi garanti etmez kategoriye özel paylaşılan bellek kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="a657b-137">Enabling the `<forcePerformanceCounterUniqueSharedMemoryReads>` element does not guarantee that category-specific shared memory will be used.</span></span> <span data-ttu-id="a657b-138">Ayar için etkin `true` yalnızca CategoryOptions kayıt defteri ayarı başvurmak PerfCounter.dll neden olur.</span><span class="sxs-lookup"><span data-stu-id="a657b-138">Setting enabled to `true` only causes PerfCounter.dll to reference the CategoryOptions registry setting.</span></span> <span data-ttu-id="a657b-139">CategoryOptions için varsayılan ayar kategorisi özgü paylaşılan bellek kullanmaktır; Ancak, genel paylaşılan bellek kullanılması gerektiğini belirtmek için CategoryOptions değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a657b-139">The default setting for CategoryOptions is to use category-specific shared memory; however, you can change CategoryOptions to indicate that global shared memory should be used.</span></span>  
  
 <span data-ttu-id="a657b-140">HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services CategoryOptions ayarını içeren kayıt defteri anahtarıdır\\< categoryName\>\Performance.</span><span class="sxs-lookup"><span data-stu-id="a657b-140">The registry key that contains the CategoryOptions setting is HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\\<categoryName\>\Performance.</span></span> <span data-ttu-id="a657b-141">Varsayılan olarak, CategoryOptions 3, hangi PerfCounter.dll bildirir kategoriye özel paylaşılan bellek kullanmak üzere ayarlanmış.</span><span class="sxs-lookup"><span data-stu-id="a657b-141">By default, CategoryOptions is set to 3, which instructs PerfCounter.dll to use category-specific shared memory.</span></span> <span data-ttu-id="a657b-142">CategoryOptions 0 olarak ayarlarsanız, PerfCounter.dll genel paylaşılan bellek kullanır.</span><span class="sxs-lookup"><span data-stu-id="a657b-142">If CategoryOptions is set to 0, PerfCounter.dll uses global shared memory.</span></span> <span data-ttu-id="a657b-143">Oluşturulan örneğinin adını yeniden kullanılıyor örneğine aynı ise örnek verileri yeniden kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a657b-143">Instance data will be reused only if the name of the instance being created is identical to the instance being reused.</span></span> <span data-ttu-id="a657b-144">Tüm sürümleri için kategori yazma kuramaz.</span><span class="sxs-lookup"><span data-stu-id="a657b-144">All versions will be able to write to the category.</span></span> <span data-ttu-id="a657b-145">CategoryOptions 1 olarak ayarlanırsa, genel paylaşılan bellek kullanılır, ancak aynı uzunlukta yeniden kullanılıyor kategorisi kategori adı ise, örnek verileri yeniden kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a657b-145">If CategoryOptions is set to 1, global shared memory is used, but instance data can be reused if the category name is the same length as the category being reused.</span></span>  
  
 <span data-ttu-id="a657b-146">0 ve 1 ayarları bellek sızıntıları ve yukarı doldurma performans sayacı bellek yol açabilir.</span><span class="sxs-lookup"><span data-stu-id="a657b-146">The settings 0 and 1 can lead to memory leaks and the filling up of performance counter memory.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a657b-147">Örnek</span><span class="sxs-lookup"><span data-stu-id="a657b-147">Example</span></span>  
 <span data-ttu-id="a657b-148">Aşağıdaki örnek, PerfCounter.dll kategori özgü paylaşılan bellek kullanması gerekip gerekmediğini belirlemek için CategoryOptions kayıt defteri girdisini başvurmalısınız belirtin gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="a657b-148">The following example shows how to specify that PerfCounter.dll should reference the CategoryOptions registry entry to determine whether it should use category-specific shared memory.</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <forcePerformanceCounterUniqueSharedMemoryReads enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a657b-149">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a657b-149">See Also</span></span>  
 [<span data-ttu-id="a657b-150">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="a657b-150">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="a657b-151">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="a657b-151">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
