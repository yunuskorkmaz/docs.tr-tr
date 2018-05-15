---
title: '&lt;gcServer&gt; öğesi'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/gcServer
- http://schemas.microsoft.com/.NetConfiguration/v2.0#gcServer
helpviewer_keywords:
- gcServer element
- <gcServer> element
ms.assetid: 8d25b80e-2581-4803-bd87-a59528e3cb03
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 027176bdff644a6ff3314df7484ed88ace93001b
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltgcservergt-element"></a><span data-ttu-id="2afd5-102">&lt;gcServer&gt; öğesi</span><span class="sxs-lookup"><span data-stu-id="2afd5-102">&lt;gcServer&gt; Element</span></span>
<span data-ttu-id="2afd5-103">Ortak dil çalışma zamanı sunucu çöp toplama çalışıp çalışmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="2afd5-103">Specifies whether the common language runtime runs server garbage collection.</span></span>  
  
 <span data-ttu-id="2afd5-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="2afd5-104">\<configuration></span></span>  
<span data-ttu-id="2afd5-105">\<çalışma zamanı ></span><span class="sxs-lookup"><span data-stu-id="2afd5-105">\<runtime></span></span>  
<span data-ttu-id="2afd5-106">\<gcServer></span><span class="sxs-lookup"><span data-stu-id="2afd5-106">\<gcServer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2afd5-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2afd5-107">Syntax</span></span>  
  
```xml  
<gcServer    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2afd5-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="2afd5-108">Attributes and Elements</span></span>  
 <span data-ttu-id="2afd5-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2afd5-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2afd5-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="2afd5-110">Attributes</span></span>  
  
|<span data-ttu-id="2afd5-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="2afd5-111">Attribute</span></span>|<span data-ttu-id="2afd5-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2afd5-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="2afd5-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="2afd5-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="2afd5-114">Çalışma zamanı sunucu çöp toplama çalışıp çalışmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="2afd5-114">Specifies whether the runtime runs server garbage collection.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="2afd5-115">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="2afd5-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="2afd5-116">Değer</span><span class="sxs-lookup"><span data-stu-id="2afd5-116">Value</span></span>|<span data-ttu-id="2afd5-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2afd5-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="2afd5-118">Sunucu çöp toplama çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="2afd5-118">Does not run server garbage collection.</span></span> <span data-ttu-id="2afd5-119">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="2afd5-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="2afd5-120">Sunucu çöp toplama çalışır.</span><span class="sxs-lookup"><span data-stu-id="2afd5-120">Runs server garbage collection.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2afd5-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="2afd5-121">Child Elements</span></span>  
 <span data-ttu-id="2afd5-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="2afd5-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2afd5-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="2afd5-123">Parent Elements</span></span>  
  
|<span data-ttu-id="2afd5-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="2afd5-124">Element</span></span>|<span data-ttu-id="2afd5-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2afd5-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="2afd5-126">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="2afd5-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="2afd5-127">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="2afd5-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2afd5-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2afd5-128">Remarks</span></span>  
 <span data-ttu-id="2afd5-129">Ortak dil çalışma zamanı (CLR) çöp toplama iki türlerini destekler: tüm sistemlerde kullanılabilir iş istasyonu çöp toplama ve çok işlemcili sistemlerde kullanılabilir sunucu çöp toplama.</span><span class="sxs-lookup"><span data-stu-id="2afd5-129">The common language runtime (CLR) supports two types of garbage collection: workstation garbage collection, which is available on all systems, and server garbage collection, which is available on multiprocessor systems.</span></span> <span data-ttu-id="2afd5-130">Kullandığınız `<gcServer>` çöp toplama CLR türünü denetlemek için öğesi gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="2afd5-130">You use the `<gcServer>` element to control the type of garbage collection the CLR performs.</span></span> <span data-ttu-id="2afd5-131">Kullanım <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType> sunucu çöp toplama etkin olup olmadığını belirlemek için özellik.</span><span class="sxs-lookup"><span data-stu-id="2afd5-131">Use the <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType> property to determine if server garbage collection is enabled.</span></span>  
  
 <span data-ttu-id="2afd5-132">Tek işlemcili bilgisayarlar için varsayılan iş istasyonu çöp toplama en hızlı seçeneği olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2afd5-132">For single-processor computers, the default workstation garbage collection should be the fastest option.</span></span> <span data-ttu-id="2afd5-133">İş istasyonu veya sunucu iki işlemcili bilgisayarlar için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2afd5-133">Either workstation or server can be used for two-processor computers.</span></span> <span data-ttu-id="2afd5-134">Sunucu çöp toplama ikiden fazla işlemci için en hızlı seçeneği olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2afd5-134">Server garbage collection should be the fastest option for more than two processors.</span></span>  
  
 <span data-ttu-id="2afd5-135">Bu öğe yalnızca uygulama yapılandırma dosyasında kullanılabilir; makine yapılandırma dosyasında ise yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="2afd5-135">This element can be used only in the application configuration file; it is ignored if it is in the machine configuration file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2afd5-136">Sunucu çöp toplama etkin değilse .NET Framework 4 ve önceki sürümlerinde eşzamanlı atık toplama kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="2afd5-136">In the .NET Framework 4 and earlier versions, concurrent garbage collection is not available when server garbage collection is enabled.</span></span> <span data-ttu-id="2afd5-137">İle başlayarak [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)], sunucu çöp toplama eşzamanlı.</span><span class="sxs-lookup"><span data-stu-id="2afd5-137">Starting with the [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)], server garbage collection is concurrent.</span></span> <span data-ttu-id="2afd5-138">Eşzamanlı olmayan sunucu çöp toplama kullanmak üzere ayarlanmış `<gcServer>` öğesine `true` ve [ \<gcConcurrent > öğesi](../../../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) için `false`.</span><span class="sxs-lookup"><span data-stu-id="2afd5-138">To use non-concurrent server garbage collection, set the `<gcServer>` element to `true` and the [\<gcConcurrent> element](../../../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) to `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2afd5-139">Örnek</span><span class="sxs-lookup"><span data-stu-id="2afd5-139">Example</span></span>  
 <span data-ttu-id="2afd5-140">Aşağıdaki örnekte, sunucu çöp toplama sağlar.</span><span class="sxs-lookup"><span data-stu-id="2afd5-140">The following example enables server garbage collection.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <gcServer enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2afd5-141">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2afd5-141">See Also</span></span>  
 <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="2afd5-142">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="2afd5-142">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="2afd5-143">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="2afd5-143">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="2afd5-144">Nasıl yapılır: eş zamanlı çöp toplama devre dışı bırak</span><span class="sxs-lookup"><span data-stu-id="2afd5-144">How to: Disable Concurrent Garbage Collection</span></span>](http://msdn.microsoft.com/library/ba2c6c67-5778-497c-9fac-5f793b5500c7)
