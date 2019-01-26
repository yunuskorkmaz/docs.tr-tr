---
title: '&lt;performanceCounters&gt; öğesi'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/performanceCounters
- http://schemas.microsoft.com/.NetConfiguration/v2.0#performanceCounters
helpviewer_keywords:
- performanceCounters element
- <perfomanceCounters> element
ms.assetid: a71f605b-c7d9-4501-a5c3-abcbb964a43f
ms.openlocfilehash: 5afa38a98aa6ea0901849b01d6b1030d079f218e
ms.sourcegitcommit: b351b0781a035616c90c68ccae6dd60aae66a953
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/26/2019
ms.locfileid: "55083983"
---
# <a name="ltperformancecountersgt-element"></a><span data-ttu-id="0e900-102">&lt;performanceCounters&gt; öğesi</span><span class="sxs-lookup"><span data-stu-id="0e900-102">&lt;performanceCounters&gt; Element</span></span>
<span data-ttu-id="0e900-103">Performans sayaçlarını birer paylaşılan genel bellek boyutunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="0e900-103">Specifies the size of the global memory shared by performance counters.</span></span>  
  
 <span data-ttu-id="0e900-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="0e900-104">\<configuration></span></span>  
<span data-ttu-id="0e900-105">\<System.Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="0e900-105">\<system.diagnostics></span></span>  
<span data-ttu-id="0e900-106">\<performanceCounters ></span><span class="sxs-lookup"><span data-stu-id="0e900-106">\<performanceCounters></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e900-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0e900-107">Syntax</span></span>  
  
