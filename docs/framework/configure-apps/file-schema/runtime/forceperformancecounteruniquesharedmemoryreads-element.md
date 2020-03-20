---
title: <forcePerformanceCounterUniqueSharedMemoryReads> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- forcePerformanceCounterUniqueSharedMemoryReads element
- <forcePerformanceCounterUniqueSharedMemoryReads> element
ms.assetid: 91149858-4810-4f65-9b48-468488172c9b
ms.openlocfilehash: 742b444c445ba67d6977b622e615a6a8f591826e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154146"
---
# <a name="forceperformancecounteruniquesharedmemoryreads-element"></a><span data-ttu-id="75f6e-102">\<forcePerformanceCounterUniqueSharedMemoryReads> Öğesi</span><span class="sxs-lookup"><span data-stu-id="75f6e-102">\<forcePerformanceCounterUniqueSharedMemoryReads> Element</span></span>
<span data-ttu-id="75f6e-103">PerfCounter.dll'nin kategoriye özgü paylaşılan bellekten veya genel bellekten performans sayacı verilerini yükleyip yüklemeyeceğini belirlemek için bir .NET Framework sürüm 1.1 uygulamasında CategoryOptions kayıt defteri ayarını kullanıp kullanmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="75f6e-103">Specifies whether PerfCounter.dll uses the CategoryOptions registry setting in a .NET Framework version 1.1 application to determine whether to load performance counter data from category-specific shared memory or global memory.</span></span>  
  
