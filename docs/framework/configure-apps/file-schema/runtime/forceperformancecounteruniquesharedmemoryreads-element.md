---
title: <forcePerformanceCounterUniqueSharedMemoryReads> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- forcePerformanceCounterUniqueSharedMemoryReads element
- <forcePerformanceCounterUniqueSharedMemoryReads> element
ms.assetid: 91149858-4810-4f65-9b48-468488172c9b
ms.openlocfilehash: 742b444c445ba67d6977b622e615a6a8f591826e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154146"
---
# <a name="forceperformancecounteruniquesharedmemoryreads-element"></a><span data-ttu-id="37c84-102">\<forcePerformanceCounterUniqueSharedMemoryReads> Öğesi</span><span class="sxs-lookup"><span data-stu-id="37c84-102">\<forcePerformanceCounterUniqueSharedMemoryReads> Element</span></span>
<span data-ttu-id="37c84-103">PerfCounter. dll ' nin, performans sayacı verilerinin kategoriye özgü paylaşılan bellekten veya genel bellekten yüklenip yüklenmeyeceğini belirleme .NET Framework sürüm 1,1 uygulamasında CategoryOptions kayıt defteri ayarını kullanıp kullanmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="37c84-103">Specifies whether PerfCounter.dll uses the CategoryOptions registry setting in a .NET Framework version 1.1 application to determine whether to load performance counter data from category-specific shared memory or global memory.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<forcePerformanceCounterUniqueSharedMemoryReads>**  
  
## <a name="syntax"></a><span data-ttu-id="37c84-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="37c84-104">Syntax</span></span>  
  
