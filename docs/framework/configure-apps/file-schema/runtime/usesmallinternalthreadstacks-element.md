---
title: "&lt;Usesmallınternalthreadstacks&gt; öğesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UseSmallInternalThreadStacks element
- <UseSmallInternalThreadStacks> element
ms.assetid: 1e3f6ec0-1cac-4e1c-9c81-17d948ae5874
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c96537cad59034578d1284f7dc432e5775f3730b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltusesmallinternalthreadstacksgt-element"></a><span data-ttu-id="22a04-102">&lt;Usesmallınternalthreadstacks&gt; öğesi</span><span class="sxs-lookup"><span data-stu-id="22a04-102">&lt;UseSmallInternalThreadStacks&gt; Element</span></span>
<span data-ttu-id="22a04-103">Ortak dil çalışma zamanı (CLR) bellek miktarını azaltmak istekleri dahili olarak, bu iş parçacığı için varsayılan yığın boyutunu kullanmak yerine kullanır belirli iş parçacıklarını oluşturduğunda açık yığın boyutları belirterek kullanır.</span><span class="sxs-lookup"><span data-stu-id="22a04-103">Requests that the common language runtime (CLR) reduce memory use by specifying explicit stack sizes when it creates certain threads that it uses internally, instead of using the default stack size for those threads.</span></span>  
  
 <span data-ttu-id="22a04-104">\<Yapılandırma > öğesi</span><span class="sxs-lookup"><span data-stu-id="22a04-104">\<configuration> Element</span></span>  
<span data-ttu-id="22a04-105">\<çalışma zamanı > öğesi</span><span class="sxs-lookup"><span data-stu-id="22a04-105">\<runtime> Element</span></span>  
<span data-ttu-id="22a04-106">\<Usesmallınternalthreadstacks > öğesi</span><span class="sxs-lookup"><span data-stu-id="22a04-106">\<UseSmallInternalThreadStacks> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22a04-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="22a04-107">Syntax</span></span>  
  
```xml  
<UseSmallInternalThreadStacks enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="22a04-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="22a04-108">Attributes and Elements</span></span>  
 <span data-ttu-id="22a04-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="22a04-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="22a04-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="22a04-110">Attributes</span></span>  
  
|<span data-ttu-id="22a04-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="22a04-111">Attribute</span></span>|<span data-ttu-id="22a04-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="22a04-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="22a04-113">Etkin</span><span class="sxs-lookup"><span data-stu-id="22a04-113">enabled</span></span>|<span data-ttu-id="22a04-114">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="22a04-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="22a04-115">Dahili olarak kullanan belirli iş parçacıklarını oluşturduğunda, istenip istenmeyeceğini CLR kullanım açık yığın boyutları yerine varsayılan yığın boyutunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="22a04-115">Specifies whether to request that the CLR use explicit stack sizes instead of the default stack size when it creates certain threads that it uses internally.</span></span> <span data-ttu-id="22a04-116">Açık yığın boyutu 1 MB varsayılan yığın boyutundan daha küçük.</span><span class="sxs-lookup"><span data-stu-id="22a04-116">The explicit stack sizes are smaller than the default stack size of 1 MB.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="22a04-117">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="22a04-117">enabled Attribute</span></span>  
  
|<span data-ttu-id="22a04-118">Değer</span><span class="sxs-lookup"><span data-stu-id="22a04-118">Value</span></span>|<span data-ttu-id="22a04-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="22a04-119">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="22a04-120">true</span><span class="sxs-lookup"><span data-stu-id="22a04-120">true</span></span>|<span data-ttu-id="22a04-121">Açık yığın boyutları isteyin.</span><span class="sxs-lookup"><span data-stu-id="22a04-121">Request explicit stack sizes.</span></span>|  
|<span data-ttu-id="22a04-122">false</span><span class="sxs-lookup"><span data-stu-id="22a04-122">false</span></span>|<span data-ttu-id="22a04-123">Varsayılan yığın boyutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="22a04-123">Use the default stack size.</span></span> <span data-ttu-id="22a04-124">Bunun için varsayılan değer [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="22a04-124">This is the default for the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)].</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="22a04-125">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="22a04-125">Child Elements</span></span>  
 <span data-ttu-id="22a04-126">Yok.</span><span class="sxs-lookup"><span data-stu-id="22a04-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="22a04-127">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="22a04-127">Parent Elements</span></span>  
  
|<span data-ttu-id="22a04-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="22a04-128">Element</span></span>|<span data-ttu-id="22a04-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="22a04-129">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="22a04-130">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="22a04-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="22a04-131">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="22a04-131">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="22a04-132">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="22a04-132">Remarks</span></span>  
 <span data-ttu-id="22a04-133">İstek dikkate alınır, iç iş parçacığı için CLR kullanan açık iş parçacığı boyutları varsayılan boyuttan daha küçük olduğu için bu yapılandırma öğesi bir işlemde daha az sanal bellek kullanımını istemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="22a04-133">This configuration element is used to request reduced virtual memory use in a process, because the explicit thread sizes that the CLR uses for its internal threads, if the request is honored, are smaller than the default size.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="22a04-134">Bu yapılandırma öğesi mutlak bir gereksinim yerine CLR isteğidir.</span><span class="sxs-lookup"><span data-stu-id="22a04-134">This configuration element is a request to the CLR rather than an absolute requirement.</span></span> <span data-ttu-id="22a04-135">İçinde [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], istek yalnızca x86 için dikkate alınır mimarisi.</span><span class="sxs-lookup"><span data-stu-id="22a04-135">In the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], the request is honored only for the x86 architecture.</span></span> <span data-ttu-id="22a04-136">Bu öğe CLR gelecek sürümlerinde tamamen göz ardı veya seçili iç iş parçacıkları için kullanılan her zaman açık yığın boyutları olarak değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="22a04-136">This element might be ignored completely in future versions of the CLR, or replaced by explicit stack sizes that are always used for selected internal threads.</span></span>  
  
 <span data-ttu-id="22a04-137">CLR isteği geliştirir, daha küçük yığın boyutları olası yığın olun çünkü bu yapılandırma öğesi daha küçük sanal bellek kullanımı için güvenilirlik trades belirterek daha büyük bir olasılıkla taşar.</span><span class="sxs-lookup"><span data-stu-id="22a04-137">Specifying this configuration element trades reliability for smaller virtual memory use if the CLR honors the request, because smaller stack sizes could potentially make stack overflows more likely.</span></span>  
  
## <a name="example"></a><span data-ttu-id="22a04-138">Örnek</span><span class="sxs-lookup"><span data-stu-id="22a04-138">Example</span></span>  
 <span data-ttu-id="22a04-139">Aşağıdaki örnek, CLR kullanım açık yığın belirli dahili olarak kullandığı iş parçacıklarının boyutları isteği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="22a04-139">The following example shows how to request that the CLR use explicit stack sizes for certain threads that it uses internally.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <UseSmallInternalThreadStacks enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="22a04-140">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="22a04-140">See Also</span></span>  
 [<span data-ttu-id="22a04-141">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="22a04-141">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="22a04-142">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="22a04-142">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
