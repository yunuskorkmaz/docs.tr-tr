---
title: '&lt;Usesmallınternalthreadstacks&gt; öğesi'
ms.date: 03/30/2017
helpviewer_keywords:
- UseSmallInternalThreadStacks element
- <UseSmallInternalThreadStacks> element
ms.assetid: 1e3f6ec0-1cac-4e1c-9c81-17d948ae5874
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a11b9a008878e716e9b3d8cd54abe5eb4169672a
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltusesmallinternalthreadstacksgt-element"></a><span data-ttu-id="59429-102">&lt;Usesmallınternalthreadstacks&gt; öğesi</span><span class="sxs-lookup"><span data-stu-id="59429-102">&lt;UseSmallInternalThreadStacks&gt; Element</span></span>
<span data-ttu-id="59429-103">Ortak dil çalışma zamanı (CLR) bellek miktarını azaltmak istekleri dahili olarak, bu iş parçacığı için varsayılan yığın boyutunu kullanmak yerine kullanır belirli iş parçacıklarını oluşturduğunda açık yığın boyutları belirterek kullanır.</span><span class="sxs-lookup"><span data-stu-id="59429-103">Requests that the common language runtime (CLR) reduce memory use by specifying explicit stack sizes when it creates certain threads that it uses internally, instead of using the default stack size for those threads.</span></span>  
  
 <span data-ttu-id="59429-104">\<Yapılandırma > öğesi</span><span class="sxs-lookup"><span data-stu-id="59429-104">\<configuration> Element</span></span>  
<span data-ttu-id="59429-105">\<çalışma zamanı > öğesi</span><span class="sxs-lookup"><span data-stu-id="59429-105">\<runtime> Element</span></span>  
<span data-ttu-id="59429-106">\<Usesmallınternalthreadstacks > öğesi</span><span class="sxs-lookup"><span data-stu-id="59429-106">\<UseSmallInternalThreadStacks> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59429-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="59429-107">Syntax</span></span>  
  
```xml  
<UseSmallInternalThreadStacks enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="59429-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="59429-108">Attributes and Elements</span></span>  
 <span data-ttu-id="59429-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="59429-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="59429-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="59429-110">Attributes</span></span>  
  
|<span data-ttu-id="59429-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="59429-111">Attribute</span></span>|<span data-ttu-id="59429-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="59429-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="59429-113">Etkin</span><span class="sxs-lookup"><span data-stu-id="59429-113">enabled</span></span>|<span data-ttu-id="59429-114">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="59429-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="59429-115">Dahili olarak kullanan belirli iş parçacıklarını oluşturduğunda, istenip istenmeyeceğini CLR kullanım açık yığın boyutları yerine varsayılan yığın boyutunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="59429-115">Specifies whether to request that the CLR use explicit stack sizes instead of the default stack size when it creates certain threads that it uses internally.</span></span> <span data-ttu-id="59429-116">Açık yığın boyutu 1 MB varsayılan yığın boyutundan daha küçük.</span><span class="sxs-lookup"><span data-stu-id="59429-116">The explicit stack sizes are smaller than the default stack size of 1 MB.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="59429-117">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="59429-117">enabled Attribute</span></span>  
  
|<span data-ttu-id="59429-118">Değer</span><span class="sxs-lookup"><span data-stu-id="59429-118">Value</span></span>|<span data-ttu-id="59429-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="59429-119">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="59429-120">true</span><span class="sxs-lookup"><span data-stu-id="59429-120">true</span></span>|<span data-ttu-id="59429-121">Açık yığın boyutları isteyin.</span><span class="sxs-lookup"><span data-stu-id="59429-121">Request explicit stack sizes.</span></span>|  
|<span data-ttu-id="59429-122">false</span><span class="sxs-lookup"><span data-stu-id="59429-122">false</span></span>|<span data-ttu-id="59429-123">Varsayılan yığın boyutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="59429-123">Use the default stack size.</span></span> <span data-ttu-id="59429-124">Bunun için varsayılan değer [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="59429-124">This is the default for the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)].</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="59429-125">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="59429-125">Child Elements</span></span>  
 <span data-ttu-id="59429-126">Yok.</span><span class="sxs-lookup"><span data-stu-id="59429-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="59429-127">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="59429-127">Parent Elements</span></span>  
  
|<span data-ttu-id="59429-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="59429-128">Element</span></span>|<span data-ttu-id="59429-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="59429-129">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="59429-130">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="59429-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="59429-131">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="59429-131">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="59429-132">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="59429-132">Remarks</span></span>  
 <span data-ttu-id="59429-133">İstek dikkate alınır, iç iş parçacığı için CLR kullanan açık iş parçacığı boyutları varsayılan boyuttan daha küçük olduğu için bu yapılandırma öğesi bir işlemde daha az sanal bellek kullanımını istemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="59429-133">This configuration element is used to request reduced virtual memory use in a process, because the explicit thread sizes that the CLR uses for its internal threads, if the request is honored, are smaller than the default size.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="59429-134">Bu yapılandırma öğesi mutlak bir gereksinim yerine CLR isteğidir.</span><span class="sxs-lookup"><span data-stu-id="59429-134">This configuration element is a request to the CLR rather than an absolute requirement.</span></span> <span data-ttu-id="59429-135">İçinde [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], istek yalnızca x86 için dikkate alınır mimarisi.</span><span class="sxs-lookup"><span data-stu-id="59429-135">In the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], the request is honored only for the x86 architecture.</span></span> <span data-ttu-id="59429-136">Bu öğe CLR gelecek sürümlerinde tamamen göz ardı veya seçili iç iş parçacıkları için kullanılan her zaman açık yığın boyutları olarak değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="59429-136">This element might be ignored completely in future versions of the CLR, or replaced by explicit stack sizes that are always used for selected internal threads.</span></span>  
  
 <span data-ttu-id="59429-137">CLR isteği geliştirir, daha küçük yığın boyutları olası yığın olun çünkü bu yapılandırma öğesi daha küçük sanal bellek kullanımı için güvenilirlik trades belirterek daha büyük bir olasılıkla taşar.</span><span class="sxs-lookup"><span data-stu-id="59429-137">Specifying this configuration element trades reliability for smaller virtual memory use if the CLR honors the request, because smaller stack sizes could potentially make stack overflows more likely.</span></span>  
  
## <a name="example"></a><span data-ttu-id="59429-138">Örnek</span><span class="sxs-lookup"><span data-stu-id="59429-138">Example</span></span>  
 <span data-ttu-id="59429-139">Aşağıdaki örnek, CLR kullanım açık yığın belirli dahili olarak kullandığı iş parçacıklarının boyutları isteği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="59429-139">The following example shows how to request that the CLR use explicit stack sizes for certain threads that it uses internally.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <UseSmallInternalThreadStacks enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="59429-140">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="59429-140">See Also</span></span>  
 [<span data-ttu-id="59429-141">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="59429-141">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="59429-142">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="59429-142">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
