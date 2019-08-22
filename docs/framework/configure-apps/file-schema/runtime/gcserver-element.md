---
title: <gcServer> Öğesi
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
ms.openlocfilehash: 61b4076a72dbc17ffc800a1a8d37a22d1435e02b
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663676"
---
# <a name="gcserver-element"></a><span data-ttu-id="9d397-102">\<gcServer > öğesi</span><span class="sxs-lookup"><span data-stu-id="9d397-102">\<gcServer> Element</span></span>
<span data-ttu-id="9d397-103">Ortak dil çalışma zamanının sunucu çöp toplamayı çalıştırmasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="9d397-103">Specifies whether the common language runtime runs server garbage collection.</span></span>  
  
 <span data-ttu-id="9d397-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="9d397-104">\<configuration></span></span>  
<span data-ttu-id="9d397-105">\<çalışma zamanı ></span><span class="sxs-lookup"><span data-stu-id="9d397-105">\<runtime></span></span>  
<span data-ttu-id="9d397-106">\<gcServer></span><span class="sxs-lookup"><span data-stu-id="9d397-106">\<gcServer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d397-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9d397-107">Syntax</span></span>  
  
```xml  
<gcServer    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9d397-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="9d397-108">Attributes and Elements</span></span>  
 <span data-ttu-id="9d397-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9d397-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9d397-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="9d397-110">Attributes</span></span>  
  
|<span data-ttu-id="9d397-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="9d397-111">Attribute</span></span>|<span data-ttu-id="9d397-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9d397-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="9d397-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="9d397-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="9d397-114">Çalışma zamanının sunucu çöp toplamayı çalıştırmasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="9d397-114">Specifies whether the runtime runs server garbage collection.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="9d397-115">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="9d397-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="9d397-116">Değer</span><span class="sxs-lookup"><span data-stu-id="9d397-116">Value</span></span>|<span data-ttu-id="9d397-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9d397-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="9d397-118">Sunucu çöp toplamayı çalıştırmaz.</span><span class="sxs-lookup"><span data-stu-id="9d397-118">Does not run server garbage collection.</span></span> <span data-ttu-id="9d397-119">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="9d397-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="9d397-120">Sunucu çöp toplamayı çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="9d397-120">Runs server garbage collection.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9d397-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="9d397-121">Child Elements</span></span>  
 <span data-ttu-id="9d397-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="9d397-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9d397-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="9d397-123">Parent Elements</span></span>  
  
|<span data-ttu-id="9d397-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="9d397-124">Element</span></span>|<span data-ttu-id="9d397-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9d397-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="9d397-126">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="9d397-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="9d397-127">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="9d397-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9d397-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9d397-128">Remarks</span></span>  
 <span data-ttu-id="9d397-129">Ortak dil çalışma zamanı (CLR) iki tür çöp toplamayı destekler: tüm sistemlerde kullanılabilen iş istasyonu çöp toplama ve çok işlemcili sistemlerde bulunan sunucu çöp toplama.</span><span class="sxs-lookup"><span data-stu-id="9d397-129">The common language runtime (CLR) supports two types of garbage collection: workstation garbage collection, which is available on all systems, and server garbage collection, which is available on multiprocessor systems.</span></span> <span data-ttu-id="9d397-130">CLR 'nin gerçekleştirdiği `<gcServer>` çöp toplamanın türünü denetlemek için öğesini kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="9d397-130">You use the `<gcServer>` element to control the type of garbage collection the CLR performs.</span></span> <span data-ttu-id="9d397-131">Sunucu çöp toplamanın etkinleştirilip etkinleştirilmediğini anlamak için özelliğinikullanın.<xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="9d397-131">Use the <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType> property to determine if server garbage collection is enabled.</span></span>  
  
 <span data-ttu-id="9d397-132">Tek işlemcili bilgisayarlar için varsayılan iş istasyonu atık toplama en hızlı seçenek olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9d397-132">For single-processor computers, the default workstation garbage collection should be the fastest option.</span></span> <span data-ttu-id="9d397-133">İki işlemcili bilgisayarlar için iş istasyonu veya sunucu kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9d397-133">Either workstation or server can be used for two-processor computers.</span></span> <span data-ttu-id="9d397-134">Sunucu çöp toplama, ikiden fazla işlemci için en hızlı seçenek olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9d397-134">Server garbage collection should be the fastest option for more than two processors.</span></span>  
  
 <span data-ttu-id="9d397-135">Bu öğe yalnızca uygulama yapılandırma dosyasında kullanılabilir; makine yapılandırma dosyasında ise yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="9d397-135">This element can be used only in the application configuration file; it is ignored if it is in the machine configuration file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9d397-136">.NET Framework 4 ve önceki sürümlerde, sunucu çöp toplama etkinleştirildiğinde eşzamanlı çöp toplama kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="9d397-136">In the .NET Framework 4 and earlier versions, concurrent garbage collection is not available when server garbage collection is enabled.</span></span> <span data-ttu-id="9d397-137">4,5 .NET Framework başlayarak, sunucu çöp toplama işlemi eşzamanlı olur.</span><span class="sxs-lookup"><span data-stu-id="9d397-137">Starting with the .NET Framework 4.5, server garbage collection is concurrent.</span></span> <span data-ttu-id="9d397-138">Eş zamanlı olmayan sunucu çöp toplamayı kullanmak `<gcServer>` için, `true` öğesini ve [ \<gcConcurrent > öğesi](gcconcurrent-element.md) olarak `false`ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="9d397-138">To use non-concurrent server garbage collection, set the `<gcServer>` element to `true` and the [\<gcConcurrent> element](gcconcurrent-element.md) to `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9d397-139">Örnek</span><span class="sxs-lookup"><span data-stu-id="9d397-139">Example</span></span>  
 <span data-ttu-id="9d397-140">Aşağıdaki örnek, sunucu çöp toplamayı mümkün bir şekilde sunar.</span><span class="sxs-lookup"><span data-stu-id="9d397-140">The following example enables server garbage collection.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <gcServer enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9d397-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9d397-141">See also</span></span>

- <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>
- [<span data-ttu-id="9d397-142">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="9d397-142">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="9d397-143">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="9d397-143">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="9d397-144">Eşzamanlı atık toplamayı devre dışı bırakmak için</span><span class="sxs-lookup"><span data-stu-id="9d397-144">To disable concurrent garbage collection</span></span>](gcconcurrent-element.md#to-disable-background-garbage-collection)