<span data-ttu-id="75f6e-104">[**\<yapılandırma>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="75f6e-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="75f6e-105">&nbsp;&nbsp;[**\<çalışma zamanı>**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="75f6e-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="75f6e-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<forcePerformanceCounterUniqueSharedMemoryReads>**</span><span class="sxs-lookup"><span data-stu-id="75f6e-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<forcePerformanceCounterUniqueSharedMemoryReads>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75f6e-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="75f6e-107">Syntax</span></span>  
  
```xml  
<forcePerformanceCounterUniqueSharedMemoryReads
enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="75f6e-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="75f6e-108">Attributes and Elements</span></span>  
 <span data-ttu-id="75f6e-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="75f6e-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="75f6e-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="75f6e-110">Attributes</span></span>  
  
|<span data-ttu-id="75f6e-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="75f6e-111">Attribute</span></span>|<span data-ttu-id="75f6e-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="75f6e-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="75f6e-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="75f6e-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="75f6e-114">PerfCounter.dll'nin kategoriye özgü paylaşılan bellekten veya genel bellekten performans sayacı verilerini yükleyip yüklemeyeceğini belirlemek için CategoryOptions kayıt defteri ayarını kullanıp kullanmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="75f6e-114">Indicates whether PerfCounter.dll uses the CategoryOptions registry setting to determine whether to load performance counter data from category-specific shared memory or global memory.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="75f6e-115">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="75f6e-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="75f6e-116">Değer</span><span class="sxs-lookup"><span data-stu-id="75f6e-116">Value</span></span>|<span data-ttu-id="75f6e-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="75f6e-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="75f6e-118">PerfCounter.dll CategoryOptions kayıt defteri ayarı bu varsayılan kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="75f6e-118">PerfCounter.dll does not use the CategoryOptions registry setting This is the default.</span></span>|  
|`true`|<span data-ttu-id="75f6e-119">PerfCounter.dll CategoryOptions kayıt defteri ayarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="75f6e-119">PerfCounter.dll does use the CategoryOptions registry setting.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="75f6e-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="75f6e-120">Child Elements</span></span>  
 <span data-ttu-id="75f6e-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="75f6e-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="75f6e-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="75f6e-122">Parent Elements</span></span>  
  
|<span data-ttu-id="75f6e-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="75f6e-123">Element</span></span>|<span data-ttu-id="75f6e-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="75f6e-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="75f6e-125">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="75f6e-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="75f6e-126">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="75f6e-126">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="75f6e-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="75f6e-127">Remarks</span></span>  
 <span data-ttu-id="75f6e-128">.NET Framework 4'ten önceki .NET Framework sürümlerinde, yüklenilen PerfCounter.dll sürümü, işlemde yüklenen çalışma süresine karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="75f6e-128">In versions of the .NET Framework before the .NET Framework 4, the version of PerfCounter.dll that was loaded corresponded to the runtime that was loaded in the process.</span></span> <span data-ttu-id="75f6e-129">Bir bilgisayarda hem .NET Framework sürüm 1.1 hem de .NET Framework 2.0 yüklü olsaydı, bir .NET Framework 1.1 uygulaması PerfCounter.dll'nin .NET Framework 1.1 sürümünü yükler.</span><span class="sxs-lookup"><span data-stu-id="75f6e-129">If a computer had both the .NET Framework version 1.1 and the .NET Framework 2.0 installed, a .NET Framework 1.1 application would load the .NET Framework 1.1 version of PerfCounter.dll.</span></span> <span data-ttu-id="75f6e-130">.NET Framework 4'ten başlayarak, PerfCounter.dll'nin en yeni yüklü sürümü yüklenir.</span><span class="sxs-lookup"><span data-stu-id="75f6e-130">Starting with the .NET Framework 4, the newest installed version of PerfCounter.dll is loaded.</span></span> <span data-ttu-id="75f6e-131">Bu, bilgisayara .NET Framework 4 yüklenirse ,NET Framework 1.1 uygulamasının PerfCounter.dll'nin .NET Framework 4 sürümünü yükleyeceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="75f6e-131">This means that a .NET Framework 1.1 application will load the .NET Framework 4 version of PerfCounter.dll if the .NET Framework 4 is installed on the computer.</span></span>  
  
 <span data-ttu-id="75f6e-132">Performans sayaçlarını tüketirken .NET Framework 4'ten başlayarak PerfCounter.dll, kategoriye özgü paylaşılan bellekten mi yoksa genel paylaşılan bellekten mi okunması gerektiğini belirlemek için her sağlayıcı için CategoryOptions kayıt defteri girişini denetler.</span><span class="sxs-lookup"><span data-stu-id="75f6e-132">Starting with the .NET Framework 4, when consuming performance counters, PerfCounter.dll checks the CategoryOptions registry entry for each provider to determine whether it should read from category-specific shared memory or global shared memory.</span></span> <span data-ttu-id="75f6e-133">.NET Framework 1.1 PerfCounter.dll, kategoriye özgü paylaşılan belleğin farkında olmadığından, kayıt defteri girişini okumaz; her zaman genel paylaşılan bellekten okur.</span><span class="sxs-lookup"><span data-stu-id="75f6e-133">The .NET Framework 1.1 PerfCounter.dll does not read that registry entry, because it is not aware of category-specific shared memory; it always reads from global shared memory.</span></span>  
  
 <span data-ttu-id="75f6e-134">Geriye dönük uyumluluk için .NET Framework 4 PerfCounter.dll, .NET Framework 1.1 uygulamasında çalışırken CategoryOptions kayıt defteri girişini denetlemez.</span><span class="sxs-lookup"><span data-stu-id="75f6e-134">For backward compatibility, the .NET Framework 4 PerfCounter.dll does not check the CategoryOptions registry entry when running in a .NET Framework 1.1 application.</span></span> <span data-ttu-id="75f6e-135">Sadece .NET Framework 1.1 PerfCounter.dll gibi, küresel paylaşılan bellek kullanır.</span><span class="sxs-lookup"><span data-stu-id="75f6e-135">It simply uses global shared memory, just like the .NET Framework 1.1 PerfCounter.dll.</span></span> <span data-ttu-id="75f6e-136">Ancak, .NET Framework 4 PerfCounter.dll öğesini etkinleştirerek kayıt defteri `<forcePerformanceCounterUniqueSharedMemoryReads>` ayarını denetlemesi için talimat verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="75f6e-136">However, you can instruct the .NET Framework 4 PerfCounter.dll to check the registry setting by enabling the `<forcePerformanceCounterUniqueSharedMemoryReads>` element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="75f6e-137">Öğeyi `<forcePerformanceCounterUniqueSharedMemoryReads>` etkinleştirmek, kategoriye özgü paylaşılan belleğin kullanılacağını garanti etmez.</span><span class="sxs-lookup"><span data-stu-id="75f6e-137">Enabling the `<forcePerformanceCounterUniqueSharedMemoryReads>` element does not guarantee that category-specific shared memory will be used.</span></span> <span data-ttu-id="75f6e-138">Yalnızca PerfCounter.dll'nin CategoryOptions kayıt defteri ayarına başvurmasına neden olacak şekilde etkinleştirildi. `true`</span><span class="sxs-lookup"><span data-stu-id="75f6e-138">Setting enabled to `true` only causes PerfCounter.dll to reference the CategoryOptions registry setting.</span></span> <span data-ttu-id="75f6e-139">CategoryOptions için varsayılan ayar kategoriye özgü paylaşılan bellek kullanmaktır; ancak, genel paylaşılan belleğin kullanılması gerektiğini belirtmek için CategoryOptions'ı değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="75f6e-139">The default setting for CategoryOptions is to use category-specific shared memory; however, you can change CategoryOptions to indicate that global shared memory should be used.</span></span>  
  
 <span data-ttu-id="75f6e-140">CategoryOptions ayarını içeren kayıt defteri anahtarı\\ HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\><categoryName \Performance'tır.</span><span class="sxs-lookup"><span data-stu-id="75f6e-140">The registry key that contains the CategoryOptions setting is HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\\<categoryName\>\Performance.</span></span> <span data-ttu-id="75f6e-141">Varsayılan olarak, CategoryOptions 3 olarak ayarlanır ve bu da PerfCounter.dll'ye kategoriye özgü paylaşılan belleği kullanmasını bildirir.</span><span class="sxs-lookup"><span data-stu-id="75f6e-141">By default, CategoryOptions is set to 3, which instructs PerfCounter.dll to use category-specific shared memory.</span></span> <span data-ttu-id="75f6e-142">CategoryOptions 0 olarak ayarlanmışsa, PerfCounter.dll genel paylaşılan bellek kullanır.</span><span class="sxs-lookup"><span data-stu-id="75f6e-142">If CategoryOptions is set to 0, PerfCounter.dll uses global shared memory.</span></span> <span data-ttu-id="75f6e-143">Örnek veriler, yalnızca oluşturulan örneğin adı yeniden kullanılan örnekle aynıysa yeniden kullanılır.</span><span class="sxs-lookup"><span data-stu-id="75f6e-143">Instance data will be reused only if the name of the instance being created is identical to the instance being reused.</span></span> <span data-ttu-id="75f6e-144">Tüm sürümler kategoriye yazabilecektir.</span><span class="sxs-lookup"><span data-stu-id="75f6e-144">All versions will be able to write to the category.</span></span> <span data-ttu-id="75f6e-145">CategoryOptions 1 olarak ayarlanmışsa, genel paylaşılan bellek kullanılır, ancak kategori adı yeniden kullanılan kategoriyle aynı uzunluktaysa örnek verileri yeniden kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="75f6e-145">If CategoryOptions is set to 1, global shared memory is used, but instance data can be reused if the category name is the same length as the category being reused.</span></span>  
  
 <span data-ttu-id="75f6e-146">0 ve 1 ayarları bellek sızıntılarına ve performans sayacı belleği doldurmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="75f6e-146">The settings 0 and 1 can lead to memory leaks and the filling up of performance counter memory.</span></span>  
  
## <a name="example"></a><span data-ttu-id="75f6e-147">Örnek</span><span class="sxs-lookup"><span data-stu-id="75f6e-147">Example</span></span>  
 <span data-ttu-id="75f6e-148">Aşağıdaki örnekte, PerfCounter.dll'nin kategoriye özgü paylaşılan bellek kullanıp kullanmaması gerektiğini belirlemek için CategoryOptions kayıt defteri girişine başvurması gerektiğinin nasıl belirtilen bir şekilde belirtilen.</span><span class="sxs-lookup"><span data-stu-id="75f6e-148">The following example shows how to specify that PerfCounter.dll should reference the CategoryOptions registry entry to determine whether it should use category-specific shared memory.</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <forcePerformanceCounterUniqueSharedMemoryReads enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="75f6e-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="75f6e-149">See also</span></span>

- [<span data-ttu-id="75f6e-150">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="75f6e-150">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="75f6e-151">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="75f6e-151">Configuration File Schema</span></span>](../index.md)
