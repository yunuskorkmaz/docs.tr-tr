---
title: <forcePerformanceCounterUniqueSharedMemoryReads> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- forcePerformanceCounterUniqueSharedMemoryReads element
- <forcePerformanceCounterUniqueSharedMemoryReads> element
ms.assetid: 91149858-4810-4f65-9b48-468488172c9b
ms.openlocfilehash: efa6dce1035f7d2cf63b74c6a03d911b5dede722
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73116947"
---
# <a name="forceperformancecounteruniquesharedmemoryreads-element"></a><span data-ttu-id="2a41a-102">\<forcePerformanceCounterUniqueSharedMemoryReads > öğesi</span><span class="sxs-lookup"><span data-stu-id="2a41a-102">\<forcePerformanceCounterUniqueSharedMemoryReads> Element</span></span>
<span data-ttu-id="2a41a-103">PerfCounter. dll ' nin, performans sayacı verilerinin kategoriye özgü paylaşılan bellekten veya genel bellekten yüklenip yüklenmeyeceğini belirleme .NET Framework sürüm 1,1 uygulamasında CategoryOptions kayıt defteri ayarını kullanıp kullanmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="2a41a-103">Specifies whether PerfCounter.dll uses the CategoryOptions registry setting in a .NET Framework version 1.1 application to determine whether to load performance counter data from category-specific shared memory or global memory.</span></span>  
  
<span data-ttu-id="2a41a-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="2a41a-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="2a41a-105">&nbsp; &nbsp;[ **\<runtime >** ](runtime-element.md) </span><span class="sxs-lookup"><span data-stu-id="2a41a-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="2a41a-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<forcePerformanceCounterUniqueSharedMemoryReads >**</span><span class="sxs-lookup"><span data-stu-id="2a41a-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<forcePerformanceCounterUniqueSharedMemoryReads>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a41a-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2a41a-107">Syntax</span></span>  
  
