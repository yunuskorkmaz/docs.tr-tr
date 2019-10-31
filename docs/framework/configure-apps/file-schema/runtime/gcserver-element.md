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
ms.openlocfilehash: 98ecc7069df20a92492e9a6276a0d88331ccc0bb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73116663"
---
# <a name="gcserver-element"></a><span data-ttu-id="41c14-102">\<gcServer > öğesi</span><span class="sxs-lookup"><span data-stu-id="41c14-102">\<gcServer> Element</span></span>
<span data-ttu-id="41c14-103">Ortak dil çalışma zamanının sunucu çöp toplamayı çalıştırmasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="41c14-103">Specifies whether the common language runtime runs server garbage collection.</span></span>  
  
<span data-ttu-id="41c14-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="41c14-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="41c14-105">&nbsp; &nbsp;[ **\<runtime >** ](runtime-element.md) </span><span class="sxs-lookup"><span data-stu-id="41c14-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="41c14-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<gcServer >**</span><span class="sxs-lookup"><span data-stu-id="41c14-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<gcServer>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41c14-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="41c14-107">Syntax</span></span>  
  
```xml  
<gcServer    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="41c14-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="41c14-108">Attributes and Elements</span></span>  
 <span data-ttu-id="41c14-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="41c14-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="41c14-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="41c14-110">Attributes</span></span>  
  
|<span data-ttu-id="41c14-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="41c14-111">Attribute</span></span>|<span data-ttu-id="41c14-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="41c14-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="41c14-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="41c14-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="41c14-114">Çalışma zamanının sunucu çöp toplamayı çalıştırmasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="41c14-114">Specifies whether the runtime runs server garbage collection.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="41c14-115">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="41c14-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="41c14-116">Değer</span><span class="sxs-lookup"><span data-stu-id="41c14-116">Value</span></span>|<span data-ttu-id="41c14-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="41c14-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="41c14-118">Sunucu çöp toplamayı çalıştırmaz.</span><span class="sxs-lookup"><span data-stu-id="41c14-118">Does not run server garbage collection.</span></span> <span data-ttu-id="41c14-119">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="41c14-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="41c14-120">Sunucu çöp toplamayı çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="41c14-120">Runs server garbage collection.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="41c14-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="41c14-121">Child Elements</span></span>  
 <span data-ttu-id="41c14-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="41c14-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="41c14-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="41c14-123">Parent Elements</span></span>  
  
|<span data-ttu-id="41c14-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="41c14-124">Element</span></span>|<span data-ttu-id="41c14-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="41c14-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="41c14-126">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="41c14-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="41c14-127">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="41c14-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="41c14-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="41c14-128">Remarks</span></span>  
 <span data-ttu-id="41c14-129">Ortak dil çalışma zamanı (CLR) iki tür çöp toplamayı destekler: tüm sistemlerde kullanılabilen iş istasyonu çöp toplama ve çok işlemcili sistemlerde bulunan sunucu çöp toplama.</span><span class="sxs-lookup"><span data-stu-id="41c14-129">The common language runtime (CLR) supports two types of garbage collection: workstation garbage collection, which is available on all systems, and server garbage collection, which is available on multiprocessor systems.</span></span> <span data-ttu-id="41c14-130">CLR 'nin gerçekleştirdiği çöp toplamanın türünü denetlemek için `<gcServer>` öğesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="41c14-130">You use the `<gcServer>` element to control the type of garbage collection the CLR performs.</span></span> <span data-ttu-id="41c14-131">Sunucu çöp toplamanın etkinleştirilip etkinleştirilmediğini anlamak için <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType> özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="41c14-131">Use the <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType> property to determine if server garbage collection is enabled.</span></span>  
  
 <span data-ttu-id="41c14-132">Tek işlemcili bilgisayarlar için varsayılan iş istasyonu atık toplama en hızlı seçenek olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="41c14-132">For single-processor computers, the default workstation garbage collection should be the fastest option.</span></span> <span data-ttu-id="41c14-133">İki işlemcili bilgisayarlar için iş istasyonu veya sunucu kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="41c14-133">Either workstation or server can be used for two-processor computers.</span></span> <span data-ttu-id="41c14-134">Sunucu çöp toplama, ikiden fazla işlemci için en hızlı seçenek olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="41c14-134">Server garbage collection should be the fastest option for more than two processors.</span></span>  
  
 <span data-ttu-id="41c14-135">Bu öğe yalnızca uygulama yapılandırma dosyasında kullanılabilir; makine yapılandırma dosyasında ise yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="41c14-135">This element can be used only in the application configuration file; it is ignored if it is in the machine configuration file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="41c14-136">.NET Framework 4 ve önceki sürümlerde, sunucu çöp toplama etkinleştirildiğinde eşzamanlı çöp toplama kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="41c14-136">In the .NET Framework 4 and earlier versions, concurrent garbage collection is not available when server garbage collection is enabled.</span></span> <span data-ttu-id="41c14-137">4,5 .NET Framework başlayarak, sunucu çöp toplama işlemi eşzamanlı olur.</span><span class="sxs-lookup"><span data-stu-id="41c14-137">Starting with the .NET Framework 4.5, server garbage collection is concurrent.</span></span> <span data-ttu-id="41c14-138">Eş zamanlı olmayan sunucu çöp toplamayı kullanmak için `<gcServer>` öğesini `true` ve [\<gcConcurrent > öğesi](gcconcurrent-element.md) `false`olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="41c14-138">To use non-concurrent server garbage collection, set the `<gcServer>` element to `true` and the [\<gcConcurrent> element](gcconcurrent-element.md) to `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="41c14-139">Örnek</span><span class="sxs-lookup"><span data-stu-id="41c14-139">Example</span></span>  
 <span data-ttu-id="41c14-140">Aşağıdaki örnek, sunucu çöp toplamayı mümkün bir şekilde sunar.</span><span class="sxs-lookup"><span data-stu-id="41c14-140">The following example enables server garbage collection.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <gcServer enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="41c14-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="41c14-141">See also</span></span>

- <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>
- [<span data-ttu-id="41c14-142">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="41c14-142">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="41c14-143">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="41c14-143">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="41c14-144">Eşzamanlı atık toplamayı devre dışı bırakmak için</span><span class="sxs-lookup"><span data-stu-id="41c14-144">To disable concurrent garbage collection</span></span>](gcconcurrent-element.md#to-disable-background-garbage-collection)
