---
title: '&lt;gcServer&gt; Element'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/gcServer
- http://schemas.microsoft.com/.NetConfiguration/v2.0#gcServer
helpviewer_keywords:
- gcServer element
- <gcServer> element
ms.assetid: 8d25b80e-2581-4803-bd87-a59528e3cb03
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 46aae3ad287c2626123cf3f513fc72bc1acdd06e
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="ltgcservergt-element"></a><span data-ttu-id="4b4d2-102">&lt;gcServer&gt; Element</span><span class="sxs-lookup"><span data-stu-id="4b4d2-102">&lt;gcServer&gt; Element</span></span>
<span data-ttu-id="4b4d2-103">Ortak dil çalışma zamanı sunucu çöp toplama çalışıp çalışmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="4b4d2-103">Specifies whether the common language runtime runs server garbage collection.</span></span>  
  
 <span data-ttu-id="4b4d2-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="4b4d2-104">\<configuration></span></span>  
<span data-ttu-id="4b4d2-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="4b4d2-105">\<runtime></span></span>  
<span data-ttu-id="4b4d2-106">\<gcServer></span><span class="sxs-lookup"><span data-stu-id="4b4d2-106">\<gcServer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b4d2-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4b4d2-107">Syntax</span></span>  
  
```xml  
<gcServer    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4b4d2-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="4b4d2-108">Attributes and Elements</span></span>  
 <span data-ttu-id="4b4d2-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4b4d2-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4b4d2-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="4b4d2-110">Attributes</span></span>  
  
|<span data-ttu-id="4b4d2-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="4b4d2-111">Attribute</span></span>|<span data-ttu-id="4b4d2-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4b4d2-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="4b4d2-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="4b4d2-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="4b4d2-114">Çalışma zamanı sunucu çöp toplama çalışıp çalışmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="4b4d2-114">Specifies whether the runtime runs server garbage collection.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="4b4d2-115">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="4b4d2-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="4b4d2-116">Değer</span><span class="sxs-lookup"><span data-stu-id="4b4d2-116">Value</span></span>|<span data-ttu-id="4b4d2-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4b4d2-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="4b4d2-118">Sunucu çöp toplama çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="4b4d2-118">Does not run server garbage collection.</span></span> <span data-ttu-id="4b4d2-119">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="4b4d2-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="4b4d2-120">Sunucu çöp toplama çalışır.</span><span class="sxs-lookup"><span data-stu-id="4b4d2-120">Runs server garbage collection.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4b4d2-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="4b4d2-121">Child Elements</span></span>  
 <span data-ttu-id="4b4d2-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="4b4d2-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4b4d2-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="4b4d2-123">Parent Elements</span></span>  
  
|<span data-ttu-id="4b4d2-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="4b4d2-124">Element</span></span>|<span data-ttu-id="4b4d2-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4b4d2-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="4b4d2-126">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="4b4d2-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="4b4d2-127">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="4b4d2-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4b4d2-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4b4d2-128">Remarks</span></span>  
 <span data-ttu-id="4b4d2-129">Ortak dil çalışma zamanı (CLR) çöp toplama iki türlerini destekler: tüm sistemlerde kullanılabilir iş istasyonu çöp toplama ve çok işlemcili sistemlerde kullanılabilir sunucu çöp toplama.</span><span class="sxs-lookup"><span data-stu-id="4b4d2-129">The common language runtime (CLR) supports two types of garbage collection: workstation garbage collection, which is available on all systems, and server garbage collection, which is available on multiprocessor systems.</span></span> <span data-ttu-id="4b4d2-130">Kullandığınız `<gcServer>` çöp toplama CLR türünü denetlemek için öğesi gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="4b4d2-130">You use the `<gcServer>` element to control the type of garbage collection the CLR performs.</span></span> <span data-ttu-id="4b4d2-131">Kullanım <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType> sunucu çöp toplama etkin olup olmadığını belirlemek için özellik.</span><span class="sxs-lookup"><span data-stu-id="4b4d2-131">Use the <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType> property to determine if server garbage collection is enabled.</span></span>  
  
 <span data-ttu-id="4b4d2-132">Tek işlemcili bilgisayarlar için varsayılan iş istasyonu çöp toplama en hızlı seçeneği olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4b4d2-132">For single-processor computers, the default workstation garbage collection should be the fastest option.</span></span> <span data-ttu-id="4b4d2-133">İş istasyonu veya sunucu iki işlemcili bilgisayarlar için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4b4d2-133">Either workstation or server can be used for two-processor computers.</span></span> <span data-ttu-id="4b4d2-134">Sunucu çöp toplama ikiden fazla işlemci için en hızlı seçeneği olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4b4d2-134">Server garbage collection should be the fastest option for more than two processors.</span></span>  
  
 <span data-ttu-id="4b4d2-135">Bu öğe yalnızca uygulama yapılandırma dosyasında kullanılabilir; makine yapılandırma dosyasında ise yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="4b4d2-135">This element can be used only in the application configuration file; it is ignored if it is in the machine configuration file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4b4d2-136">Sunucu çöp toplama etkin değilse .NET Framework 4 ve önceki sürümlerinde eşzamanlı atık toplama kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="4b4d2-136">In the .NET Framework 4 and earlier versions, concurrent garbage collection is not available when server garbage collection is enabled.</span></span> <span data-ttu-id="4b4d2-137">İle başlayarak [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)], sunucu çöp toplama eşzamanlı.</span><span class="sxs-lookup"><span data-stu-id="4b4d2-137">Starting with the [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)], server garbage collection is concurrent.</span></span> <span data-ttu-id="4b4d2-138">Eşzamanlı olmayan sunucu çöp toplama kullanmak üzere ayarlanmış `<gcServer>` öğesine `true` ve [ \<gcConcurrent > öğesi](../../../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) için `false`.</span><span class="sxs-lookup"><span data-stu-id="4b4d2-138">To use non-concurrent server garbage collection, set the `<gcServer>` element to `true` and the [\<gcConcurrent> element](../../../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) to `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4b4d2-139">Örnek</span><span class="sxs-lookup"><span data-stu-id="4b4d2-139">Example</span></span>  
 <span data-ttu-id="4b4d2-140">Aşağıdaki örnekte, sunucu çöp toplama sağlar.</span><span class="sxs-lookup"><span data-stu-id="4b4d2-140">The following example enables server garbage collection.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <gcServer enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4b4d2-141">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4b4d2-141">See Also</span></span>  
 <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="4b4d2-142">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="4b4d2-142">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="4b4d2-143">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="4b4d2-143">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="4b4d2-144">Nasıl yapılır: eş zamanlı çöp toplama devre dışı bırak</span><span class="sxs-lookup"><span data-stu-id="4b4d2-144">How to: Disable Concurrent Garbage Collection</span></span>](http://msdn.microsoft.com/library/ba2c6c67-5778-497c-9fac-5f793b5500c7)