```xml  
<forcePerformanceCounterUniqueSharedMemoryReads   
enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2a41a-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="2a41a-108">Attributes and Elements</span></span>  
 <span data-ttu-id="2a41a-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2a41a-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2a41a-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="2a41a-110">Attributes</span></span>  
  
|<span data-ttu-id="2a41a-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="2a41a-111">Attribute</span></span>|<span data-ttu-id="2a41a-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2a41a-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="2a41a-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="2a41a-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="2a41a-114">PerfCounter. dll ' nin, performans sayacı verilerinin kategoriye özgü paylaşılan bellekten mi yoksa genel bellekten mi yükleneceğini öğrenmek için CategoryOptions kayıt defteri ayarını kullanıp kullanmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="2a41a-114">Indicates whether PerfCounter.dll uses the CategoryOptions registry setting to determine whether to load performance counter data from category-specific shared memory or global memory.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="2a41a-115">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="2a41a-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="2a41a-116">Değer</span><span class="sxs-lookup"><span data-stu-id="2a41a-116">Value</span></span>|<span data-ttu-id="2a41a-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2a41a-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="2a41a-118">PerfCounter. dll, CategoryOptions kayıt defteri ayarını kullanmaz. bu varsayılan ayardır.</span><span class="sxs-lookup"><span data-stu-id="2a41a-118">PerfCounter.dll does not use the CategoryOptions registry setting This is the default.</span></span>|  
|`true`|<span data-ttu-id="2a41a-119">PerfCounter. dll, CategoryOptions kayıt defteri ayarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="2a41a-119">PerfCounter.dll does use the CategoryOptions registry setting.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2a41a-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="2a41a-120">Child Elements</span></span>  
 <span data-ttu-id="2a41a-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="2a41a-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2a41a-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="2a41a-122">Parent Elements</span></span>  
  
|<span data-ttu-id="2a41a-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="2a41a-123">Element</span></span>|<span data-ttu-id="2a41a-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2a41a-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="2a41a-125">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="2a41a-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="2a41a-126">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="2a41a-126">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2a41a-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2a41a-127">Remarks</span></span>  
 <span data-ttu-id="2a41a-128">.NET Framework 4 ' ün öncesindeki .NET Framework sürümlerinde, yüklenmiş olan PerfCounter. dll sürümü, işleme yüklenmiş çalışma zamanına karşılık gelen sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="2a41a-128">In versions of the .NET Framework before the .NET Framework 4, the version of PerfCounter.dll that was loaded corresponded to the runtime that was loaded in the process.</span></span> <span data-ttu-id="2a41a-129">Bir bilgisayarda .NET Framework sürüm 1,1 ve .NET Framework 2,0 yüklüyse, bir .NET Framework 1,1 uygulaması PerfCounter. dll ' nin .NET Framework 1,1 sürümünü yükler.</span><span class="sxs-lookup"><span data-stu-id="2a41a-129">If a computer had both the .NET Framework version 1.1 and the .NET Framework 2.0 installed, a .NET Framework 1.1 application would load the .NET Framework 1.1 version of PerfCounter.dll.</span></span> <span data-ttu-id="2a41a-130">.NET Framework 4 ' te başlayarak, PerfCounter. dll ' nin en yeni yüklü sürümü yüklenir.</span><span class="sxs-lookup"><span data-stu-id="2a41a-130">Starting with the .NET Framework 4, the newest installed version of PerfCounter.dll is loaded.</span></span> <span data-ttu-id="2a41a-131">Bu, .NET Framework 1,1 uygulaması, bilgisayarda .NET Framework 4 yüklüyse PerfCounter. dll ' nin .NET Framework 4 sürümünü yükleyecek anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="2a41a-131">This means that a .NET Framework 1.1 application will load the .NET Framework 4 version of PerfCounter.dll if the .NET Framework 4 is installed on the computer.</span></span>  
  
 <span data-ttu-id="2a41a-132">.NET Framework 4 ' ten başlayarak, performans sayaçlarını tükettiği için PerfCounter. dll, her bir sağlayıcının kategorilere özgü paylaşılan bellekten veya genel paylaşılan bellekten okunup okunmayacağını belirlemede bu kayıt defteri girişini denetler.</span><span class="sxs-lookup"><span data-stu-id="2a41a-132">Starting with the .NET Framework 4, when consuming performance counters, PerfCounter.dll checks the CategoryOptions registry entry for each provider to determine whether it should read from category-specific shared memory or global shared memory.</span></span> <span data-ttu-id="2a41a-133">.NET Framework 1,1 PerfCounter. dll, kategoriye özgü paylaşılan belleğin farkında olmadığından, bu kayıt defteri girdisini okuyamıyor; her zaman genel paylaşılan bellekten okur.</span><span class="sxs-lookup"><span data-stu-id="2a41a-133">The .NET Framework 1.1 PerfCounter.dll does not read that registry entry, because it is not aware of category-specific shared memory; it always reads from global shared memory.</span></span>  
  
 <span data-ttu-id="2a41a-134">Geriye dönük uyumluluk için .NET Framework 4 PerfCounter. dll, bir .NET Framework 1,1 uygulamasında çalışırken CategoryOptions kayıt defteri girişini denetlemez.</span><span class="sxs-lookup"><span data-stu-id="2a41a-134">For backward compatibility, the .NET Framework 4 PerfCounter.dll does not check the CategoryOptions registry entry when running in a .NET Framework 1.1 application.</span></span> <span data-ttu-id="2a41a-135">Yalnızca .NET Framework 1,1 PerfCounter. dll gibi genel paylaşılan belleği kullanır.</span><span class="sxs-lookup"><span data-stu-id="2a41a-135">It simply uses global shared memory, just like the .NET Framework 1.1 PerfCounter.dll.</span></span> <span data-ttu-id="2a41a-136">Ancak, `<forcePerformanceCounterUniqueSharedMemoryReads>` öğesini etkinleştirerek kayıt defteri ayarını denetlemek için .NET Framework 4 PerfCounter. dll ' ye bakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2a41a-136">However, you can instruct the .NET Framework 4 PerfCounter.dll to check the registry setting by enabling the `<forcePerformanceCounterUniqueSharedMemoryReads>` element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2a41a-137">`<forcePerformanceCounterUniqueSharedMemoryReads>` öğesinin etkinleştirilmesi, kategoriye özgü paylaşılan belleğin kullanılacağını garanti etmez.</span><span class="sxs-lookup"><span data-stu-id="2a41a-137">Enabling the `<forcePerformanceCounterUniqueSharedMemoryReads>` element does not guarantee that category-specific shared memory will be used.</span></span> <span data-ttu-id="2a41a-138">`true` etkinleştirildi ayarı yalnızca PerfCounter. dll ' nin CategoryOptions kayıt defteri ayarına başvurmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="2a41a-138">Setting enabled to `true` only causes PerfCounter.dll to reference the CategoryOptions registry setting.</span></span> <span data-ttu-id="2a41a-139">CategoryOptions için varsayılan ayar, kategoriye özgü paylaşılan bellek kullanmaktır; Ancak, genel paylaşılan belleğin kullanılması gerektiğini belirtmek için CategoryOptions ' ı değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2a41a-139">The default setting for CategoryOptions is to use category-specific shared memory; however, you can change CategoryOptions to indicate that global shared memory should be used.</span></span>  
  
 <span data-ttu-id="2a41a-140">CategoryOptions ayarını içeren kayıt defteri anahtarı HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\\< categoryName\>\Performanceşeklindedir.</span><span class="sxs-lookup"><span data-stu-id="2a41a-140">The registry key that contains the CategoryOptions setting is HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\\<categoryName\>\Performance.</span></span> <span data-ttu-id="2a41a-141">Varsayılan olarak, CategoryOptions 3 olarak ayarlanır, bu da PerfCounter. dll ' ye kategoriye özgü paylaşılan bellek kullanmasını söyler.</span><span class="sxs-lookup"><span data-stu-id="2a41a-141">By default, CategoryOptions is set to 3, which instructs PerfCounter.dll to use category-specific shared memory.</span></span> <span data-ttu-id="2a41a-142">CategoryOptions 0 olarak ayarlandıysa, PerfCounter. dll genel paylaşılan belleği kullanır.</span><span class="sxs-lookup"><span data-stu-id="2a41a-142">If CategoryOptions is set to 0, PerfCounter.dll uses global shared memory.</span></span> <span data-ttu-id="2a41a-143">Örnek verileri yalnızca oluşturulan örneğin adı, yeniden kullanılan örnekle aynıysa yeniden kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2a41a-143">Instance data will be reused only if the name of the instance being created is identical to the instance being reused.</span></span> <span data-ttu-id="2a41a-144">Tüm sürümler kategoriye yazabilecektir.</span><span class="sxs-lookup"><span data-stu-id="2a41a-144">All versions will be able to write to the category.</span></span> <span data-ttu-id="2a41a-145">Kategorili olarak 1 olarak ayarlanırsa, genel paylaşılan bellek kullanılır, ancak kategori adı, yeniden kullanılan kategoriyle aynı uzunluktadır sonra örnek verileri yeniden kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2a41a-145">If CategoryOptions is set to 1, global shared memory is used, but instance data can be reused if the category name is the same length as the category being reused.</span></span>  
  
 <span data-ttu-id="2a41a-146">0 ve 1 ayarları, bellek sızıntılarına ve performans sayacı belleğinin doldurulmasına yol açabilir.</span><span class="sxs-lookup"><span data-stu-id="2a41a-146">The settings 0 and 1 can lead to memory leaks and the filling up of performance counter memory.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2a41a-147">Örnek</span><span class="sxs-lookup"><span data-stu-id="2a41a-147">Example</span></span>  
 <span data-ttu-id="2a41a-148">Aşağıdaki örnek, kategoriye özgü paylaşılan bellek kullanıp kullanmayacağını belirlemek için PerfCounter. dll ' nin CategoryOptions kayıt defteri girişine başvurması gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="2a41a-148">The following example shows how to specify that PerfCounter.dll should reference the CategoryOptions registry entry to determine whether it should use category-specific shared memory.</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <forcePerformanceCounterUniqueSharedMemoryReads enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2a41a-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2a41a-149">See also</span></span>

- [<span data-ttu-id="2a41a-150">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="2a41a-150">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="2a41a-151">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="2a41a-151">Configuration File Schema</span></span>](../index.md)
