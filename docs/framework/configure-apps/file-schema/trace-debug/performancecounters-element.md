---
title: "&lt;performans sayaçları&gt; öğesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/performanceCounters
- http://schemas.microsoft.com/.NetConfiguration/v2.0#performanceCounters
helpviewer_keywords:
- performanceCounters element
- <perfomanceCounters> element
ms.assetid: a71f605b-c7d9-4501-a5c3-abcbb964a43f
caps.latest.revision: "10"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: f7fdbb244663e5114880437a5a508270c80a9c79
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltperformancecountersgt-element"></a><span data-ttu-id="924f6-102">&lt;performans sayaçları&gt; öğesi</span><span class="sxs-lookup"><span data-stu-id="924f6-102">&lt;performanceCounters&gt; Element</span></span>
<span data-ttu-id="924f6-103">Performans sayaçları tarafından paylaşılan genel bellek boyutunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="924f6-103">Specifies the size of the global memory shared by performance counters.</span></span>  
  
 <span data-ttu-id="924f6-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="924f6-104">\<configuration></span></span>  
<span data-ttu-id="924f6-105">\<System.Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="924f6-105">\<system.diagnostics></span></span>  
<span data-ttu-id="924f6-106">\<performans sayaçları ></span><span class="sxs-lookup"><span data-stu-id="924f6-106">\<performanceCounters></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="924f6-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="924f6-107">Syntax</span></span>  
  