```xml  
<forcePerformanceCounterUniqueSharedMemoryReads
enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="37c84-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="37c84-105">Attributes and Elements</span></span>  
 <span data-ttu-id="37c84-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="37c84-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="37c84-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="37c84-107">Attributes</span></span>  
  
|<span data-ttu-id="37c84-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="37c84-108">Attribute</span></span>|<span data-ttu-id="37c84-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="37c84-109">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="37c84-110">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="37c84-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="37c84-111">PerfCounter. dll ' nin, performans sayacı verilerinin kategoriye özgü paylaşılan bellekten mi yoksa genel bellekten mi yükleneceğini öğrenmek için CategoryOptions kayıt defteri ayarını kullanıp kullanmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="37c84-111">Indicates whether PerfCounter.dll uses the CategoryOptions registry setting to determine whether to load performance counter data from category-specific shared memory or global memory.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="37c84-112">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="37c84-112">enabled Attribute</span></span>  
  
|<span data-ttu-id="37c84-113">Değer</span><span class="sxs-lookup"><span data-stu-id="37c84-113">Value</span></span>|<span data-ttu-id="37c84-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="37c84-114">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="37c84-115">PerfCounter. dll, CategoryOptions kayıt defteri ayarını kullanmaz. bu varsayılan ayardır.</span><span class="sxs-lookup"><span data-stu-id="37c84-115">PerfCounter.dll does not use the CategoryOptions registry setting This is the default.</span></span>|  
|`true`|<span data-ttu-id="37c84-116">PerfCounter. dll, CategoryOptions kayıt defteri ayarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="37c84-116">PerfCounter.dll does use the CategoryOptions registry setting.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="37c84-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="37c84-117">Child Elements</span></span>  
 <span data-ttu-id="37c84-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="37c84-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="37c84-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="37c84-119">Parent Elements</span></span>  
  
|<span data-ttu-id="37c84-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="37c84-120">Element</span></span>|<span data-ttu-id="37c84-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="37c84-121">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="37c84-122">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="37c84-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="37c84-123">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="37c84-123">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="37c84-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="37c84-124">Remarks</span></span>  
 <span data-ttu-id="37c84-125">.NET Framework 4 ' ün öncesindeki .NET Framework sürümlerinde, yüklenmiş olan PerfCounter. dll sürümü, işleme yüklenmiş çalışma zamanına karşılık gelen sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="37c84-125">In versions of the .NET Framework before the .NET Framework 4, the version of PerfCounter.dll that was loaded corresponded to the runtime that was loaded in the process.</span></span> <span data-ttu-id="37c84-126">Bir bilgisayarda .NET Framework sürüm 1,1 ve .NET Framework 2,0 yüklüyse, bir .NET Framework 1,1 uygulaması PerfCounter. dll ' nin .NET Framework 1,1 sürümünü yükler.</span><span class="sxs-lookup"><span data-stu-id="37c84-126">If a computer had both the .NET Framework version 1.1 and the .NET Framework 2.0 installed, a .NET Framework 1.1 application would load the .NET Framework 1.1 version of PerfCounter.dll.</span></span> <span data-ttu-id="37c84-127">.NET Framework 4 ' te başlayarak, PerfCounter. dll ' nin en yeni yüklü sürümü yüklenir.</span><span class="sxs-lookup"><span data-stu-id="37c84-127">Starting with the .NET Framework 4, the newest installed version of PerfCounter.dll is loaded.</span></span> <span data-ttu-id="37c84-128">Bu, .NET Framework 1,1 uygulaması, bilgisayarda .NET Framework 4 yüklüyse PerfCounter. dll ' nin .NET Framework 4 sürümünü yükleyecek anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="37c84-128">This means that a .NET Framework 1.1 application will load the .NET Framework 4 version of PerfCounter.dll if the .NET Framework 4 is installed on the computer.</span></span>  
  
 <span data-ttu-id="37c84-129">.NET Framework 4 ' ten başlayarak, performans sayaçlarını tükettiği için PerfCounter. dll, her bir sağlayıcının kategorilere özgü paylaşılan bellekten veya genel paylaşılan bellekten okunup okunmayacağını belirlemede bu kayıt defteri girişini denetler.</span><span class="sxs-lookup"><span data-stu-id="37c84-129">Starting with the .NET Framework 4, when consuming performance counters, PerfCounter.dll checks the CategoryOptions registry entry for each provider to determine whether it should read from category-specific shared memory or global shared memory.</span></span> <span data-ttu-id="37c84-130">.NET Framework 1,1 PerfCounter. dll, kategoriye özgü paylaşılan belleğin farkında olmadığından, bu kayıt defteri girdisini okuyamıyor; her zaman genel paylaşılan bellekten okur.</span><span class="sxs-lookup"><span data-stu-id="37c84-130">The .NET Framework 1.1 PerfCounter.dll does not read that registry entry, because it is not aware of category-specific shared memory; it always reads from global shared memory.</span></span>  
  
 <span data-ttu-id="37c84-131">Geriye dönük uyumluluk için .NET Framework 4 PerfCounter. dll, bir .NET Framework 1,1 uygulamasında çalışırken CategoryOptions kayıt defteri girişini denetlemez.</span><span class="sxs-lookup"><span data-stu-id="37c84-131">For backward compatibility, the .NET Framework 4 PerfCounter.dll does not check the CategoryOptions registry entry when running in a .NET Framework 1.1 application.</span></span> <span data-ttu-id="37c84-132">Yalnızca .NET Framework 1,1 PerfCounter. dll gibi genel paylaşılan belleği kullanır.</span><span class="sxs-lookup"><span data-stu-id="37c84-132">It simply uses global shared memory, just like the .NET Framework 1.1 PerfCounter.dll.</span></span> <span data-ttu-id="37c84-133">Ancak, öğesini etkinleştirerek kayıt defteri ayarını denetlemek için .NET Framework 4 PerfCounter. dll ' ye bakabilirsiniz `<forcePerformanceCounterUniqueSharedMemoryReads>` .</span><span class="sxs-lookup"><span data-stu-id="37c84-133">However, you can instruct the .NET Framework 4 PerfCounter.dll to check the registry setting by enabling the `<forcePerformanceCounterUniqueSharedMemoryReads>` element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="37c84-134">Öğesinin etkinleştirilmesi, `<forcePerformanceCounterUniqueSharedMemoryReads>` kategoriye özgü paylaşılan belleğin kullanılacağını garanti etmez.</span><span class="sxs-lookup"><span data-stu-id="37c84-134">Enabling the `<forcePerformanceCounterUniqueSharedMemoryReads>` element does not guarantee that category-specific shared memory will be used.</span></span> <span data-ttu-id="37c84-135">Enabled ayarı `true` yalnızca PerfCounter. dll ' nin CategoryOptions kayıt defteri ayarına başvurmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="37c84-135">Setting enabled to `true` only causes PerfCounter.dll to reference the CategoryOptions registry setting.</span></span> <span data-ttu-id="37c84-136">CategoryOptions için varsayılan ayar, kategoriye özgü paylaşılan bellek kullanmaktır; Ancak, genel paylaşılan belleğin kullanılması gerektiğini belirtmek için CategoryOptions ' ı değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="37c84-136">The default setting for CategoryOptions is to use category-specific shared memory; however, you can change CategoryOptions to indicate that global shared memory should be used.</span></span>  
  
 <span data-ttu-id="37c84-137">CategoryOptions ayarını içeren kayıt defteri anahtarı HKEY_LOCAL_MACHINE \System\CurrentControlSet\Services \\<CategoryName \> \ performanceşeklindedir.</span><span class="sxs-lookup"><span data-stu-id="37c84-137">The registry key that contains the CategoryOptions setting is HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\\<categoryName\>\Performance.</span></span> <span data-ttu-id="37c84-138">Varsayılan olarak, CategoryOptions 3 olarak ayarlanır, bu da PerfCounter. dll ' ye kategoriye özgü paylaşılan bellek kullanmasını söyler.</span><span class="sxs-lookup"><span data-stu-id="37c84-138">By default, CategoryOptions is set to 3, which instructs PerfCounter.dll to use category-specific shared memory.</span></span> <span data-ttu-id="37c84-139">CategoryOptions 0 olarak ayarlandıysa, PerfCounter. dll genel paylaşılan belleği kullanır.</span><span class="sxs-lookup"><span data-stu-id="37c84-139">If CategoryOptions is set to 0, PerfCounter.dll uses global shared memory.</span></span> <span data-ttu-id="37c84-140">Örnek verileri yalnızca oluşturulan örneğin adı, yeniden kullanılan örnekle aynıysa yeniden kullanılır.</span><span class="sxs-lookup"><span data-stu-id="37c84-140">Instance data will be reused only if the name of the instance being created is identical to the instance being reused.</span></span> <span data-ttu-id="37c84-141">Tüm sürümler kategoriye yazabilecektir.</span><span class="sxs-lookup"><span data-stu-id="37c84-141">All versions will be able to write to the category.</span></span> <span data-ttu-id="37c84-142">Kategorili olarak 1 olarak ayarlanırsa, genel paylaşılan bellek kullanılır, ancak kategori adı, yeniden kullanılan kategoriyle aynı uzunluktadır sonra örnek verileri yeniden kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="37c84-142">If CategoryOptions is set to 1, global shared memory is used, but instance data can be reused if the category name is the same length as the category being reused.</span></span>  
  
 <span data-ttu-id="37c84-143">0 ve 1 ayarları, bellek sızıntılarına ve performans sayacı belleğinin doldurulmasına yol açabilir.</span><span class="sxs-lookup"><span data-stu-id="37c84-143">The settings 0 and 1 can lead to memory leaks and the filling up of performance counter memory.</span></span>  
  
## <a name="example"></a><span data-ttu-id="37c84-144">Örnek</span><span class="sxs-lookup"><span data-stu-id="37c84-144">Example</span></span>  
 <span data-ttu-id="37c84-145">Aşağıdaki örnek, kategoriye özgü paylaşılan bellek kullanıp kullanmayacağını belirlemek için PerfCounter. dll ' nin CategoryOptions kayıt defteri girişine başvurması gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="37c84-145">The following example shows how to specify that PerfCounter.dll should reference the CategoryOptions registry entry to determine whether it should use category-specific shared memory.</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <forcePerformanceCounterUniqueSharedMemoryReads enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="37c84-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="37c84-146">See also</span></span>

- [<span data-ttu-id="37c84-147">Çalışma zamanı ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="37c84-147">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="37c84-148">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="37c84-148">Configuration File Schema</span></span>](../index.md)
