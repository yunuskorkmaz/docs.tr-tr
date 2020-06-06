---
title: <performanceCounters> Öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/performanceCounters
- http://schemas.microsoft.com/.NetConfiguration/v2.0#performanceCounters
helpviewer_keywords:
- performanceCounters element
- <performanceCounters> element
ms.assetid: a71f605b-c7d9-4501-a5c3-abcbb964a43f
ms.openlocfilehash: f52fdb2d5b0b7911de63f96663e70735d2f2496c
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "71697147"
---
# <a name="performancecounters-element"></a><span data-ttu-id="47406-102">\<performanceCounters> Öğesi</span><span class="sxs-lookup"><span data-stu-id="47406-102">\<performanceCounters> Element</span></span>

<span data-ttu-id="47406-103">Performans sayaçları tarafından paylaşılan genel belleğin boyutunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="47406-103">Specifies the size of the global memory shared by performance counters.</span></span>

[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<performanceCounters>**  

## <a name="syntax"></a><span data-ttu-id="47406-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="47406-104">Syntax</span></span>

```xml
<performanceCounters filemappingsize="524288" />
```

## <a name="attributes-and-elements"></a><span data-ttu-id="47406-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="47406-105">Attributes and Elements</span></span>

<span data-ttu-id="47406-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="47406-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="47406-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="47406-107">Attributes</span></span>

|<span data-ttu-id="47406-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="47406-108">Attribute</span></span>|<span data-ttu-id="47406-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="47406-109">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="47406-110">dosya mappingsize</span><span class="sxs-lookup"><span data-stu-id="47406-110">filemappingsize</span></span>|<span data-ttu-id="47406-111">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="47406-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="47406-112">Performans sayaçları tarafından paylaşılan genel belleğin bayt cinsinden boyutunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="47406-112">Specifies the size, in bytes, of the global memory shared by performance counters.</span></span> <span data-ttu-id="47406-113">Varsayılan değer 524288 ' dir.</span><span class="sxs-lookup"><span data-stu-id="47406-113">The default is 524288.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="47406-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="47406-114">Child Elements</span></span>

<span data-ttu-id="47406-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="47406-115">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="47406-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="47406-116">Parent Elements</span></span>

|<span data-ttu-id="47406-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="47406-117">Element</span></span>|<span data-ttu-id="47406-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="47406-118">Description</span></span>|
|-------------|-----------------|
|`Configuration`|<span data-ttu-id="47406-119">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="47406-119">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`system.diagnostics`|<span data-ttu-id="47406-120">ASP.NET yapılandırma bölümünün kök öğesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="47406-120">Specifies the root element for the ASP.NET configuration section.</span></span>|

## <a name="remarks"></a><span data-ttu-id="47406-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="47406-121">Remarks</span></span>

<span data-ttu-id="47406-122">Performans sayaçları, performans verilerini yayınlamak için bellek eşlemeli bir dosya veya paylaşılan bellek kullanır.</span><span class="sxs-lookup"><span data-stu-id="47406-122">Performance counters use a memory mapped file, or shared memory, to publish performance data.</span></span>  <span data-ttu-id="47406-123">Paylaşılan belleğin boyutu, aynı anda kaç örnek kullanılabileceğini belirler.</span><span class="sxs-lookup"><span data-stu-id="47406-123">The size of the shared memory determines how many instances can be used at once.</span></span>  <span data-ttu-id="47406-124">İki tür paylaşılan bellek vardır: genel paylaşılan bellek ve ayrı paylaşılan bellek.</span><span class="sxs-lookup"><span data-stu-id="47406-124">There are two types of shared memory: global shared memory and separate shared memory.</span></span>  <span data-ttu-id="47406-125">Genel paylaşılan bellek, 1,0 veya 1,1 .NET Framework sürümleriyle yüklenen tüm performans sayacı kategorileri tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="47406-125">The global shared memory is used by all performance counter categories installed with the .NET Framework versions 1.0 or 1.1.</span></span>  <span data-ttu-id="47406-126">.NET Framework sürüm 2,0 ile yüklenen performans sayacı kategorileri, her bir performans sayacı kategorisiyle kendi belleği bulunan ayrı paylaşılan bellek kullanır.</span><span class="sxs-lookup"><span data-stu-id="47406-126">Performance counter categories installed with the .NET Framework version 2.0 use separate shared memory, with each performance counter category having its own memory.</span></span>

<span data-ttu-id="47406-127">Genel paylaşılan belleğin boyutu yalnızca bir yapılandırma dosyası ile ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="47406-127">The size of global shared memory can be set only with a configuration file.</span></span>  <span data-ttu-id="47406-128">Varsayılan boyut 524.288 bEvet, en büyük boyut 33.554.432 bayttır ve en küçük boyut 32.768 bayttır.</span><span class="sxs-lookup"><span data-stu-id="47406-128">The default size is 524,288 byes, the maximum size is 33,554,432 bytes, and the minimum size is 32,768 bytes.</span></span>  <span data-ttu-id="47406-129">Genel paylaşılan bellek tüm süreçler ve kategoriler tarafından paylaşıldığından, ilk Oluşturucu boyutu belirtir.</span><span class="sxs-lookup"><span data-stu-id="47406-129">Since the global shared memory is shared by all processes and categories, the first creator specifies the size.</span></span>  <span data-ttu-id="47406-130">Uygulama yapılandırma dosyanızda boyutu tanımlarsanız, bu boyut yalnızca uygulamanız, performans sayaçlarının yürütülmesine neden olan ilk uygulama ise kullanılır.</span><span class="sxs-lookup"><span data-stu-id="47406-130">If you define the size in your application configuration file, that size is only used if your application is the first application that causes the performance counters to execute.</span></span>  <span data-ttu-id="47406-131">Bu nedenle, değeri belirtmek için doğru konum `filemappingsize` Machine. config dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="47406-131">Therefore the correct location to specify the `filemappingsize` value is the Machine.config file.</span></span>  <span data-ttu-id="47406-132">Genel paylaşılan bellekteki bellek ayrı performans sayaçları tarafından yayınlanamaz, bu nedenle farklı adlara sahip çok sayıda performans sayacı örneği oluşturulursa, genel paylaşılan bellek tükenir.</span><span class="sxs-lookup"><span data-stu-id="47406-132">Memory in the global shared memory cannot be released by individual performance counters, so eventually global shared memory is exhausted if a large number of performance counter instances with different names are created.</span></span>

<span data-ttu-id="47406-133">Ayrı paylaşılan belleğin boyutu için, kayıt defteri anahtarındaki DWORD FileMappingSize değeri önce \SYSTEM\CurrentControlSet\Services \Performance HKEY_LOCAL_MACHINE, \\ *\<category name>* ardından yapılandırma dosyasında genel paylaşılan bellek için belirtilen değer tarafından başvurulur.</span><span class="sxs-lookup"><span data-stu-id="47406-133">For the size of separate shared memory, the DWORD FileMappingSize value in the registry key HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\\*\<category name>* \Performance is referenced first, followed by the value specified for the global shared memory in the configuration file.</span></span> <span data-ttu-id="47406-134">FileMappingSize değeri yoksa, ayrı paylaşılan bellek boyutu yapılandırma dosyasındaki genel ayarı bir dördüncü (1/4) olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="47406-134">If the FileMappingSize value does not exist, then the separate shared memory size is set to one fourth (1/4) the global setting in the configuration file.</span></span>

## <a name="see-also"></a><span data-ttu-id="47406-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="47406-135">See also</span></span>

- <xref:System.Diagnostics.PerformanceCounter>
- <xref:System.Diagnostics.PerformanceCounterCategory>
- <xref:System.Diagnostics.PerformanceCounter.InstanceLifetime%2A>
- <xref:System.Diagnostics.PerformanceCounterInstanceLifetime>