```xml  
<performanceCounters filemappingsize="524288" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="924f6-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="924f6-108">Attributes and Elements</span></span>  
 <span data-ttu-id="924f6-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="924f6-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="924f6-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="924f6-110">Attributes</span></span>  
  
|<span data-ttu-id="924f6-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="924f6-111">Attribute</span></span>|<span data-ttu-id="924f6-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="924f6-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="924f6-113">filemappingsize</span><span class="sxs-lookup"><span data-stu-id="924f6-113">filemappingsize</span></span>|<span data-ttu-id="924f6-114">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="924f6-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="924f6-115">Performans sayaçları tarafından paylaşılan genel belleğin bayt cinsinden boyutu belirtir.</span><span class="sxs-lookup"><span data-stu-id="924f6-115">Specifies the size, in bytes, of the global memory shared by performance counters.</span></span> <span data-ttu-id="924f6-116">524288 varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="924f6-116">The default is 524288.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="924f6-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="924f6-117">Child Elements</span></span>  
 <span data-ttu-id="924f6-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="924f6-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="924f6-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="924f6-119">Parent Elements</span></span>  
  
|<span data-ttu-id="924f6-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="924f6-120">Element</span></span>|<span data-ttu-id="924f6-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="924f6-121">Description</span></span>|  
|-------------|-----------------|  
|`Configuration`|<span data-ttu-id="924f6-122">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="924f6-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="924f6-123">ASP.NET yapılandırma bölümü için kök öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="924f6-123">Specifies the root element for the ASP.NET configuration section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="924f6-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="924f6-124">Remarks</span></span>  
 <span data-ttu-id="924f6-125">Performans sayaçları, bellekle eşlenen dosya veya paylaşılan bellek performans verilerini yayınlamak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="924f6-125">Performance counters use a memory mapped file, or shared memory, to publish performance data.</span></span>  <span data-ttu-id="924f6-126">Kaç tane aynı anda kullanılabilir paylaşılan bellek boyutunu belirler.</span><span class="sxs-lookup"><span data-stu-id="924f6-126">The size of the shared memory determines how many instances can be used at once.</span></span>  <span data-ttu-id="924f6-127">Paylaşılan bellek iki tür vardır: Genel paylaşılan bellek ve ayrı bir paylaşılan bellek.</span><span class="sxs-lookup"><span data-stu-id="924f6-127">There are two types of shared memory: global shared memory and separate shared memory.</span></span>  <span data-ttu-id="924f6-128">Genel paylaşılan bellek, .NET Framework sürüm 1.0 veya 1.1 ile tüm performans sayacı kategorileri tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="924f6-128">The global shared memory is used by all performance counter categories installed with the .NET Framework versions 1.0 or 1.1.</span></span>  <span data-ttu-id="924f6-129">.NET Framework sürüm 2.0 ile birlikte yüklenen performans sayacı kategorileri ayrı paylaşılan bellek, her performans sayacı kategorisi kendi bellek sahip kullanın.</span><span class="sxs-lookup"><span data-stu-id="924f6-129">Performance counter categories installed with the .NET Framework version 2.0 use separate shared memory, with each performance counter category having its own memory.</span></span>  
  
 <span data-ttu-id="924f6-130">Genel paylaşılan bellek boyutu yalnızca bir yapılandırma dosyası ile ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="924f6-130">The size of global shared memory can be set only with a configuration file.</span></span>  <span data-ttu-id="924f6-131">Varsayılan boyutu 524.288 bEvet en büyük boyutu 33,554,432 bayt ve minimum boyut 32.768 bayttır.</span><span class="sxs-lookup"><span data-stu-id="924f6-131">The default size is 524,288 byes, the maximum size is 33,554,432 bytes, and the minimum size is 32,768 bytes.</span></span>  <span data-ttu-id="924f6-132">Genel paylaşılan bellek tüm işlemleri ve kategorileri tarafından paylaşılan olduğundan, ilk oluşturan boyutunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="924f6-132">Since the global shared memory is shared by all processes and categories, the first creator specifies the size.</span></span>  <span data-ttu-id="924f6-133">Uygulama yapılandırma dosyasında boyutu tanımlarsanız, uygulamanız yürütmek performans sayaçları neden olan ilk uygulama ise bu boyut yalnızca kullanılır.</span><span class="sxs-lookup"><span data-stu-id="924f6-133">If you define the size in your application configuration file, that size is only used if your application is the first application that causes the performance counters to execute.</span></span>  <span data-ttu-id="924f6-134">Bu nedenle belirtmek için doğru konuma `filemappingsize` Machine.config dosyasının bir değerdir.</span><span class="sxs-lookup"><span data-stu-id="924f6-134">Therefore the correct location to specify the `filemappingsize` value is the Machine.config file.</span></span>  <span data-ttu-id="924f6-135">Genel paylaşılan bellek bellek performans sayacı örnekleri farklı adlara sahip çok sayıda oluşturduysanız genel paylaşılan bellek tükendi tek tek performans sayaçları tarafından sonuç bırakılamıyor.</span><span class="sxs-lookup"><span data-stu-id="924f6-135">Memory in the global shared memory cannot be released by individual performance counters, so eventually global shared memory is exhausted if a large number of performance counter instances with different names are created.</span></span>  
  
 <span data-ttu-id="924f6-136">Ayrı bir paylaşılan bellek boyutu için anahtar DWORD FileMappingSize değeri kayıt defterinde HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\\*\<kategori adı >*\Performance başvurusu ilk olarak, genel paylaşılan bellek yapılandırma dosyası için belirtilen değer arkasından.</span><span class="sxs-lookup"><span data-stu-id="924f6-136">For the size of separate shared memory, the DWORD FileMappingSize value in the registry key HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\\*\<category name>*\Performance is referenced first, followed by the value specified for the global shared memory in the configuration file.</span></span> <span data-ttu-id="924f6-137">FileMappingSize değer yok sonra bir dördüncü kümesi ayrı bir paylaşılan bellek boyutu (1/4) yapılandırma dosyasında genel ayar.</span><span class="sxs-lookup"><span data-stu-id="924f6-137">If the FileMappingSize value does not exist, then the separate shared memory size is set to one fourth (1/4) the global setting in the configuration file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="924f6-138">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="924f6-138">See Also</span></span>  
 <xref:System.Diagnostics.PerformanceCounter>  
 <xref:System.Diagnostics.PerformanceCounterCategory>  
 <xref:System.Diagnostics.PerformanceCounter.InstanceLifetime%2A>  
 <xref:System.Diagnostics.PerformanceCounterInstanceLifetime>