```xml  
<performanceCounters filemappingsize="524288" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0e900-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="0e900-108">Attributes and Elements</span></span>  
 <span data-ttu-id="0e900-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0e900-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0e900-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0e900-110">Attributes</span></span>  
  
|<span data-ttu-id="0e900-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="0e900-111">Attribute</span></span>|<span data-ttu-id="0e900-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0e900-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0e900-113">filemappingsize</span><span class="sxs-lookup"><span data-stu-id="0e900-113">filemappingsize</span></span>|<span data-ttu-id="0e900-114">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="0e900-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="0e900-115">Genel performans sayaçlarını birer paylaşılan belleğin bayt cinsinden boyutunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="0e900-115">Specifies the size, in bytes, of the global memory shared by performance counters.</span></span> <span data-ttu-id="0e900-116">524288 varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="0e900-116">The default is 524288.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0e900-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="0e900-117">Child Elements</span></span>  
 <span data-ttu-id="0e900-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="0e900-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0e900-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="0e900-119">Parent Elements</span></span>  
  
|<span data-ttu-id="0e900-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="0e900-120">Element</span></span>|<span data-ttu-id="0e900-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0e900-121">Description</span></span>|  
|-------------|-----------------|  
|`Configuration`|<span data-ttu-id="0e900-122">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="0e900-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="0e900-123">ASP.NET yapılandırma bölümü için olan kök öğesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="0e900-123">Specifies the root element for the ASP.NET configuration section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0e900-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0e900-124">Remarks</span></span>  
 <span data-ttu-id="0e900-125">Performans sayaçları, performans verilerini yayınlamak için bellek eşlemeli dosya veya paylaşılan belleği'ni kullanın.</span><span class="sxs-lookup"><span data-stu-id="0e900-125">Performance counters use a memory mapped file, or shared memory, to publish performance data.</span></span>  <span data-ttu-id="0e900-126">Tek seferde kaç tane kullanılabilir paylaşılan bellek boyutunu belirler.</span><span class="sxs-lookup"><span data-stu-id="0e900-126">The size of the shared memory determines how many instances can be used at once.</span></span>  <span data-ttu-id="0e900-127">Paylaşılan bellek iki tür vardır: Genel paylaşılan bellek ve ayrı bir paylaşılan bellek.</span><span class="sxs-lookup"><span data-stu-id="0e900-127">There are two types of shared memory: global shared memory and separate shared memory.</span></span>  <span data-ttu-id="0e900-128">Genel paylaşılan bellek, .NET Framework sürümleri 1.0 veya 1.1 ile tüm performans sayacı kategorileri tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0e900-128">The global shared memory is used by all performance counter categories installed with the .NET Framework versions 1.0 or 1.1.</span></span>  <span data-ttu-id="0e900-129">.NET Framework sürüm 2.0 yüklü performans sayacı kategorileri ayrı paylaşılan bellek, her performans sayacı kategorisinin, kendi belleğe sahip kullanın.</span><span class="sxs-lookup"><span data-stu-id="0e900-129">Performance counter categories installed with the .NET Framework version 2.0 use separate shared memory, with each performance counter category having its own memory.</span></span>  
  
 <span data-ttu-id="0e900-130">Yalnızca bir yapılandırma dosyası ile genel paylaşılan bellek boyutunu ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0e900-130">The size of global shared memory can be set only with a configuration file.</span></span>  <span data-ttu-id="0e900-131">Varsayılan boyutu 524.288 bEvet en büyük boyutu 33,554,432 bayt ve en düşük boyut 32.768 bayttır.</span><span class="sxs-lookup"><span data-stu-id="0e900-131">The default size is 524,288 byes, the maximum size is 33,554,432 bytes, and the minimum size is 32,768 bytes.</span></span>  <span data-ttu-id="0e900-132">Genel paylaşılan bellek tüm işlemleri ve kategorileri tarafından paylaşılan olduğundan, ilk oluşturan boyutunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="0e900-132">Since the global shared memory is shared by all processes and categories, the first creator specifies the size.</span></span>  <span data-ttu-id="0e900-133">Uygulama yapılandırma dosyanızda boyutu tanımlarsanız, uygulamanızı yürütmek performans sayaçları neden olan ilk uygulama ise, boyutu yalnızca kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0e900-133">If you define the size in your application configuration file, that size is only used if your application is the first application that causes the performance counters to execute.</span></span>  <span data-ttu-id="0e900-134">Bu nedenle doğru konumu belirlemek için `filemappingsize` Machine.config dosyasının bir değerdir.</span><span class="sxs-lookup"><span data-stu-id="0e900-134">Therefore the correct location to specify the `filemappingsize` value is the Machine.config file.</span></span>  <span data-ttu-id="0e900-135">Çok sayıda performans sayacı örneklerinin farklı adlara sahip oluşturduysanız genel paylaşılan bellek bitti bireysel performans sayaçlarını birer, sonuç genel paylaşılan bellek bellekte bırakılamıyor.</span><span class="sxs-lookup"><span data-stu-id="0e900-135">Memory in the global shared memory cannot be released by individual performance counters, so eventually global shared memory is exhausted if a large number of performance counter instances with different names are created.</span></span>  
  
 <span data-ttu-id="0e900-136">Ayrı bir paylaşılan bellek boyutu için kayıt defteri DWORD FileMappingSize değerinde anahtar HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\\*\<kategori adı >* \Performance başvuruluyor yapılandırma dosyasındaki genel paylaşılan bellek için belirtilen değer ilk olarak, arkasından.</span><span class="sxs-lookup"><span data-stu-id="0e900-136">For the size of separate shared memory, the DWORD FileMappingSize value in the registry key HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\\*\<category name>* \Performance is referenced first, followed by the value specified for the global shared memory in the configuration file.</span></span> <span data-ttu-id="0e900-137">FileMappingSize değeri yok sonra ayrı bir paylaşılan bellek boyutu için bir dördüncü ayarlanır (1/4) yapılandırma dosyasındaki genel ayarı.</span><span class="sxs-lookup"><span data-stu-id="0e900-137">If the FileMappingSize value does not exist, then the separate shared memory size is set to one fourth (1/4) the global setting in the configuration file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e900-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0e900-138">See also</span></span>
- <xref:System.Diagnostics.PerformanceCounter>
- <xref:System.Diagnostics.PerformanceCounterCategory>
- <xref:System.Diagnostics.PerformanceCounter.InstanceLifetime%2A>
- <xref:System.Diagnostics.PerformanceCounterInstanceLifetime>
