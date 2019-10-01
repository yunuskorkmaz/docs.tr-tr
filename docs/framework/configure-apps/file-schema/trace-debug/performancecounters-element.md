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
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697147"
---
# <a name="performancecounters-element"></a><span data-ttu-id="10987-102">\<performanceCounters > öğesi</span><span class="sxs-lookup"><span data-stu-id="10987-102">\<performanceCounters> Element</span></span>

<span data-ttu-id="10987-103">Performans sayaçları tarafından paylaşılan genel belleğin boyutunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="10987-103">Specifies the size of the global memory shared by performance counters.</span></span>

[<span data-ttu-id="10987-104"> **\<Yapılandırma >** </span><span class="sxs-lookup"><span data-stu-id="10987-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="10987-105">&nbsp; @ no__t-1[ **\<system. Diagnostics >** ](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="10987-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>  
<span data-ttu-id="10987-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 **\<performanceCounters >**</span><span class="sxs-lookup"><span data-stu-id="10987-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<performanceCounters>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="10987-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="10987-107">Syntax</span></span>

```xml
<performanceCounters filemappingsize="524288" />
```

## <a name="attributes-and-elements"></a><span data-ttu-id="10987-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="10987-108">Attributes and Elements</span></span>

<span data-ttu-id="10987-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="10987-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="10987-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="10987-110">Attributes</span></span>

|<span data-ttu-id="10987-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="10987-111">Attribute</span></span>|<span data-ttu-id="10987-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="10987-112">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="10987-113">dosya mappingsize</span><span class="sxs-lookup"><span data-stu-id="10987-113">filemappingsize</span></span>|<span data-ttu-id="10987-114">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="10987-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="10987-115">Performans sayaçları tarafından paylaşılan genel belleğin bayt cinsinden boyutunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="10987-115">Specifies the size, in bytes, of the global memory shared by performance counters.</span></span> <span data-ttu-id="10987-116">Varsayılan değer 524288 ' dir.</span><span class="sxs-lookup"><span data-stu-id="10987-116">The default is 524288.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="10987-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="10987-117">Child Elements</span></span>

<span data-ttu-id="10987-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="10987-118">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="10987-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="10987-119">Parent Elements</span></span>

|<span data-ttu-id="10987-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="10987-120">Element</span></span>|<span data-ttu-id="10987-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="10987-121">Description</span></span>|
|-------------|-----------------|
|`Configuration`|<span data-ttu-id="10987-122">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="10987-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`system.diagnostics`|<span data-ttu-id="10987-123">ASP.NET yapılandırma bölümünün kök öğesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="10987-123">Specifies the root element for the ASP.NET configuration section.</span></span>|

## <a name="remarks"></a><span data-ttu-id="10987-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="10987-124">Remarks</span></span>

<span data-ttu-id="10987-125">Performans sayaçları, performans verilerini yayınlamak için bellek eşlemeli bir dosya veya paylaşılan bellek kullanır.</span><span class="sxs-lookup"><span data-stu-id="10987-125">Performance counters use a memory mapped file, or shared memory, to publish performance data.</span></span>  <span data-ttu-id="10987-126">Paylaşılan belleğin boyutu, aynı anda kaç örnek kullanılabileceğini belirler.</span><span class="sxs-lookup"><span data-stu-id="10987-126">The size of the shared memory determines how many instances can be used at once.</span></span>  <span data-ttu-id="10987-127">İki tür paylaşılan bellek vardır: genel paylaşılan bellek ve ayrı paylaşılan bellek.</span><span class="sxs-lookup"><span data-stu-id="10987-127">There are two types of shared memory: global shared memory and separate shared memory.</span></span>  <span data-ttu-id="10987-128">Genel paylaşılan bellek, 1,0 veya 1,1 .NET Framework sürümleriyle yüklenen tüm performans sayacı kategorileri tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="10987-128">The global shared memory is used by all performance counter categories installed with the .NET Framework versions 1.0 or 1.1.</span></span>  <span data-ttu-id="10987-129">.NET Framework sürüm 2,0 ile yüklenen performans sayacı kategorileri, her bir performans sayacı kategorisiyle kendi belleği bulunan ayrı paylaşılan bellek kullanır.</span><span class="sxs-lookup"><span data-stu-id="10987-129">Performance counter categories installed with the .NET Framework version 2.0 use separate shared memory, with each performance counter category having its own memory.</span></span>

<span data-ttu-id="10987-130">Genel paylaşılan belleğin boyutu yalnızca bir yapılandırma dosyası ile ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="10987-130">The size of global shared memory can be set only with a configuration file.</span></span>  <span data-ttu-id="10987-131">Varsayılan boyut 524.288 bEvet, en büyük boyut 33.554.432 bayttır ve en küçük boyut 32.768 bayttır.</span><span class="sxs-lookup"><span data-stu-id="10987-131">The default size is 524,288 byes, the maximum size is 33,554,432 bytes, and the minimum size is 32,768 bytes.</span></span>  <span data-ttu-id="10987-132">Genel paylaşılan bellek tüm süreçler ve kategoriler tarafından paylaşıldığından, ilk Oluşturucu boyutu belirtir.</span><span class="sxs-lookup"><span data-stu-id="10987-132">Since the global shared memory is shared by all processes and categories, the first creator specifies the size.</span></span>  <span data-ttu-id="10987-133">Uygulama yapılandırma dosyanızda boyutu tanımlarsanız, bu boyut yalnızca uygulamanız, performans sayaçlarının yürütülmesine neden olan ilk uygulama ise kullanılır.</span><span class="sxs-lookup"><span data-stu-id="10987-133">If you define the size in your application configuration file, that size is only used if your application is the first application that causes the performance counters to execute.</span></span>  <span data-ttu-id="10987-134">Bu nedenle, `filemappingsize` değerini belirtmek için doğru konum Machine. config dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="10987-134">Therefore the correct location to specify the `filemappingsize` value is the Machine.config file.</span></span>  <span data-ttu-id="10987-135">Genel paylaşılan bellekteki bellek ayrı performans sayaçları tarafından yayınlanamaz, bu nedenle farklı adlara sahip çok sayıda performans sayacı örneği oluşturulursa, genel paylaşılan bellek tükenir.</span><span class="sxs-lookup"><span data-stu-id="10987-135">Memory in the global shared memory cannot be released by individual performance counters, so eventually global shared memory is exhausted if a large number of performance counter instances with different names are created.</span></span>

<span data-ttu-id="10987-136">Ayrı paylaşılan belleğin boyutu için, no__t kayıt defteri anahtarındaki DWORD FileMappingSize değeri, önce bir değer olan HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services FILE-0 *\<category name >* \Performance yapılandırma dosyasındaki genel paylaşılan bellek için belirtilir.</span><span class="sxs-lookup"><span data-stu-id="10987-136">For the size of separate shared memory, the DWORD FileMappingSize value in the registry key HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\\*\<category name>* \Performance is referenced first, followed by the value specified for the global shared memory in the configuration file.</span></span> <span data-ttu-id="10987-137">FileMappingSize değeri yoksa, ayrı paylaşılan bellek boyutu yapılandırma dosyasındaki genel ayarı bir dördüncü (1/4) olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="10987-137">If the FileMappingSize value does not exist, then the separate shared memory size is set to one fourth (1/4) the global setting in the configuration file.</span></span>

## <a name="see-also"></a><span data-ttu-id="10987-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="10987-138">See also</span></span>

- <xref:System.Diagnostics.PerformanceCounter>
- <xref:System.Diagnostics.PerformanceCounterCategory>
- <xref:System.Diagnostics.PerformanceCounter.InstanceLifetime%2A>
- <xref:System.Diagnostics.PerformanceCounterInstanceLifetime>
