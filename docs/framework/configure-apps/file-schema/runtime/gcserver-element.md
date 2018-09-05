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
ms.openlocfilehash: 8bfe0db3d6fcbdbbcfb90ff488ab19cdbfaab75e
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43658814"
---
# <a name="ltgcservergt-element"></a><span data-ttu-id="89852-102">&lt;gcServer&gt; öğesi</span><span class="sxs-lookup"><span data-stu-id="89852-102">&lt;gcServer&gt; Element</span></span>
<span data-ttu-id="89852-103">Ortak dil çalışma zamanı sunucu çöp toplama çalışıp çalışmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="89852-103">Specifies whether the common language runtime runs server garbage collection.</span></span>  
  
 <span data-ttu-id="89852-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="89852-104">\<configuration></span></span>  
<span data-ttu-id="89852-105">\<çalışma zamanı ></span><span class="sxs-lookup"><span data-stu-id="89852-105">\<runtime></span></span>  
<span data-ttu-id="89852-106">\<gcServer></span><span class="sxs-lookup"><span data-stu-id="89852-106">\<gcServer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89852-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="89852-107">Syntax</span></span>  
  
```xml  
<gcServer    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="89852-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="89852-108">Attributes and Elements</span></span>  
 <span data-ttu-id="89852-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="89852-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="89852-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="89852-110">Attributes</span></span>  
  
|<span data-ttu-id="89852-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="89852-111">Attribute</span></span>|<span data-ttu-id="89852-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="89852-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="89852-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="89852-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="89852-114">Çalışma zamanı sunucu çöp toplama çalışıp çalışmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="89852-114">Specifies whether the runtime runs server garbage collection.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="89852-115">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="89852-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="89852-116">Değer</span><span class="sxs-lookup"><span data-stu-id="89852-116">Value</span></span>|<span data-ttu-id="89852-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="89852-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="89852-118">Sunucu çöp toplama çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="89852-118">Does not run server garbage collection.</span></span> <span data-ttu-id="89852-119">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="89852-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="89852-120">Sunucu Çöp toplamayı çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="89852-120">Runs server garbage collection.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="89852-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="89852-121">Child Elements</span></span>  
 <span data-ttu-id="89852-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="89852-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="89852-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="89852-123">Parent Elements</span></span>  
  
|<span data-ttu-id="89852-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="89852-124">Element</span></span>|<span data-ttu-id="89852-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="89852-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="89852-126">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="89852-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="89852-127">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="89852-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="89852-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="89852-128">Remarks</span></span>  
 <span data-ttu-id="89852-129">Ortak dil çalışma zamanı (CLR) iki çöp toplama türlerini destekler: tüm sistemlerinde kullanılabilir olan iş istasyonu çöp toplama ve çok işlemcili sistemlerde kullanılabilir sunucu çöp toplama.</span><span class="sxs-lookup"><span data-stu-id="89852-129">The common language runtime (CLR) supports two types of garbage collection: workstation garbage collection, which is available on all systems, and server garbage collection, which is available on multiprocessor systems.</span></span> <span data-ttu-id="89852-130">Kullandığınız `<gcServer>` CLR çöp toplama türünü denetlemek için öğesi gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="89852-130">You use the `<gcServer>` element to control the type of garbage collection the CLR performs.</span></span> <span data-ttu-id="89852-131">Kullanım <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType> sunucu çöp toplama etkin olup olmadığını belirlemek için özellik.</span><span class="sxs-lookup"><span data-stu-id="89852-131">Use the <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType> property to determine if server garbage collection is enabled.</span></span>  
  
 <span data-ttu-id="89852-132">Tek işlemcili bilgisayarlar için varsayılan iş istasyonu çöp toplama en hızlı seçenek olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="89852-132">For single-processor computers, the default workstation garbage collection should be the fastest option.</span></span> <span data-ttu-id="89852-133">İş istasyonu veya sunucu iki işlemcili bilgisayarlar için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="89852-133">Either workstation or server can be used for two-processor computers.</span></span> <span data-ttu-id="89852-134">Sunucu çöp toplama en hızlı seçenek ikiden fazla işlemci olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="89852-134">Server garbage collection should be the fastest option for more than two processors.</span></span>  
  
 <span data-ttu-id="89852-135">Bu öğe yalnızca uygulama yapılandırma dosyasında kullanılabilir; makine yapılandırma dosyasındaki ise göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="89852-135">This element can be used only in the application configuration file; it is ignored if it is in the machine configuration file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="89852-136">Sunucu çöp toplama etkinleştirildiğinde eş zamanlı çöp toplama .NET Framework 4 ve önceki sürümlerle kullanılabilir değil.</span><span class="sxs-lookup"><span data-stu-id="89852-136">In the .NET Framework 4 and earlier versions, concurrent garbage collection is not available when server garbage collection is enabled.</span></span> <span data-ttu-id="89852-137">İle başlayarak [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)], eşzamanlı çöp toplama koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="89852-137">Starting with the [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)], server garbage collection is concurrent.</span></span> <span data-ttu-id="89852-138">Eşzamanlı olmayan çöp toplama koleksiyonu kullanmak için ayarlanmış `<gcServer>` öğesine `true` ve [ \<gcConcurrent > öğesi](../../../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) için `false`.</span><span class="sxs-lookup"><span data-stu-id="89852-138">To use non-concurrent server garbage collection, set the `<gcServer>` element to `true` and the [\<gcConcurrent> element](../../../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) to `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="89852-139">Örnek</span><span class="sxs-lookup"><span data-stu-id="89852-139">Example</span></span>  
 <span data-ttu-id="89852-140">Aşağıdaki örnek, sunucu Çöp toplamayı etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="89852-140">The following example enables server garbage collection.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <gcServer enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="89852-141">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="89852-141">See Also</span></span>  
 <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="89852-142">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="89852-142">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="89852-143">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="89852-143">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="89852-144">Nasıl yapılır: eş zamanlı çöp toplama devre dışı bırak</span><span class="sxs-lookup"><span data-stu-id="89852-144">How to: Disable Concurrent Garbage Collection</span></span>](https://msdn.microsoft.com/library/ba2c6c67-5778-497c-9fac-5f793b5500c7)
